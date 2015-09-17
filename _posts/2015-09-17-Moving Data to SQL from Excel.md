---
layout: post
title: Moving Data from Excel to SQL
---

Often times I felt a need for easier way to transfer data from excel to SQL Server Quickly for analysis
etc. Sometimes, I also need to join tables and query result from one server to another server, here
linked servers seems to be more promising solution but it requires certain amount of administrative
task and security consideration and I felt it is not quick. To help me in this I have wrote two
powershell functions below.  


### Convert the copied data to powershell object

The first step is to get the excel spreadsheet to a powershell object. We need to copy the data to
clipboard and this function will process the data from clipboard. 

{% highlight powershell %}
function Get-SHExcelClip
{
<#

.EXAMPLE
Copy a table from excel with header and run below command
Get-SHExcelClip

 #>
    ConvertFrom-Csv (Get-Clipboard | ? {$_.trim() -ne ''} |  % {'"'+($_ -replace "`t", '","') +'"'})
 }
{% endhighlight %}


### Pipe the powershell object to generate SQL

Later, the output can be piped to get a [select] query generated with [union all] between every
select. The select is copied back to clipboard for convinence.


{% highlight powershell %}
function Get-SHSQLSelect
{
<#

.EXAMPLE
 Import-AllSHModules
 Get-SHExcelClip | Get-SHSQLSelect

 #>
   [CmdletBinding()] param(
        [Parameter(ValueFromPipeline=$true)][PSObject]$InputObject
    )
    begin {
        $query = ''
    }
    process {
        $temp = "select `r`n"
           foreach($prop in $InputObject.psobject.properties){
                $temp = $temp + "`t`t`t'" + $prop.value + "'`t as [" + $prop.Name + "],`r`n" 
           }
           #Remove the last comma
           $temp =  $temp.Substring(0,$temp.Length - 3)

           #Add a union all
           $temp = $temp+ "`r`nunion all"

           #Add newline
           $query = $query + $temp + "`r`n"
    }
    end {
            #remove the last union all
           $query =  $query.Substring(0,$query.Length - 12)
           $query | Set-Clipboard
    }
 }
{% endhighlight %}

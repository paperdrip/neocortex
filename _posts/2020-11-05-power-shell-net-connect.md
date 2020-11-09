---
layout: post
title: Checking site accessibility using Powershell
date: 2020-11-05 10:50
tags: ["powershell", "network"]
summary:
---

There's a need to determine certain web site accessibility from a Windows desktop sitting behind a firewall. "Telnet" is the first tool to consider but we want to automate the process as the test would be conducted across a number of PC but scripting around the Telnet command is not pleasant to say the least.

Also, we don't want to use tools that need installation. Thus, I am figuring what's available built-in.

Turns out there's a Powershell command called `test-netconnection` that I could leverage. Below are how I resolve particular requirement with this command.

### Surpress warning message
The switch "Quiet" limits the output to only "true" or "false" but to surpress the warning during execution, `-WarningAction SilentlyContinue` comes to the rescue.

### Connection time out
Easy, there's no control on time out setting. So wait for 10 seconds.

### Getting the size of array within scripting
Additional $ sign is needed to extract the value and print it out in the console.

`Write-Host "Testing $counter out of $($array.Count)"`

### Bypass priviledge restriction
When my script is copied to another machine, when it runs, a SecurityError exception is thrown.

So instead of just running the script, additional argument is needed.

`PowerShell.exe -ExecutionPolicy Bypass -File domain-check.ps1`

### Looping through an array and test the connectivity
Below are how I did to loop through the array and conduct test. One thing to note, 443 is not available as "CommonPort" and thus I have to specifiy it in numbers.

`
foreach ($element in $array){
    Write-Host "Testing $counter out of $($array.Count)"
    $result = test-netconnection -ComputerName $element -Port 443 -InformationLevel Quiet -WarningAction SilentlyContinue
    if(!$result) {
        $err_array+=$element
    }
    $counter++
}
`
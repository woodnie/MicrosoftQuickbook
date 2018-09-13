### Boot time {#boot-time}

Get-EventLog -LogName System | where { ($_.InstanceId -bAnd 0xFFFF) -eq 6006 }

Get-WmiObject -class Win32_OperatingSystem | Select-Object  __SERVER,@{label=&amp;apos;LastBootUpTime&amp;apos;;expression={$_.ConvertToDateTime($_.LastBootUpTime)}}

Get-CimInstance -Class Win32_OperatingSystem | Select-Object LastBootUpTime

net statistics workstation

wmic os get lastbootuptime

systeminfo | find /i &quot;Boot Time&quot;
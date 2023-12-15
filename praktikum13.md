# Praktikum 13 aruanne
Kolmeteistkümnendas praksis tegelesime skriptimisega Windowsi Powershell ISE-s.

[tulemus.txt](https://github.com/armeig/opsys_praktikumid_armei_grete/files/13686918/tulemus.txt)

skript:
```

function valjasta{
	param ($nr, $param, $sisu)
	$fail = ".\tulemus.txt"
	if($sisu -eq $null){
		$rida = "$nr.	${param}"
		Write-Output $rida
		$rida | Out-File -FilePath $fail -Append
	}elseif($sisu.GetType().Name -eq "Object[]"){
		$rida = "$nr.	${param}:"
		Write-Output $rida $sisu
		$rida | Out-File -FilePath $fail -Append
		$sisu | Out-File -FilePath $fail -Append
	}else{
		$rida = "$nr.	${param}:	$sisu"
		Write-Output $rida
		$rida | Out-File -FilePath $fail -Append
	}
}


Valjasta 1 "host" (hostname)


$PS = $PSVersionTable.PSVersion 
Valjasta 2 "Powershelli versioon" $PS

$WV = [System.Environment]::OSVersion.Version 
Valjasta 3 "Windowsi versioon" $WV

$VK = Get-WmiObject Win32_NetworkAdapterConfiguration -Filter "IPEnabled='True'" | select * | Select-Object IPAddress, IPSubnet, DefaultIPGateway, DHCPEnabled, MACAddress | Sort-Object DHCPEnabled | Format-List
Valjasta 4 "Võrgukonfiguratsioon" $VK

$protsessor = Get-WmiObject -Class Win32_Processor | Format-list
Valjasta 5 "Protsessori kirjaldus" $protsessor

$RAM = Get-WmiObject Win32_ComputerSystem | Select-Object TotalPhysicalMemory | Format-List
Valjasta 6 "RAM" $RAM

$VC = Get-WmiObject Win32_VideoController | Select-Object Name, DriverVersion, DriverDate, CurrentVerticalResolution, CurrentHorizontalResolution | Format-List 
Valjasta 7 "Graafikakaardi nimi, draiveri versioon, kuupäev ja ekraani lahutus" $VC

$partitsioonitabel = Get-Disk | Get-Partition
Valjasta 8 "Partitsioonitabel" $partitsioonitabel

$Cketas = Get-WmiObject -Class Win32_LogicalDisk | Where-Object {$_.DeviceID -eq 'C:'} | Select-Object FreeSpace
$vabaruum = [math]::Round($Cketas.FreeSpace/1GB, 2)
Valjasta 9 "C-kettal on vaba ruumi" $vabaruum
 
$draiverid = Get-WmiObject -Class Win32_PnpSignedDriver | Where-Object {$_.DeviceID -like "PCI*"} | Select-Object Description, Manufacturer, DriverVersion | Format-Table -AutoSize
Valjasta 10 "PCI-siinil olevate seademete draiverite info" $draiverid

$kasutajad = Get-WmiObject Win32_UserAccount | select * | Select-Object Name, Description, LocalAccount, Disabled | Format-Table -AutoSize
Valjasta 11 "Kasutajad" $kasutajad

$protsessid = (Get-Process).count
Valjasta 12 "Käimasolevate protsesside arv" $protsessid

$käivitatud = Get-Process | Select-Object Name, PID, StartTime | Sort-Object StartTime | Select-Object -Last 10
Valjasta 13 "10 viimasena käivitatud protsessi" $käivitatud

$kuupäevjakellaaeg = Get-Date -Format "dd/MM/yyyy HH:mm"
Valjasta 14 $kuupäevjakellaaeg
```


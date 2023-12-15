# Praktikum 13 aruanne
Kolmeteistkümnendas praksis tegelesime skriptimisega Windowsi Powershell ISE-s.

[tulemus.txt](https://github.com/armeig/opsys_praktikumid_armei_grete/files/13686918/tulemus.txt)

faili tulemus.txt sisu:
```
1.	host:	ARMEI-W11
2.	Powershelli versioon:	5.1.22621.2506
3.	Windowsi versioon:	10.0.22631.0
4.	Võrgukonfiguratsioon:


IPAddress        : {10.0.2.15, fe80::2d6a:a237:f579:8fbb}
IPSubnet         : {255.255.255.0, 64}
DefaultIPGateway : {10.0.2.2}
DHCPEnabled      : True
MACAddress       : 08:00:27:91:87:18



5.	Protsessori kirjaldus:


Caption           : Intel64 Family 6 Model 186 Stepping 3
DeviceID          : CPU0
Manufacturer      : GenuineIntel
MaxClockSpeed     : 2496
Name              : 13th Gen Intel(R) Core(TM) i5-1335U
SocketDesignation : 



6.	RAM:


TotalPhysicalMemory : 4277866496



7.	Graafikakaardi nimi, draiveri versioon, kuupäev ja ekraani lahutus:


Name                        : VirtualBox Graphics Adapter (WDDM)
DriverVersion               : 7.0.10.8379
DriverDate                  : 20230712000000.000000-000
CurrentVerticalResolution   : 1080
CurrentHorizontalResolution : 1920



8.	Partitsioonitabel:


   DiskPath: \\?\scsi#disk&ven_vbox&prod_harddisk#4&2617aeae&0&000000#{53f56307-b6bf-11d0-94f2-00a0c91efb8b}

PartitionNumber  DriveLetter Offset                                                                                                Size Type                                                                                           
---------------  ----------- ------                                                                                                ---- ----                                                                                           
1                            1048576                                                                                             100 MB System                                                                                         
2                            105906176                                                                                            16 MB Reserved                                                                                       
3                C           122683392                                                                                         63.22 GB Basic                                                                                          
4                            68009590784                                                                                         675 MB Recovery                                                                                       


9.	C-kettal on vaba ruumi:	32.54
10.	PCI-siinil olevate seademete draiverite info:

Description                          Manufacturer                     DriverVersion  
-----------                          ------------                     -------------  
Standard SATA AHCI Controller        Standard SATA AHCI Controller    10.0.22621.2506
USB xHCI Compliant Host Controller   Generic USB xHCI Host Controller 10.0.22621.2506
High Definition Audio Controller     Microsoft                        10.0.22621.2792
VirtualBox Guest Device              Oracle Corporation               7.0.10.8379    
Intel(R) PRO/1000 MT Desktop Adapter Intel                            8.4.13.0       
VirtualBox Graphics Adapter (WDDM)   Oracle Corporation               7.0.10.8379    
PCI to ISA Bridge                    Intel                            10.0.22621.1   
CPU to PCI Bridge                    Intel                            10.0.22621.1   


11.	Kasutajad:

Name               Description                                                                                     LocalAccount Disabled
----               -----------                                                                                     ------------ --------
Administrator      Built-in account for administering the computer/domain                                                  True     True
DefaultAccount     A user account managed by the system.                                                                   True     True
Grete                                                                                                                      True    False
Grete-tava                                                                                                                 True    False
Guest              Built-in account for guest access to the computer/domain                                                True     True
tootaja1                                                                                                                   True    False
tootaja2                                                                                                                   True    False
WDAGUtilityAccount A user account managed and used by the system for Windows Defender Application Guard scenarios.         True     True
ylemus                                                                                                                     True    False


12.	Käimasolevate protsesside arv:	157
13.	10 viimasena käivitatud protsessi:

Name               PID StartTime            
----               --- ---------            
msedge                 12/15/2023 2:51:44 PM
dllhost                12/15/2023 4:00:34 PM
audiodg                12/15/2023 4:22:30 PM
taskhostw              12/15/2023 4:40:32 PM
svchost                12/15/2023 4:50:01 PM
smartscreen            12/15/2023 5:07:19 PM
Notepad                12/15/2023 5:20:15 PM
DataExchangeHost       12/15/2023 5:20:28 PM
backgroundTaskHost     12/15/2023 5:24:31 PM
RuntimeBroker          12/15/2023 5:24:31 PM


14.	15/12/2023 17:24
```

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
select * käsku tuleks kasutada juhul kui soovid rohkem infot saada.
Select-Object käsku tuleks kasutada kui soovid suurest osast infost paari kindlat infokillukest.
Sort-Objekt käsk aitab sorteerida saadud vastus valitud parameetri põhjal.
Format-Table väljastab vastuse tabeli kujul.
Format-List väljastab vastuse listina.
-AutoSize teeb veerud piisavalt laiad, et kogu info oleks näha.


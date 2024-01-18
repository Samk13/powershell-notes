# Powershell commands

## Get motherboard model

```powershell
Get-WmiObject win32_baseboard | Select-Object -Property Product
```

## Get the maximum capacity of the MB RAM in GB

```powershell
Get-WmiObject -Class Win32_PhysicalMemoryArray | Select-Object -Property @{Name="MaxCapacityGB";Expression={$_.MaxCapacity / 1MB}}
```

## Get the current RAM installed

```powershell
 Get-WmiObject -Class Win32_PhysicalMemory | Measure-Object -Property Capacity -Sum | Select-Object @{Name="TotalGB"; Expression={ $_.Sum / 1GB }}
```

## Get the list of connected storage devices

```powershell
 Get-PhysicalDisk | Select-Object MediaType, BusType, Model
```

## Get the current graphic driver version

```powershell
Get-WmiObject Win32_VideoController | Select-Object Name, DriverVersion
# or
Get-WmiObject Win32_VideoController | Select-Object -Property Name, DriverVersion
```

````log
Name                          DriverVersion
----                          -------------
NVIDIA GeForce RTX 4090 SUPER 31.0.15.4633
```
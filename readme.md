# block facebook and/or microsoft

A Powershell script that adds Rules to your Windows Firewall to block all facebook and microsoft ip´s..
All ip's listed here are from:

- facebook:  [https://ipinfo.io/AS32934](https://ipinfo.io/AS32934)
- microsoft: [https://ipinfo.io/AS8075](https://ipinfo.io/AS8075)

(downstreams included) and will be added to an Inbound and Outbound firewall rule to be blocked.
(IPv4 and IPv6 address ranges included)

## Installation

Download the files from github.
Start the Commandline as Admin in the folder where the script is and enter this:

__for facebook:__

```batch
powershell -ep RemoteSigned .\block-facebook-in-out.ps1
```

__for microsoft:__

```batch
powershell -ep RemoteSigned .\block-microsoft-in-out.ps1
```

### Take a look (block-facebook-in&out.ps1)

```powershell
New-NetFirewallRule -Name "110 Block facebook (in)" `
                -Description "Kill all facebook ip ranges" `
                -DisplayName "110 Block facebook (in)" `
                -Enabled True `
                -Profile Any `
                -Direction Inbound `
                -Action Block `
                -RemoteAddress ("102.132.96.0/20",
                                "102.132.96.0/24",
                                "103.4.96.0/22",
                                ...
```

### Take a look (block-microsoft-in&out.ps1)

```powershell
New-NetFirewallRule -Name "111 Block microsoft (in)" `
                -Description "Kill all microsoft ip ranges" `
                -DisplayName "111 Block microsoft (in)" `
                -Enabled True `
                -Profile Any `
                -Direction Inbound `
                -Action Block `
                -RemoteAddress("104.44.65.0/24",
"104.44.70.0/24",
"104.44.73.0/24",
"13.107.12.0/24",
```
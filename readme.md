# block facebook

A small Powershell script that adds Rules to your Windows Firewall to block all facebook ip´s..  
All ip's from facebook listed here [ipinfo.io/AS32934](https://ipinfo.io/AS32934) are added to an Inbound and Outbound rule and will be blocked.

## Installation

Start the Commandline as Admin in your folder where the script is and enter this:

```batch
powershell -ep RemoteSigned .\block_facebook.ps1
```

### Take a look

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

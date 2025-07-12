# WN10-CC-000035-STIG-IMPLEMENTATION

<img width="2462" height="1506" alt="image" src="https://github.com/user-attachments/assets/1e93e0b7-683a-4ee8-970c-8846eadb83fa" />

✅ WN10-CC-000035 — Ignore NetBIOS Name Release Requests Except from WINS Servers
📌 Why fix this
By default, Windows can accept NetBIOS name release requests from any source. An attacker on the same network could exploit this to impersonate legitimate hosts or disrupt name resolution.
Requiring the system to ignore unsolicited NetBIOS name release requests — except from trusted WINS servers — protects the integrity of network name resolution and helps prevent spoofing or session hijacking attacks.

<img width="2422" height="1644" alt="image" src="https://github.com/user-attachments/assets/ffc8b468-06dd-43da-9914-8bf6dd7d20a9" />

POWERSHELL SCRIPT USED TO FIX:
# WN10-CC-000035 - Fix: Ignore NetBIOS name release requests except from WINS servers

# Run as Administrator!

# Set NoNameReleaseOnDemand to 1 to ignore unsolicited NetBIOS name release requests
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\NetBT\Parameters" `
  -Name "NoNameReleaseOnDemand" `
  -Type DWord `
  -Value 1

Write-Output "NetBIOS name release requests now ignored except from WINS servers. STIG WN10-CC-000035 compliant."


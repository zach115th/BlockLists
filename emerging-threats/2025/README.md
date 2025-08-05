# 2025 Emerging-Threats Block Lists 🛡️

Threat actors never sit still, and neither should our defenses.  
This folder tracks **high-risk indicators of compromise (IoCs) first observed in 2025** so you can quickly feed them into firewalls, SIEMs, Suricata/Snort, Pi-hole, or any other security control that accepts plain-text lists.

---

## What you’ll find here

| Path | Content |
|------|---------|
| `toolshell/` | Indicators linked to the **SharePoint “ToolShell” exploitation wave** (CVE-2025-53770/-53771) – IPs, SHA-256 file hashes, and more.
| `autocolor/` | Indicators linked to the **"Autocolor" Linux RAT** – IPs, SHA-256 file hashes, and more.

> **Why start with ToolShell?**  
> The July 2025 campaigns were one of the most active zero-day exploitations of the year, with widespread web-shell drops and beaconing to hard-coded command-and-control hosts:contentReference[oaicite:1]{index=1}. Consolidating those IoCs here lets defenders react faster than vendor threat-feeds usually update.

*More sub-folders will be added as new 2025 threats emerge (e.g., novel ransomware families, ISP hijack infrastructure, etc.).*  

---

## Feed into your tooling

Suricata:
suricata-update add-url file://$PWD/toolshell/toolshell_ips.txt --url-type iprep

Windows Firewall:
PowerShell example:
Get-Content toolshell/toolshell_ips.txt | ForEach-Object { New-NetFirewallRule -DisplayName "BlockToolShell_$($_)" -Direction Outbound -RemoteAddress $_ -Action Block }

Pi-hole: Web GUI ➜ Group Management → Adlists ➜ add raw GitHub URL.

---

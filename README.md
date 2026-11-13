## ioc-enrichment-script

# IOC enrichment and triage script

A command line Python utility that enriches indicators of compromise (IPs, domains, file hashes) with details from VirusTotal and AbuseIPDB. Provides a verdict on risk level and potential MITRE ATT&CK techniques used. Eliminates the dull task of SOC triage by entering IOCs into multiple web consoles, just use one command for one verdict.

> **Code:** [`ioc_enrich.py`](ioc_enrich.py) — full script source.
API Keys should be placed at the beginning of the document:
VT_API_KEY = "your_virustotal_key"
ABUSE_API_KEY = "your_abuseipdb_key"

---

## Stack

- Python 3
- `vt-py` (VirusTotal API v3)
- `requests` (AbuseIPDB API v2)
- `argparse` (CLI)

---

## Usage

```bash
python3 ioc_enrich.py --ip 5.252.153.241
python3 ioc_enrich.py --domain authenticatoor.org
python3 ioc_enrich.py --hash 54e6ea47eb04634d3e87fd7787e2136ccfbcc80ade34f246a12cf93bab527f6b
```

## How the verdict is reached
```
if malicious >= 5:                       return "MALICIOUS"
if malicious >= 1 or suspicious >= 2:    return "SUSPICIOUS"
if abuse_score >= 50:                    return "SUSPICIOUS (high abuse score)"
                                         return "LIKELY BENIGN"
```

---

[ioc_enrich.py](https://github.com/user-attachments/files/34802428/ioc_enrich.py)

<img width="1280" height="536" alt="Screenshot 2026-11-13 at 12 28 21" src="https://github.com/user-attachments/assets/010f8987-4319-45cc-971a-ddeca628bd07" />


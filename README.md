[README.md](https://github.com/user-attachments/files/32416439/README.md)
# ReconKit

External attack surface & threat intelligence mapper — a single-file Python CLI for authorized reconnaissance and security posture assessment of a domain.

## Features

- WHOIS lookup
- ASN / BGP network range resolution (via RDAP/IP metadata)
- DNS record enumeration (A, AAAA, MX, NS, TXT, CNAME, SOA)
- DNSSEC validation audit
- CAA (Certificate Authority Authorization) audit
- DNS zone transfer (AXFR) testing
- WAF / reverse proxy fingerprinting
- SSL/TLS certificate inspection and protocol audit
- SPF / DMARC mail hardening checks
- Security header inspection
- HTTP endpoint probing
- robots.txt / security.txt discovery
- Passive subdomain enumeration via crt.sh
- Active subdomain brute-forcing (wordlist-based)
- Subdomain takeover checks
- Wayback Machine historical URL harvesting
- Nmap port scanning
- Hardening posture scoring
- JSON + interactive HTML report output

## Requirements

- Python 3.8+
- `requests` (see `requirements.txt`)
- Optional system tools for full functionality: `whois`, `dig` (dnsutils/bind-tools), `nmap`

Install Python dependency:

```bash
pip install -r requirements.txt
```

Install system tools (Debian/Kali/Ubuntu):

```bash
sudo apt-get install whois dnsutils nmap
```

## Usage

```bash
python3 reconkit.py <domain> --all --i-have-authorization
```

Or run individual modules:

```bash
python3 reconkit.py example.com --whois --dns --ssl --i-have-authorization
```

Run `python3 reconkit.py -h` for the full list of flags.

Reports are written to `reports/<domain>_report.json` and `reports/<domain>_report.html`.

## ⚠️ Authorization notice

This tool performs active reconnaissance techniques (including DNS zone transfer attempts, subdomain brute-forcing, and port scanning) against a target domain. **Only run it against domains you own or have explicit written authorization to test.** The `--i-have-authorization` flag is required by the tool as a reminder of this responsibility; passing it does not itself grant you legal authorization to test a target.

## License

MIT — see [LICENSE](LICENSE).

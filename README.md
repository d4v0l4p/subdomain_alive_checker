# subdomain_alive_checker

GUI tool that checks a list of URLs or subdomains and sorts them into alive and dead. You can paste them in, load them from text files or let subfinder collect them for a domain.

## How the check works

1. If the hostname doesn't resolve, it's dead.
2. Then a normal request (4 s timeout). A status code below 400 means alive.
3. If that fails, it tries to load the page in headless Chrome (7 s timeout). If that works it's alive too, otherwise dead.

5 URLs are checked at the same time.

## What you need

- Python 3
- Google Chrome (for the Selenium step, the driver is downloaded automatically)
- [subfinder](https://github.com/projectdiscovery/subfinder), only if you want to use "Run Subfinder"

## Setup

```bash
git clone https://github.com/d4v0l4p/subdomain_alive_checker.git
cd subdomain_alive_checker
pip install -r requirements.txt
```

subfinder (needs Go):

```bash
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
```

## Usage

```bash
python alive_checker.py
```

- Paste URLs into the top box, one per line, or use "Import URLs" for .txt files
- "Run Subfinder" asks for one or more root domains and adds the subdomains it finds
- "Check URLs" starts the check, alive ones go to the left, dead ones to the right
- "Generate Chart" makes a pie chart of alive vs dead

"Dashboard" and "Export HTML" are not done yet.

## License

MIT, see [LICENSE](LICENSE).

# Lab 5 - HTTP over TCP Sockets

Command-line tool `go2web` that performs HTTP/HTTPS requests using raw TCP sockets.

## Features

- `go2web -u <URL>`: sends a GET request and prints a human-readable response
- `go2web -s <search-term>`: searches via DuckDuckGo Lite and prints top 10 results
- `go2web -p <URL> -o <file.png>`: captures a full-page screenshot of a webpage
- `go2web -h`: shows help
- Redirect handling (`301`, `302`, `303`, `307`, `308`)

## Constraints Compliance

- No built-in or third-party HTTP client libraries are used
- Network requests are implemented manually over `socket` and `ssl`
- HTML output is converted to readable text (no raw tags)
- JSON output is pretty-printed

## Run

```bash
chmod +x go2web
./go2web -h
./go2web -u "https://utm.md/en/"
./go2web -s "technical university moldova"
./go2web -p "https://utm.md/en/" -o "utm-fullpage.png"
```

## Screenshot Mode Setup

Screenshot mode requires Playwright and Chromium.

```bash
pip install playwright
playwright install chromium
```

## Implementation Notes

- URL parsing: `urllib.parse`
- TCP connection: `socket`
- TLS for HTTPS: `ssl`
- HTTP response parsing: custom parser (status line, headers, body)
- Chunked transfer decoding: custom implementation
- Human-readable HTML: custom `HTMLParser`-based text extraction

## Demo GIF

Add your terminal recording GIF here for submission, for example:

```md
![go2web demo](./assets/go2web-demo.gif)
```

## Suggested Commit History

Keep several meaningful commits (avoid 1-2 total commits), for example:

1. `feat: add go2web CLI argument parser`
2. `feat: implement HTTP over TCP and HTTPS via TLS`
3. `feat: add search mode with top 10 parsing`
4. `docs: update README with usage and demo`

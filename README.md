# FreeMask

FreeMask is a tiny, client-side web tool for adding a `finalmask` fragment to VLESS and Trojan share links.

It is intentionally simple:

- Runs entirely in the browser
- Does not upload links to a server
- Supports plain share links and base64 subscription text
- Handles multiple links at once
- Can load text files and export the result
- Avoids changing links that already contain `fm=`
- Can optionally patch links using TLS / Reality
- Has no backend, database, account system, or telemetry

## Live site

**https://erfanheydarzade.github.io/FreeMask/**

The site is deployed directly from this repository with GitHub Pages.

## How it works

FreeMask takes input such as:

```text
vless://...
trojan://...
```

and appends an encoded `fm` parameter containing the configured fragment settings.

Everything is processed locally by JavaScript in the page. The input is not sent to FreeMask servers because FreeMask has no server component.

## Usage

1. Open the [live site](https://erfanheydarzade.github.io/FreeMask/).
2. Paste your links into **Your links**.
3. Optionally enable **Also patch TLS / Reality links**.
4. Copy the generated result or download `links_fm.txt`.
5. Import the resulting links into your client.

Base64 subscription text is also accepted.

## Privacy

FreeMask is a static web application. There is no API endpoint, analytics service, database, or upload service behind it.

For practical privacy, you should still inspect the page and browser extensions you use. A static site cannot magically make a compromised browser trustworthy. Humanity has invented browser extensions, after all.

## Project structure

```text
FreeMask/
├── .github/
│   └── workflows/
│       └── pages.yml
├── 404.html
├── index.html
├── CONTRIBUTING.md
├── LICENSE
├── README.md
└── SECURITY.md
```

## Development

No build system is required.

The application is plain HTML, CSS, and JavaScript. You can open `index.html` directly in a browser, or serve the repository with any static HTTP server.

For example with Python:

```powershell
python -m http.server 8080
```

Then open:

```text
http://127.0.0.1:8080/
```

## GitHub Pages

GitHub Pages publishes the repository as a static site through GitHub Actions. GitHub recommends Actions when you want a controlled deployment workflow rather than relying on the default branch publishing behavior.

The workflow lives at:

```text
.github/workflows/pages.yml
```

After enabling **Settings → Pages → Source → GitHub Actions**, pushes to `main` deploy the current site automatically.

## License

FreeMask is released under the **Unlicense**, dedicating the work to the public domain to the extent permitted by law.

See [LICENSE](LICENSE).

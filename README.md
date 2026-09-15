# apitemplate-docs-releases

Release distribution for the **APITemplate.io documentation** site.

This repository holds the published release artifacts of `apitemplate-docs` — the
source documentation that powers <https://apitemplate.io/docs/>. Source authoring
happens in the `apitemplate-docs` repository; this repository tracks what was
actually shipped, so any published version of the docs can be retrieved,
diffed, or rolled back.

- **Live documentation:** <https://apitemplate.io/docs/>
- **API reference:** <https://apitemplate.io/apiv2/>
- **Product site:** <https://apitemplate.io/>

---

## What APITemplate.io is

APITemplate.io generates **PDFs and images at scale** from reusable templates.
You design a template once — in a drag-and-drop editor or with HTML/CSS — then
call the API with JSON data to render invoices, reports, certificates, social
graphics, banners, and other branded assets.

Core capabilities covered by these docs:

| Area | What it covers |
|---|---|
| **PDF generation** | From templates, raw HTML/CSS, or a live URL. Custom headers, footers, page numbering. |
| **Image generation** | Banners, social graphics, personalized images, dynamic elements such as QR codes. |
| **Template language** | Jinja2 — variables, conditionals, loops, filters. |
| **Delivery** | Synchronous rendering, or asynchronous with webhook callbacks. |
| **Integrations** | Zapier, Make.com, n8n.io, Airtable, Bubble.io, and the REST API. |
| **Teams** | Shared workspaces and collaborative template management. |

Typical render time is around 2 seconds against a stated 99.99% uptime target,
with SOC 2 Type II certification.

---

## Documentation structure

The released docs are organized into these top-level sections:

```
Getting Started      Create an account, get an API key, build a first template,
                     make a first request
PDF Generation       Templates, HTML-to-PDF, URL-to-PDF, headers/footers,
                     page numbering
Image Generation     Drag-and-drop editor, dynamic elements, QR codes
Template Language    Jinja2 variables, conditional logic, loops and filters
Integrations         Zapier, Make.com, n8n, Airtable, Bubble.io, REST API
Teams                Collaboration and shared workspaces
FAQs & Support       Common questions, limits, contact routes
```

---

## API quick reference

Authentication is a single header on every request:

```
X-API-KEY: YOUR_API_KEY
```

### Regional endpoints

Pick the endpoint closest to your users, or the one that satisfies your data
residency requirements — request data and generated files are processed and
stored within the chosen region.

| Region | Base URL |
|---|---|
| Singapore (default) | `https://rest.apitemplate.io/v2/` |
| Europe (Frankfurt) | `https://rest-de.apitemplate.io/v2/` |
| US East (N. Virginia) | `https://rest-us.apitemplate.io/v2/` |
| Australia (Sydney) | `https://rest-au.apitemplate.io/v2/` |

Other regions are available on request via <hello@apitemplate.io>.

### Common endpoints

| Endpoint | Purpose |
|---|---|
| `POST /create-pdf` | Render a PDF from a stored template |
| `POST /create-pdf-from-html` | Render a PDF from supplied HTML/CSS |
| `POST /create-pdf-from-url` | Render a PDF from a live URL |
| `POST /create-image` | Render an image from a stored template |
| `GET /list-templates` | List templates available to the account |

### Example request

```bash
curl -X POST "https://rest.apitemplate.io/v2/create-pdf?template_id=YOUR_TEMPLATE_ID" \
  -H "X-API-KEY: YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
        "invoice_number": "INV-0001",
        "customer_name": "Acme Pte Ltd",
        "total": "1,250.00"
      }'
```

---

## Official SDKs

| Language | Repository |
|---|---|
| Python | <https://github.com/APITemplate-io/apitemplateio-python> |
| JavaScript | <https://github.com/APITemplate-io/apitemplateio-javascript> |
| PHP | <https://github.com/APITemplate-io/apitemplateio-php> |
| C# | <https://github.com/APITemplate-io/apitemplateio-csharp> |
| Java | <https://github.com/APITemplate-io/apitemplateio-java> |

UiPath activities are also published by APITemplate.io.

---

## Releases

Each release in this repository corresponds to a published state of the
documentation site.

- Releases are tagged and listed under
  [Releases](https://github.com/AlphaCloudTechnologies/apitemplate-docs-releases/releases).
- To inspect a specific published version, check out its tag:

  ```bash
  git clone git@github.com:AlphaCloudTechnologies/apitemplate-docs-releases.git
  cd apitemplate-docs-releases
  git tag --list
  git checkout <tag>
  ```

- To see what changed between two published versions:

  ```bash
  git diff <older-tag>..<newer-tag>
  ```

Content changes belong in the upstream `apitemplate-docs` source repository, not
here — edits made directly to this repository are overwritten by the next
release.

---

## Support

- Documentation: <https://apitemplate.io/docs/>
- Email: <hello@apitemplate.io>

---

## License

Documentation content is © APITemplate.io. See the upstream repository for
licensing terms.

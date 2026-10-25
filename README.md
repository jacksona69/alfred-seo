# SEO Inspector for Alfred 5

**A fast, free technical SEO checker for Alfred 5, with detailed interactive reports in Safari.**

SEO Inspector lets you inspect any web page directly from Alfred. Check metadata, headings, images, structured data, internal links and more, without opening Developer Tools or subscribing to an SEO service.

<img width="3022" height="1714" alt="661946C1-5D55-4D11-A64C-CC7B023A99A5-seo-inspector-report" src="https://github.com/user-attachments/assets/cf0aa5f7-88c7-4f08-94ea-2a76eac4d8bb" />

Built by **Adam Jackson**.

## Features

- **Quick SEO checks:** HTTP status, redirects, page titles, meta descriptions, canonical URLs and robots directives.
- **Heading analysis:** Visual H1–H6 hierarchy with potential structural issues highlighted.
- **Image audit:** Check alt text, dimensions, loading attributes and image markup.
- **Structured data:** Inspect JSON-LD with readable formatting and expandable details.
- **Internal links:** Check up to 20 internal links for errors and redirects.
- **Open Graph:** Inspect social sharing metadata.
- **Before & after comparisons:** Save dated snapshots and identify changes between inspections.
- **Interactive HTML reports:** Search, filter and explore results in Safari.

Findings appear as errors, warnings or information, without arbitrary SEO scores.

## Requirements

- macOS 13 or later, Apple silicon or Intel
- Alfred 5 with Powerpack
- Safari

**No Python, Homebrew, additional software, API keys or subscriptions required.** Everything needed comes inside the workflow package.

## Installation

1. Download the latest `.alfredworkflow` file from [Releases](../../releases).
2. Double-click the downloaded file.
3. Click **Import** in Alfred.

That's it!

## Usage

Open Alfred and enter:

| Command | Action |
|---|---|
| `seo` | Inspect the current Safari tab |
| `seo example.com` | Inspect a specified website |
| `seo https://example.com/page/` | Inspect a specific page |
| `seo !` | Refresh the current Safari page and compare |
| `seo ! example.com` | Force a fresh inspection and compare with the previous snapshot |

Alfred displays a quick summary. Press **Return** to open the full interactive report in Safari.

Results are cached for five minutes. Use `!` after `seo` to bypass the cache.

## Configuration

SEO Inspector supports optional image-sizing exclusions for gallery systems that intentionally omit intrinsic image dimensions.

Configure these in **Alfred Preferences → Workflows → SEO Inspector → Configure Workflow**.

Exclusions affect image dimension warnings only. Other image checks remain active.

## Limitations

SEO Inspector analyses the HTML returned by the website. It doesn't execute JavaScript, measure Core Web Vitals or determine Google indexing and search rankings.

Internal link checking covers up to 20 links per page. Results reflect the website's response at the time of inspection.

## Privacy

SEO Inspector runs locally on your Mac. It contacts the websites you inspect and stores reports and snapshots in Alfred's workflow cache. It uses no external analytics service or API.

## Licence

MIT Licence

Copyright © 2026 Adam Jackson

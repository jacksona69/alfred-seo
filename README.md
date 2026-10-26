# SEO Inspector for Alfred 5

**A fast, free technical SEO checker for Alfred 5, with detailed interactive reports in Safari.**

SEO Inspector lets you inspect any web page directly from Alfred. Check metadata, headings, images, structured data, internal links and more, without opening Developer Tools or subscribing to an SEO service.

<img width="3022" height="1714" alt="SEO Inspector for Alfred" src="https://github.com/user-attachments/assets/d1599a16-0539-46fb-8ec9-11b5f2916721" />

Created by **Adam Jackson**, with development assistance from **ChatGPT Work**.

## Features

- **Executive summary:** See issues requiring attention at the top of each report, with repeated warnings grouped together and links to the relevant details.
- **Quick SEO checks:** HTTP status, redirects, page titles, meta descriptions, canonical URLs and robots directives.
- **Heading analysis:** Visual H1–H6 hierarchy with potential structural issues highlighted.
- **Image audit:** Check alt text, dimensions, loading attributes and image markup.
- **Structured data:** Inspect JSON-LD with readable formatting and expandable details.
- **Internal links:** Check up to 20 internal links for errors and redirects.
- **Social sharing metadata:** Inspect Open Graph and optional Twitter/X Card properties.
- **Before & after comparisons:** Save dated snapshots and identify changes between inspections.
- **Interactive HTML reports:** Search, filter and explore results in Safari, with collapsible sections and Expand all / Collapse all controls.
- **Configurable inspections:** Enable or disable individual SEO checks through Alfred's workflow settings.

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

## Understanding the report

Each report begins with an **Executive Summary**, highlighting errors and warnings that may need attention. Repeated issues are grouped together to make it easier to identify problems affecting multiple elements.

Click an issue to jump to its detailed findings.

The report's detailed sections are collapsed by default, with a short summary showing what each contains. Expand individual sections as needed, or use **Expand all** and **Collapse all**.

You can also search and filter the report to investigate particular findings.

## Configuration

Choose which inspections SEO Inspector performs using Alfred's native workflow configuration.

Open **Alfred Preferences → Workflows → SEO Inspector → Configure Workflow**.

Available inspection modules include:

- Metadata and directives
- Heading hierarchy
- Image SEO audit
- Internal link checking
- JSON-LD structured data
- Open Graph metadata
- Twitter/X Card metadata
- Before & after comparisons

Most checks are enabled by default. **Twitter/X Card inspection is disabled by default** but can be enabled if required.

Disabling a module removes its checks and associated findings from the report.

### Image dimension exclusions

SEO Inspector also supports optional image-sizing exclusions for gallery systems that intentionally omit intrinsic image dimensions.

Exclusions affect image dimension warnings only. Other image checks remain active when the image audit is enabled.

## Limitations

SEO Inspector analyses the HTML returned by the website. It doesn't execute JavaScript, measure Core Web Vitals or determine Google indexing and search rankings.

Internal link checking covers up to 20 links per page. Results reflect the website's response at the time of inspection.

SEO findings are intended to help identify potential issues for investigation. Not every warning necessarily represents a problem requiring correction.

## Privacy

SEO Inspector runs locally on your Mac. It contacts the websites you inspect and stores reports and snapshots in Alfred's workflow cache. It uses no external analytics service or API.

## Licence

MIT Licence

Copyright © 2026 Adam Jackson

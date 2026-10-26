# SEO Inspector for Alfred 5

**A fast, free technical SEO checker for Alfred 5, with detailed interactive reports in Safari.**

SEO Inspector lets you inspect any web page directly from Alfred. Check metadata, headings, images, structured data, internal links and more, without opening Developer Tools or subscribing to an SEO service.

<img width="3024" height="1714" alt="SEO Inspector v2 4 0" src="https://github.com/user-attachments/assets/7b9ba3d3-4625-494b-91ce-ba33a5cdbeda" />

Created by **Adam Jackson**, with development assistance from **ChatGPT Work**.

## Features

- **Executive summary:** See errors and warnings requiring attention at the top of each report, with repeated issues grouped together and links to the relevant details.
- **Quick SEO checks:** HTTP status, redirects, page titles, meta descriptions, canonical URLs and robots directives.
- **Heading analysis:** Visual H1–H6 hierarchy with potential structural issues highlighted.
- **Image SEO audit:** Check alt text, image sources, dimensions, loading attributes and responsive image markup.
- **Responsive image support:** Recognises `src`, `srcset` and `<picture>` sources, including multiple image candidates.
- **Layout-sizing analysis:** Distinguishes missing intrinsic dimensions from situations where layout reservation cannot be established from source HTML.
- **Structured data:** Inspect JSON-LD with readable formatting and expandable details.
- **Internal links:** Check up to 20 internal links for errors and redirects.
- **Social sharing metadata:** Inspect Open Graph and optional Twitter/X Card properties.
- **Before & after comparisons:** Save dated snapshots and identify changes between inspections.
- **Interactive HTML reports:** Search, filter and explore results in Safari, with collapsible sections and Expand all / Collapse all controls.
- **Configurable inspections:** Enable or disable individual SEO checks through Alfred's workflow settings.

Findings are classified as errors, warnings or information, without arbitrary SEO scores.

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

Installing a newer version updates the existing workflow.

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

### Executive summary

Each report begins with an executive summary highlighting errors and warnings that may require attention.

Repeated issues are grouped together, making it easier to identify problems affecting multiple elements.

Click an issue to navigate to its detailed findings.

### Detailed inspection sections

Detailed sections are collapsed by default, with a short summary showing what each contains.

Expand individual sections as needed, or use **Expand all** and **Collapse all**.

You can search and filter the report to investigate particular findings.

### Image SEO audit

The image audit checks image sources, alternative text, dimensions and loading attributes.

It supports responsive image markup, including `srcset` and `<picture>` elements, and identifies multiple source candidates where present.

A compact image table provides an overview of each image. Expand individual rows to inspect source URLs, alternative text, attributes and findings.

Images can be filtered by issues, missing alternative text, source concerns and dimensions.

**Understanding layout-sizing findings**

SEO Inspector distinguishes between missing image dimensions and cases where layout reservation cannot be established from source HTML.

A page may use external CSS or responsive layout techniques to reserve image space. Because SEO Inspector doesn't render the page or inspect its computed layout, it cannot always determine whether an image will cause layout shift.

In these cases, the report provides an informational observation rather than automatically treating the image as problematic.

Similarly, responsive image sources are recognised from the supplied HTML, avoiding false errors caused by relying on the `src` attribute alone.

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

Exclusions affect image dimension findings only. Other image checks remain active when the image audit is enabled.

## Limitations

SEO Inspector analyses the HTML returned by the website. It doesn't execute JavaScript, inspect the fully rendered layout, measure Core Web Vitals or determine Google indexing and search rankings.

Some images may depend on JavaScript for their sources, while others may use external CSS to establish their dimensions. Where these behaviours cannot be verified from the supplied HTML, SEO Inspector reports the uncertainty rather than assuming a problem exists.

Internal link checking covers up to 20 links per page. Results reflect the website's response at the time of inspection.

SEO findings are intended to help identify potential issues for investigation. Not every warning represents a problem requiring correction.

## Privacy

SEO Inspector runs locally on your Mac. It contacts the websites you inspect and stores reports and snapshots in Alfred's workflow cache. It uses no external analytics service or API.

## Licence

MIT Licence

Copyright © 2026 Adam Jackson

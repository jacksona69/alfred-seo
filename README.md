# SEO Inspector for Alfred 5

**A fast, free technical SEO checker for Alfred 5, with detailed interactive reports in Safari.**

SEO Inspector lets you inspect any web page directly from Alfred. Check metadata, redirects, headings, images, structured data, internal links and social sharing previews, without opening Developer Tools or subscribing to an SEO service.

Created by **Adam Jackson**, with development assistance from **ChatGPT Work**.

<img width="3024" height="1714" alt="SEO Inspector v2 5 0" src="https://github.com/user-attachments/assets/934f2ebd-0586-41da-a5ff-466a1e81e172" />

## Features

- **Executive summary:** See errors and warnings requiring attention at the top of each report, with repeated issues grouped together and links to the relevant details.
- **Quick SEO checks:** HTTP status, page titles, meta descriptions, canonical URLs and robots directives.
- **Redirect-chain inspection:** Follow individual HTTP redirects, view status codes and destinations, and identify problematic redirect chains.
- **Heading analysis:** Visual H1–H6 hierarchy with potential structural issues highlighted.
- **Image SEO audit:** Check alt text, image sources, dimensions, loading attributes and responsive image markup.
- **Image previews:** View inspected images in a modal lightbox without leaving the report. Images are never enlarged beyond their natural dimensions.
- **Responsive image support:** Recognises `src`, `srcset` and `<picture>` sources, including multiple image candidates.
- **Layout-sizing analysis:** Distinguishes missing intrinsic dimensions from situations where layout reservation cannot be established from source HTML.
- **Structured data:** Inspect JSON-LD with readable formatting and expandable details.
- **Internal links:** Check up to 20 internal links for errors and redirects.
- **Social sharing previews:** Inspect Open Graph and optional Twitter/X Card metadata, with visual previews showing how a shared page might appear.
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

### Redirect-chain inspection

SEO Inspector examines the redirects between the requested URL and the final destination.

The report shows the individual redirect steps, including HTTP status codes and destination URLs, and identifies potential problems such as redirect loops, excessive chains or invalid destinations.

Ordinary redirects, including HTTP-to-HTTPS redirects, aren't automatically treated as problems.

### Image SEO audit

The image audit checks image sources, alternative text, dimensions and loading attributes.

It supports responsive image markup, including `srcset` and `<picture>` elements, and identifies multiple source candidates where present.

A compact image table provides an overview of each image. Expand individual rows to inspect source URLs, alternative text, attributes and findings.

Images can be filtered by issues, missing alternative text, source concerns and dimensions.

**Image previews**

Click **Preview image** to open an image in a modal lightbox without leaving the report or changing its scroll position.

Images display at their natural size where possible. Larger images are scaled down to fit within the lightbox, which occupies no more than 80% of the browser viewport. Smaller images are never enlarged.

You can open the original image or copy its URL directly from the lightbox.

Images are only downloaded for preview when you explicitly request them.

**Understanding layout-sizing findings**

SEO Inspector distinguishes between missing image dimensions and cases where layout reservation cannot be established from source HTML.

A page may use external CSS or responsive layout techniques to reserve image space. Because SEO Inspector doesn't render the page or inspect its computed layout, it cannot always determine whether an image will cause layout shift.

In these cases, the report provides an informational observation rather than automatically treating the image as problematic.

Similarly, responsive image sources are recognised from the supplied HTML, avoiding false errors caused by relying on the `src` attribute alone.

### Social sharing previews

The Open Graph and optional Twitter/X sections include visual sharing-card previews.

These show the title, description, website domain and associated image, helping you assess how your page might look when shared.

Images remain unloaded until you choose to display them. You can also open them in the same lightbox used by the Image SEO Audit.

Twitter/X previews account for available Twitter-specific metadata and Open Graph fallbacks.

**These are representative previews, not exact reproductions of individual platforms.** Social networks may display or crop images differently, and their rendering behaviour can change.

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

**Excluded images remain available for inspection and preview.** Excluding an image from dimension warnings does not remove it from the audit or prevent its image preview from loading.

## Limitations

SEO Inspector analyses the HTML returned by the website. It doesn't execute JavaScript, inspect the fully rendered layout, measure Core Web Vitals or determine Google indexing and search rankings.

Some images may depend on JavaScript for their sources, while others may use external CSS to establish their dimensions. Where these behaviours cannot be verified from the supplied HTML, SEO Inspector reports the uncertainty rather than assuming a problem exists.

Image previews depend on the remote image being accessible from Safari. Some image hosts may restrict direct loading, even when the image works correctly on the original website. A failed preview does not automatically indicate an SEO problem.

Social sharing previews are illustrative and cannot guarantee how Facebook, LinkedIn, Twitter/X or other platforms will display a particular page.

Internal link checking covers up to 20 links per page. Results reflect the website's response at the time of inspection.

SEO findings are intended to help identify potential issues for investigation. Not every warning represents a problem requiring correction.

## Privacy

SEO Inspector runs locally on your Mac. It contacts the websites you inspect and stores reports and snapshots in Alfred's workflow cache. It uses no external analytics service or API.

**Image previews are loaded only when you explicitly request them.** Previewing an image makes a request to the server hosting that image, which may be a third-party image host or content delivery network. No images are preloaded simply because you open a report or expand an inspection section.

SEO Inspector does not collect usage analytics, send telemetry or check for updates in the background.

## Licence

MIT Licence

Copyright © 2026 Adam Jackson

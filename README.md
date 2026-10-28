# SEO Inspector for Alfred 5

**A fast, free technical SEO checker for Alfred 5, with detailed interactive reports in Safari.**

SEO Inspector lets you inspect any web page directly from Alfred. Check metadata, redirects, headings, images, structured data, internal links and social sharing previews, without opening Developer Tools or subscribing to an SEO service.

Created by **Adam Jackson**, with development assistance from **ChatGPT Work**.

<img width="3024" height="1714" alt="SEO Inspector v2 6 0" src="https://github.com/user-attachments/assets/f83350eb-070c-4e64-8a84-930d50568bd6" />

## Features

- **Executive summary:** See errors and warnings requiring attention at the top of each report, with repeated issues grouped together and links to the relevant details.
- **Quick SEO checks:** HTTP status, page titles, meta descriptions, canonical URLs and robots directives.
- **Redirect-chain inspection:** Follow individual HTTP redirects, view status codes and destinations, and identify problematic redirect chains.
- **Heading analysis:** Visual H1–H6 hierarchy with potential structural issues highlighted.
- **Image SEO audit:** Check alt text, image sources, dimensions, loading attributes and responsive image markup.
- **Image previews and aspect-ratio verification:** View images in a modal lightbox and identify mismatches between declared and actual image proportions, without downloading images during the initial inspection.
- **Responsive image support:** Recognises `src`, `srcset` and `<picture>` sources, including multiple image candidates.
- **Layout-sizing analysis:** Distinguishes missing intrinsic dimensions from situations where layout reservation cannot be established from source HTML.
- **Structured data:** Inspect JSON-LD with readable formatting and expandable details.
- **Internal links:** Check up to 20 internal URLs for errors and redirects, and identify clearly missing same-page anchor targets.
- **Social sharing previews:** Inspect Open Graph and optional Twitter/X Card metadata, with visual previews showing how a shared page might appear.
- **View robots.txt:** Open the inspected website's robots.txt file in Safari for manual review.
- **Copy report summary:** Copy a structured, plain-text summary of the inspection, including metadata, redirects, audit results and findings.
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

The **Copy report summary** action creates a plain-text overview suitable for sharing with a developer, pasting into an issue tracker or discussing with an AI assistant.

The copied summary includes the response status, redirects, metadata, headings, images, links, structured data, social metadata and relevant findings. It remains useful even when no errors or warnings are detected.

### Detailed inspection sections

Detailed sections are collapsed by default, with a short summary showing what each contains.

Expand individual sections as needed, or use **Expand all** and **Collapse all**.

You can search and filter the report to investigate particular findings.

### Redirect-chain inspection

SEO Inspector examines the redirects between the requested URL and the final destination.

The report shows the individual redirect steps, including HTTP status codes and destination URLs, and identifies potential problems such as redirect loops, excessive chains or invalid destinations.

Ordinary redirects, including HTTP-to-HTTPS redirects, aren't automatically treated as problems.

### Metadata and robots directives

SEO Inspector checks page titles, meta descriptions, canonical URLs, meta robots directives and the HTTP `X-Robots-Tag` header.

A **View robots.txt** shortcut opens the website's robots.txt file in Safari for manual inspection.

SEO Inspector does not automatically retrieve or analyse robots.txt, evaluate crawler-specific permissions or inspect sitemap contents.

### Image SEO audit

The image audit checks image sources, alternative text, dimensions and loading attributes.

It supports responsive image markup, including `srcset` and `<picture>` elements, and identifies multiple source candidates where present.

A compact image table provides an overview of each image. Expand individual rows to inspect source URLs, alternative text, attributes and findings.

Images can be filtered by issues, missing alternative text, source concerns and dimensions.

**Image previews and aspect-ratio verification**

Click **Preview image** to open an image in a modal lightbox without leaving the report or changing its scroll position.

Images display at their natural size where possible. Larger images are scaled down to fit within the lightbox, which occupies no more than 80% of the browser viewport. Smaller images are never enlarged.

You can open the original image or copy its URL directly from the lightbox.

Images are only downloaded for preview when you explicitly request them.

When an image is previewed, SEO Inspector can compare its actual dimensions with the dimensions declared in the HTML.

If their aspect ratios differ significantly, a warning appears in the lightbox showing both sets of dimensions.

For example, an image declared as 1280 × 720 but actually measuring 1200 × 836 has substantially different proportions and will be flagged when the comparison is reliable.

An image declared as 600 × 400 but actually measuring 1200 × 800 will not be flagged, because the proportions match.

These checks are performed on demand. They do not alter the original report's error or warning totals.

**Understanding layout-sizing findings**

SEO Inspector distinguishes between missing image dimensions and cases where layout reservation cannot be established from source HTML.

A page may use external CSS or responsive layout techniques to reserve image space. Because SEO Inspector doesn't render the page or inspect its computed layout, it cannot always determine whether an image will cause layout shift.

In these cases, the report provides an informational observation rather than automatically treating the image as problematic.

Similarly, responsive image sources are recognised from the supplied HTML, avoiding false errors caused by relying on the `src` attribute alone.

An aspect-ratio mismatch may affect how an image is displayed, but it does not necessarily mean a layout shift has occurred.

### Internal links and same-page anchors

SEO Inspector checks up to 20 internal URLs for HTTP errors and redirects.

It also examines same-page fragment links, such as `#contact` or `#pricing`, and checks for matching targets in the supplied HTML.

Clearly missing targets are reported as warnings. Anchor validation uses the HTML already retrieved and does not require additional HTTP requests or count towards the 20-link checking limit.

Because SEO Inspector does not execute page JavaScript, dynamically generated anchor targets may not be verifiable.

### Social sharing previews

The Open Graph and optional Twitter/X sections include visual sharing-card previews.

These show the title, description, website domain and associated image, helping you assess how your page might look when shared.

Images remain unloaded until you choose to display them. You can also open them in the same lightbox used by the Image SEO Audit.

When Open Graph and Twitter/X previews reference the same effective image URL, loading one also populates the other, avoiding duplicate image downloads.

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

On-demand aspect-ratio verification compares the loaded image with reliable declared dimensions. It does not measure actual browser layout shifts or guarantee that an image is displayed incorrectly.

Image previews depend on the remote image being accessible from Safari. Some image hosts may restrict direct loading, even when the image works correctly on the original website. A failed preview does not automatically indicate an SEO problem.

Social sharing previews are illustrative and cannot guarantee how Facebook, LinkedIn, Twitter/X or other platforms will display a particular page.

Internal HTTP link checking covers up to 20 URLs per page. Same-page anchor checking uses the supplied HTML and may not identify targets generated dynamically by JavaScript.

The robots.txt shortcut is for manual viewing only. SEO Inspector does not interpret robots.txt rules, fetch sitemaps or establish whether a search engine can or will index a page.

SEO findings are intended to help identify potential issues for investigation. Not every warning represents a problem requiring correction.

## Privacy

SEO Inspector runs locally on your Mac. It contacts the websites you inspect and stores reports and snapshots in Alfred's workflow cache. It uses no external analytics service or API.

**Image previews are loaded only when you explicitly request them.** Previewing an image makes a request to the server hosting that image, which may be a third-party image host or content delivery network. No images are preloaded simply because you open a report or expand an inspection section.

The robots.txt shortcut opens the website's publicly available file in Safari only when requested.

Copying a report summary uses the local clipboard and does not transmit the report to an external service.

SEO Inspector does not collect usage analytics, send telemetry or check for updates in the background.

## Licence

MIT Licence

Copyright © 2026 Adam Jackson

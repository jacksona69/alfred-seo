# SEO Inspector for Alfred 5

**A fast, free technical SEO checker for Alfred 5, with detailed interactive reports in Safari.**

SEO Inspector lets you inspect any web page directly from Alfred. Check metadata, canonical URLs, redirects, headings, images, structured data, internal links, link accessibility and social sharing previews, without opening Developer Tools or subscribing to an SEO service.

Created by **Adam Jackson**, with development assistance from **ChatGPT Work**.

<img width="3024" height="1718" alt="SEO Inspector v2 7 1" src="https://github.com/user-attachments/assets/41916356-9cea-4cec-9215-a3918ad74520" />

## What's new in v2.7.1

This maintenance release refines how SEO Inspector reports page title and meta-description lengths.

- Modest departures from conventional length guidance now appear as informational observations rather than warnings.
- Genuinely excessive lengths can still generate warnings.
- Reporting reflects the fact that search engines don't impose fixed character limits and may shorten or rewrite snippets.
- Reduces unnecessary warnings while retaining useful guidance.

All other features and existing inspection behaviour remain unchanged.

## Features

- **Executive summary:** See errors and warnings requiring attention at the top of each report, with repeated issues grouped together and links to the relevant details.
- **Quick SEO checks:** HTTP status, page titles, meta descriptions, canonical URLs and robots directives.
- **Canonical URL validation:** Identify missing, malformed, duplicate or conflicting canonical declarations, check canonical targets for redirects and HTTP errors, and review cross-page canonical references.
- **Redirect-chain inspection:** Follow individual HTTP redirects, view status codes and destinations, and identify problematic redirect chains.
- **Heading analysis:** Visual H1–H6 hierarchy with potential structural issues highlighted.
- **Image SEO audit:** Check alt text, image sources, dimensions, loading attributes and responsive image markup.
- **Image previews and aspect-ratio verification:** Preview displayed images, access separate gallery/lightbox resources where available, and identify mismatches between declared and actual image proportions on demand.
- **Responsive image support:** Recognises `src`, `srcset` and `<picture>` sources, with clearer identification of displayed, responsive and gallery image resources.
- **Tracking pixel recognition:** Identifies recognisable tracking pixels and distinguishes them from ordinary content images.
- **Layout-sizing analysis:** Distinguishes missing intrinsic dimensions from situations where layout reservation cannot be established from source HTML.
- **Structured data:** Inspect JSON-LD with readable formatting and expandable details.
- **Internal links:** Check up to 20 internal URLs for errors and redirects, and identify clearly missing same-page anchor targets.
- **Link text analysis:** Identify links with missing or unhelpful accessible names, image-only links without suitable labels, and generic link text. Recognises accessible naming attributes, including HTML `title` fallbacks.
- **Cloudflare email protection:** Recognises identifiable email-obfuscation links to reduce false broken-link warnings.
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

### Metadata, canonical URLs and robots directives

SEO Inspector checks page titles, meta descriptions, canonical URLs, meta robots directives and the HTTP `X-Robots-Tag` header.

**Title and meta-description lengths**

SEO Inspector distinguishes modest departures from conventional length guidance from genuinely excessive lengths.

Modest deviations appear as informational observations, while unusually long values can generate warnings. Search engines don't enforce fixed character limits, and the length of a displayed snippet depends on several factors.

These findings provide practical guidance rather than definitive predictions of how a search result will appear.

**Canonical URL validation**

The canonical inspection examines declarations in the page HTML and checks for missing, malformed, duplicate or conflicting values.

Where verification is available, it also reports the canonical target's HTTP response, final destination and redirects.

A canonical pointing to another page isn't automatically an error. Cross-page canonicals can be intentional, so SEO Inspector distinguishes observations from more definite problems.

Network failures or inaccessible canonical targets don't automatically mean a canonical is invalid.

**Robots.txt**

A **View robots.txt** shortcut opens the website's robots.txt file in Safari for manual inspection.

SEO Inspector does not automatically retrieve or analyse robots.txt, evaluate crawler-specific permissions or inspect sitemap contents.

### Image SEO audit

The image audit checks image sources, alternative text, dimensions and loading attributes.

It supports responsive image markup, including `srcset` and `<picture>` elements, and distinguishes displayed image resources from alternative candidates.

A compact image table provides an overview of each image. Expand individual rows to inspect source URLs, alternative text, attributes and findings.

Findings appear in one list, using severity colours for errors, warnings and informational observations. **No findings** appears only when no findings of any severity exist.

Images can be filtered by issues, missing alternative text, source concerns and dimensions.

**Image previews and gallery images**

Click **Preview image** to open the displayed image in a modal lightbox without leaving the report or changing its scroll position.

For galleries that use separate thumbnail and full-resolution image resources, SEO Inspector identifies their different roles. The main preview shows the displayed thumbnail, while a separate action provides access to the gallery image where available.

Responsive images and supported lazy-loading implementations are handled according to their source markup.

Images display at their natural size where possible. Larger images are scaled down to fit within the lightbox, which occupies no more than 80% of the browser viewport. Smaller images are never enlarged.

You can open the image or copy its URL directly from the lightbox.

Images are only downloaded for preview when you explicitly request them.

**On-demand aspect-ratio verification**

When an image is previewed, SEO Inspector can compare its actual dimensions with the dimensions declared in the HTML.

If their aspect ratios differ significantly, a warning appears in the lightbox showing both sets of dimensions.

For example, an image declared as 1280 × 720 but actually measuring 1200 × 836 has substantially different proportions and will be flagged when the comparison is reliable.

An image declared as 600 × 400 but actually measuring 1200 × 800 will not be flagged, because the proportions match.

The comparison uses the appropriate image resource, avoiding mismatches between a thumbnail's dimensions and an unrelated gallery image.

These checks occur on demand and do not alter the original report's error or warning totals.

**Tracking pixels**

SEO Inspector recognises identifiable tracking pixels, including certain hidden images used by analytics and advertising systems.

Where the available evidence reliably identifies a tracking pixel, it treats the image separately from ordinary content images rather than raising misleading missing-alt warnings.

Small or hidden images aren't automatically assumed to be tracking pixels.

**Understanding layout-sizing findings**

SEO Inspector distinguishes between missing image dimensions and cases where layout reservation cannot be established from source HTML.

A page may use external CSS or responsive layout techniques to reserve image space. Because SEO Inspector doesn't render the page or inspect its computed layout, it cannot always determine whether an image will cause layout shift.

In these cases, the report provides an informational observation rather than automatically treating the image as problematic.

Similarly, responsive image sources are recognised from the supplied HTML, avoiding false errors caused by relying on the `src` attribute alone.

An aspect-ratio mismatch may affect how an image is displayed, but it does not necessarily mean a layout shift has occurred.

### Internal links, link text and same-page anchors

SEO Inspector checks up to 20 internal URLs for HTTP errors and redirects.

The report distinguishes HTTP response codes from separate request or network failures.

**Link text analysis**

SEO Inspector also examines link text and accessible naming information.

It can identify links with no meaningful accessible name, image-only links without suitable labels and generic text that provides little information about the destination.

The analysis considers visible text, `aria-label`, `aria-labelledby`, image alternative text and HTML `title` attributes where appropriate.

This analysis uses the supplied HTML and does not require additional network requests.

**Same-page anchors**

SEO Inspector examines same-page fragment links, such as `#contact` or `#pricing`, and checks for matching targets in the supplied HTML.

Clearly missing targets are reported as warnings. Anchor validation uses the HTML already retrieved and does not require additional HTTP requests or count against the 20-link checking limit.

Because SEO Inspector does not execute page JavaScript, dynamically generated anchor targets may not be verifiable.

**Cloudflare email protection**

Recognisable Cloudflare email-obfuscation links are distinguished from ordinary navigational links, reducing false broken-link reports for generated email-protection endpoints.

Genuine broken links remain subject to normal checking.

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

SEO Inspector supports optional image-sizing exclusions for gallery systems that intentionally omit intrinsic image dimensions.

Exclusions affect image dimension findings only. Other image checks remain active when the image audit is enabled.

**Excluded images remain available for inspection and preview.** Excluding an image from dimension warnings does not remove it from the audit or prevent its image preview from loading.

## Limitations

SEO Inspector analyses the HTML returned by the website. It doesn't execute JavaScript, inspect the fully rendered layout, measure Core Web Vitals or determine Google indexing and search rankings.

Some images may depend on JavaScript for their sources, while others may use external CSS to establish their dimensions. Where these behaviours cannot be verified from the supplied HTML, SEO Inspector reports the uncertainty rather than assuming a problem exists.

Canonical target verification depends on the remote server responding to the inspection request. A blocked or inconclusive response doesn't necessarily indicate a broken canonical.

Link text analysis uses the supplied HTML and cannot reproduce every aspect of a browser's accessibility tree or dynamically generated content.

On-demand aspect-ratio verification compares the loaded image with reliable declared dimensions. It does not measure actual browser layout shifts or guarantee that an image is displayed incorrectly.

Image previews depend on the remote image being accessible from Safari. Some image hosts may restrict direct loading, even when the image works correctly on the original website. A failed preview does not automatically indicate an SEO problem.

Social sharing previews are illustrative and cannot guarantee how Facebook, LinkedIn, Twitter/X or other platforms will display a particular page.

Internal HTTP link checking covers up to 20 URLs per page. Same-page anchor and link text analysis use the supplied HTML and may not identify content generated dynamically by JavaScript.

The robots.txt shortcut is for manual viewing only. SEO Inspector does not interpret robots.txt rules, fetch sitemaps or establish whether a search engine can or will index a page.

SEO findings are intended to help identify potential issues for investigation. Not every warning represents a problem requiring correction.

## Privacy

SEO Inspector runs locally on your Mac. It contacts the websites you inspect and stores reports and snapshots in Alfred's workflow cache. It uses no external analytics service or API.

**Image previews are loaded only when you explicitly request them.** Previewing an image makes a request to the server hosting that image, which may be a third-party image host or content delivery network. No images are preloaded simply because you open a report or expand an inspection section.

Canonical target verification and internal link checking may make additional direct requests to the websites concerned. These requests do not send inspection data to a third-party SEO service.

The robots.txt shortcut opens the website's publicly available file in Safari only when requested.

Copying a report summary uses the local clipboard and does not transmit the report to an external service.

SEO Inspector does not collect usage analytics, send telemetry or check for updates in the background.

## Licence

MIT Licence

Copyright © 2026 Adam Jackson

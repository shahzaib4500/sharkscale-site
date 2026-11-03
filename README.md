# sharkscale-site

Static site behind **https://legal.sharkscale.online** — the landing page plus
the privacy policy and terms of service for every app we publish.

On a `legal.` subdomain, not the apex: `sharkscale.online` itself already
redirects to the Upwork Leads Portal, and a domain can only point at one
place. Play only needs the URL to be public and stable, which a subdomain is.

Hosted on GitHub Pages from `main`. No build step: plain HTML and one
stylesheet, so a policy correction is an edit and a push.

## Layout

```
index.html                            landing page, lists every app
styles.css                            shared styles
CNAME                                 custom domain for GitHub Pages
privacy/index.html                    → /privacy/  (general policy)
apps/<app-slug>/privacy/index.html    → /apps/<app-slug>/privacy/  (app-specific, optional)
apps/<app-slug>/terms/index.html      → /apps/<app-slug>/terms/
```

The general privacy policy is **company-wide** — it says so itself: "applies to
use all application on all platforms" — and is the default. An app whose data
handling differs materially can have its own policy, which replaces the general
one for that app: QR Scanner, Language Translator and Recover Photos do, because
each handles data differently from the AI PDF Scanner flows the general policy
describes. Subscription terms name a specific app and its plans, so those are
per app.

## Live URLs

| App | Package | Privacy | Terms |
| --- | --- | --- | --- |
| AI PDF Scanner - Document Scanner | `com.pdfreadermobileapp` | [/privacy/](https://legal.sharkscale.online/privacy/) | [/apps/ai-pdf-scanner/terms/](https://legal.sharkscale.online/apps/ai-pdf-scanner/terms/) |
| Language Translator: Documents | `com.sharkstack.aitranslator` | [/apps/ai-translator/privacy/](https://legal.sharkscale.online/apps/ai-translator/privacy/) | [/apps/ai-translator/terms/](https://legal.sharkscale.online/apps/ai-translator/terms/) |
| Recover Photos: File Recovery | `com.photorecoverymobileapp` | [/apps/photo-recovery/privacy/](https://legal.sharkscale.online/apps/photo-recovery/privacy/) | [/apps/photo-recovery/terms/](https://legal.sharkscale.online/apps/photo-recovery/terms/) |
| QR Scanner & Barcode Scanner | `com.qrmobileapp` | [/apps/qr-scanner/privacy/](https://legal.sharkscale.online/apps/qr-scanner/privacy/) | [/apps/qr-scanner/terms/](https://legal.sharkscale.online/apps/qr-scanner/terms/) |

## Adding an app

1. Copy `apps/ai-pdf-scanner/terms/` to `apps/<new-slug>/terms/`
2. Rewrite it for that app's own plans — do not leave another app's wording in
   place, it is a statement about what a user is paying for
3. Check the shared `/privacy/` still describes what the new app does. If it
   handles data the policy does not mention, add a section; give the app its
   own `apps/<new-slug>/privacy/` only if much of the shared policy would be
   untrue for it
4. Add a card to `index.html` and a row to the table above
5. Push. Pages redeploys on its own

## Updating a policy

Edit the page, change the "Last updated" date, push. The URL never changes,
so nothing has to be updated in the Play Console.

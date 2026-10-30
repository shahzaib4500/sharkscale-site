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
privacy/index.html                    → /privacy/  (all apps)
apps/<app-slug>/terms/index.html      → /apps/<app-slug>/terms/
```

The privacy policy is **company-wide** — it says so itself: "applies to use
all application on all platforms" — so it lives at one URL that every listing
points at. Subscription terms name a specific app and its plans, so those are
per app.

## Live URLs

| App | Package | Privacy | Terms |
| --- | --- | --- | --- |
| AI PDF Scanner - Document Scanner | `com.pdfreadermobileapp` | [/privacy/](https://legal.sharkscale.online/privacy/) | [/apps/ai-pdf-scanner/terms/](https://legal.sharkscale.online/apps/ai-pdf-scanner/terms/) |
| Language Translator: Documents | `com.sharkstack.aitranslator` | [/privacy/](https://legal.sharkscale.online/privacy/) | [/apps/ai-translator/terms/](https://legal.sharkscale.online/apps/ai-translator/terms/) |

## Adding an app

1. Copy `apps/ai-pdf-scanner/terms/` to `apps/<new-slug>/terms/`
2. Rewrite it for that app's own plans — do not leave another app's wording in
   place, it is a statement about what a user is paying for
3. Check the shared `/privacy/` still describes what the new app does. If it
   handles data the policy does not mention, the policy needs a section, not
   the app a different URL
4. Add a card to `index.html` and a row to the table above
5. Push. Pages redeploys on its own

## Updating a policy

Edit the page, change the "Last updated" date, push. The URL never changes,
so nothing has to be updated in the Play Console.

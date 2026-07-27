# sharkscale-site

Static site behind **https://sharkscale.online** — the landing page plus the
privacy policy and terms of service for every app we publish.

Hosted on GitHub Pages from `main`. No build step: plain HTML and one
stylesheet, so a policy correction is an edit and a push.

## Layout

```
index.html                              landing page, lists every app
styles.css                              shared styles
CNAME                                   custom domain for GitHub Pages
apps/<app-slug>/privacy/index.html      → /apps/<app-slug>/privacy/
apps/<app-slug>/terms/index.html        → /apps/<app-slug>/terms/
```

Documents are **per app**, not shared. Play's Data Safety declaration is per
app and the apps genuinely differ — one may send document text to an AI
provider where another does not — so a single shared policy would have to
describe the union of everything, which is wrong for each app individually.

## Live URLs

| App | Package | Privacy | Terms |
| --- | --- | --- | --- |
| AI PDF Scanner - Document Scanner | `com.pdfreadermobileapp` | [/apps/ai-pdf-scanner/privacy/](https://sharkscale.online/apps/ai-pdf-scanner/privacy/) | [/apps/ai-pdf-scanner/terms/](https://sharkscale.online/apps/ai-pdf-scanner/terms/) |

## Adding an app

1. Copy `apps/ai-pdf-scanner/` to `apps/<new-slug>/`
2. Rewrite both pages for what that app actually does — do not leave another
   app's wording in place, it is a statement about data handling
3. Add a card to `index.html` and a row to the table above
4. Push. Pages redeploys on its own

## Updating a policy

Edit the page, change the "Last updated" date, push. The URL never changes,
so nothing has to be updated in the Play Console.

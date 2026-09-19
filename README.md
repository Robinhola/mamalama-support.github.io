# MamaLama support site

Static support and legal pages for the MamaLama iPhone app. Plain HTML and CSS,
no build step, no dependencies.

```
index.html        support, FAQ, screenshots
privacy/          privacy policy      → served at /privacy
terms/            terms of use        → served at /terms
privacy.html      redirect stub to /privacy/  (for links already handed out)
terms.html        redirect stub to /terms/
style.css
assets/           app icon and App Store screenshots
.nojekyll         tells GitHub Pages to serve the files as-is
```

## The URL

The legal pages are directories with an `index.html` inside, so GitHub Pages
serves them at `/privacy` and `/terms` with no `.html` — that part is done.

What the domain in front of them is depends on the repo name:

| Repo name | Site URL | Policy URL |
|---|---|---|
| `mamalama-support.github.io` (today) | `https://robinhola.github.io/mamalama-support.github.io/` | `…/mamalama-support.github.io/privacy` |
| `robinhola.github.io` | `https://robinhola.github.io/` | `https://robinhola.github.io/privacy` |
| `mamalama` | `https://robinhola.github.io/mamalama/` | `https://robinhola.github.io/mamalama/privacy` |

**A repo whose name merely ends in `.github.io` gets no special treatment.**
Only a repo named exactly `<username>.github.io` is served at the domain root.
Rename the repo (Settings → General → Repository name) to whichever row you
want; GitHub redirects the old name, and `git remote set-url origin` updates
this clone.

A custom domain (`mamalama.app`, say) gives `https://mamalama.app/privacy`: add
a `CNAME` file containing the bare domain, point the DNS at GitHub, and set it
under Settings → Pages.

## Publishing

1. Push to the repo root.
2. Repo → **Settings** → **Pages** → Source: **Deploy from a branch**,
   branch `main`, folder `/ (root)`.
3. Pages on a private repo needs a paid plan. Make the repo public, or use any
   other static host.

## Then

- App Store Connect → **Support URL**: the site root.
- App Store Connect → **App Privacy → Privacy Policy URL**: `<site>/privacy`.
- Set `AppInfo.privacyPolicyURL` (and optionally `AppInfo.termsURL`) in the app
  to the same URLs so the in-app links appear.

## Keeping it in step with the app

`privacy/index.html` and `terms/index.html` started as copies of
`docs/privacy-policy.md` and `docs/terms-of-use.md` in the app repo, and
`ContentRulesView.swift` is the in-app copy of the rules. The privacy policy has
since been rewritten for UK GDPR and is now the authoritative version — if you
keep the Markdown, bring it into line. Neither document has been reviewed by a
lawyer.

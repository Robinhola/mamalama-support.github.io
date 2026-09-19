# MamaLama support site

Static support and legal pages for the MamaLama iPhone app. Plain HTML and CSS,
no build step, no dependencies.

```
index.html     support, FAQ, screenshots
privacy.html   privacy policy
terms.html     terms of use
style.css
assets/        app icon and App Store screenshots
.nojekyll      tells GitHub Pages to serve the files as-is
```

## Publishing on GitHub Pages

1. Create a repo, push this folder to it as the repo root.
2. Repo → **Settings** → **Pages** → Source: **Deploy from a branch**,
   branch `main`, folder `/ (root)`.
3. The site appears at `https://<user>.github.io/<repo>/`.

Pages on a private repo needs a paid plan; make the repo public, or use any
other static host.

## Then

- App Store Connect → Support URL: the site root.
- App Store Connect → App Privacy → Privacy Policy URL: `.../privacy.html`.
- Set `AppInfo.privacyPolicyURL` (and optionally `AppInfo.termsURL`) in the app
  to the same URLs so the in-app links appear.

## Keeping it in step with the app

`privacy.html` and `terms.html` are copies of `docs/privacy-policy.md` and
`docs/terms-of-use.md` in the app repo, and `ContentRulesView.swift` is the
in-app copy of the rules. All of them have to agree — if you edit one, edit the
others. Neither document has been reviewed by a lawyer.

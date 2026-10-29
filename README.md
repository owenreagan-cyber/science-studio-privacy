# Science Studio — public website

This repository contains the public homepage and privacy policy for the **Science Studio
Google Drive and Google Slides integration**.

It is a separate, static website repository. It does not contain the Science Studio
application, curriculum files, publisher code, credentials, or student information.

## Live site

- Homepage: https://owenreagan-cyber.github.io/science-studio-privacy/
- Privacy policy: https://owenreagan-cyber.github.io/science-studio-privacy/privacy.html

GitHub Pages serves the `main` branch from the repository root.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Public homepage |
| `privacy.html` | Privacy policy |
| `styles.css` | Shared, dependency-free styling |
| `favicon.svg` | Site icon |
| `.nojekyll` | Tells GitHub Pages to publish files without Jekyll processing |
| `README.md` | This maintenance guide |

There is no build step, package manager, framework, or external font/script dependency.

## Local preview

From this directory:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000/` in a browser. Stop the server with `Ctrl+C`.
Do not leave a preview server running after the review.

## Updating the site

1. Edit the HTML or CSS directly.
2. Preview locally and check both pages at desktop and mobile widths.
3. Re-read the privacy policy against the actual integration behavior before publishing.
4. Commit and push to `main`.
5. GitHub Pages will rebuild automatically. Check the Pages deployment status in the
   repository settings or with the GitHub CLI.

```sh
git add index.html privacy.html styles.css favicon.svg README.md .nojekyll
git commit -m "Update public site"
git push origin main
```

## Privacy accuracy rules

The privacy policy must describe what the integration actually does. Before changing it:

- Confirm the OAuth scopes in the integration source and documentation.
- Confirm what is written to Google Drive, what is read from Google Slides, and what is
  stored locally.
- Confirm whether any retention or deletion mechanism exists. Do not claim automatic
  deletion or a retention period unless it is implemented.
- Confirm whether Google user data is sent anywhere other than Google APIs.
- Do not claim Google verification, certification, or endorsement that has not occurred.

If a material claim cannot be verified, do not publish it. Report the gap instead.

## Google OAuth and domain verification

This repository is only the public website. It does not configure Google OAuth, change
OAuth scopes, or trigger reauthorization.

If Google requires domain verification for the OAuth consent screen:

1. Add a **URL-prefix** property for the site in Google Search Console.
2. Verify ownership using the HTML meta tag or HTML file method.
3. Add the verified host as an authorized domain in the Google Cloud OAuth consent screen.
4. Record the result. Do not describe verification as complete until Google confirms it.

## Security review before publishing

Run these checks before any public push:

```sh
git status
git ls-files
grep -RInE --exclude-dir=.git --exclude=README.md '(client_secret|refresh_token|access_token|ya29\.|AIza|BEGIN (RSA |EC |OPENSSH )?PRIVATE KEY|/Users/|@[A-Za-z0-9.-]+\.(org|com|edu))' .
```

Expected result: only intentional website text. No credentials, tokens, email addresses,
school names, local file paths, student records, or private project code.

Also confirm that no existing Science Studio or Animation Studio files were copied into
this repository. This site is maintained independently.

## Contact

Use the public issue tracker:

https://github.com/owenreagan-cyber/science-studio-privacy/issues

Do not post student information, school records, personal contact details, credentials, or
OAuth tokens in a public issue.

# Deploy Agent

## Role
Push the completed listing site to GitHub Pages and update the portfolio index.
Only runs after QA Agent outputs PASS.

## Pre-deploy check
Confirm output/{{LISTING_SLUG}}/index.html exists and was last modified today.
Confirm QA Agent has output PASS in this session.

## Deploy steps

### 1. Initialize git if needed
Check if .git exists in the project root.
If not: run → git init && git branch -M main

### 2. Add GitHub remote if needed
Check if remote "origin" exists.
If not: run → git remote add origin https://github.com/{{GITHUB_USERNAME}}/{{GITHUB_REPO}}.git

### 3. Stage and commit
git add output/{{LISTING_SLUG}}/ portfolio/index.html
git commit -m "Add listing: {{ADDRESS_SHORT}} ({{LISTING_SLUG}})"

### 4. Push to GitHub
git push -u origin main

### 5. Confirm GitHub Pages is enabled
Remind the user: Go to GitHub repo Settings → Pages → set source to
"Deploy from branch: main / root" if this is the first deploy.

### 6. Update portfolio index
Read portfolio/index.html.
Add a new listing card for this property with:
- Property address
- Price
- Beds / baths / sqft
- Link to output/{{LISTING_SLUG}}/index.html
- Thumbnail using photos/hero.jpg

### 7. Report live URL
Output the expected live URL:
https://{{GITHUB_USERNAME}}.github.io/{{GITHUB_REPO}}/output/{{LISTING_SLUG}}/

## Output
Output exactly → PASS
Then output the live URL.

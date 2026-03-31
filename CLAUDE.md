# Listing Site Builder — Claude Code Master Config

## Project purpose
This system builds branded real estate listing websites for The Agency Team Hawai'i.
Drop in a filled intake.md + photos folder and the agents build a complete,
deployed listing site automatically.

## Brand standards — never deviate
- Primary font: Playfair Display (headings, prices, addresses)
- Secondary font: Montserrat (body, labels, navigation)
- Background: #F7F3EE (sand) and #FFFFFF (white, alternating sections)
- Accent: #C9A96E (gold)
- Text primary: #2A1F14 (espresso)
- Text muted: #8A7A6A
- Footer background: #2A1F14 (espresso)
- Border color: #E5DDD0
- Button style: espresso background, white text, uppercase, letter-spacing 3px
- No black (#000000 or #1A1A1A) anywhere in the design

## Folder structure
- intake/intake.md → agent reads this for all listing data
- intake/photos/ → all listing photos go here
- intake/docs/ → all buyer documents (PDF) go here
- template/template.html → locked master HTML template, never modify directly
- agents/ → one .md file per agent defining its role and rules
- output/ → built listing sites go here, one subfolder per listing
- portfolio/index.html → master portfolio page, updated after every build

## Agent pipeline — always run in this order
1. Intake Agent → validates intake.md and all assets are present
2. Copy Agent → writes all site text from intake data
3. Asset Agent → processes and names all photos
4. Build Agent → assembles the site from template + copy + assets
5. QA Agent → checks the site against the quality checklist
6. Deploy Agent → pushes to GitHub Pages

## Hard rules
- No agent starts until the previous agent has explicitly output "PASS"
- If any agent outputs "HALT", stop the entire pipeline and report what is missing
- The Build Agent NEVER generates its own design — it only fills the locked template
- All listing sites output to output/[slug]/ where slug = address-kebab-case
- Portfolio index is always updated after a successful deploy
- Formspree is used for all contact forms (ID comes from intake.md)
- GitHub Pages is the deploy target

## Intake requirements — pipeline halts if any of these are missing
1. Property address (full)
2. Asking price
3. Beds / baths / sqft / lot sqft
4. At least 6 photos in intake/photos/
5. Open house dates (or "none")
6. Virtual tour URL (or "none")
7. Neighborhood highlights (min 3 bullet points)
8. Agent bio
9. Formspree form ID
10. At least 1 document in intake/docs/

## Output quality checklist (QA Agent runs this before every deploy)
- [ ] Hero photo loads and covers full width
- [ ] Address and price match intake.md exactly
- [ ] All gallery photos load without broken links
- [ ] Property details (beds/baths/sqft) are correct
- [ ] Neighborhood section has all 3 highlights
- [ ] Open house section shows correct dates or is hidden if "none"
- [ ] Virtual tour button links correctly or is hidden if "none"
- [ ] All documents in intake/docs/ appear as download cards
- [ ] Mortgage calculator computes correctly
- [ ] Contact form action points to correct Formspree ID
- [ ] Site renders correctly at 375px width (mobile)
- [ ] No placeholder text remaining (no "Lorem ipsum", "Photo", "TBD")
- [ ] Footer shows correct agent name and license number

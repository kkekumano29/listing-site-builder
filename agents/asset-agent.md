# Asset Agent

## Role
Process, validate, and organize all photos and documents in the intake folders.
Ensure every asset is correctly named and ready for the Build Agent.

## Photo tasks

### 1. Inventory
List all files in intake/photos/. Confirm at least 6 images exist.

### 2. Hero photo
The first photo alphabetically (or named hero.jpg if it exists) becomes the hero.
Rename it to hero.jpg if not already named that.

### 3. Gallery photos
Rename remaining photos sequentially: photo-01.jpg, photo-02.jpg, etc.
Preserve original file extensions (.jpg, .jpeg, .png, .webp).

### 4. Agent photo
If a file named agent.jpg exists in intake/photos/, keep it as-is.
If not, note "MISSING: agent.jpg — hero section will show placeholder" but do not HALT.

### 5. Size check
Warn (do not HALT) if any photo is smaller than 800px wide.
Warn if hero.jpg is smaller than 1400px wide.

## Document tasks

### 1. Inventory
List all files in intake/docs/. Cross-reference against DOCUMENTS list in intake.md.

### 2. Verify all listed docs exist
If any listed document file is missing from intake/docs/, output HALT.

### 3. Copy assets to output folder
Copy intake/photos/ → output/{{LISTING_SLUG}}/photos/
Copy intake/docs/ → output/{{LISTING_SLUG}}/docs/

## Output
If all required assets are present and copied: output exactly → PASS
If any required asset is missing: output exactly → HALT: [list missing files]

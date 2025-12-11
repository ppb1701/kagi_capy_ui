# Changelog

## [1.0.8] - 2025-12-11

### Fixed
- **Mobile icon grouping** - Fixed X, capy logo, and magnifier icons spreading across search bar on mobile; now tightly grouped on right side matching desktop layout
- **Mobile text length** - Improved visible text area in search input by reducing container padding from 90px to 25px
- **Mobile icon positioning** - Forced `.search-form-icons` container to `display: block` to prevent flexbox from distributing buttons
- **Fix Editing search text and Kagi Logo stacking on focus** - Added rules to hide Kagi logo when editing search on mobile to prevent text overlap

### Changed
- Mobile icon positions: Clear button at `82px`, Capy at `52px` (matching desktop), Search button at `8px`
- Search container padding reduced to `25px` while input padding set to `80px` for optimal text display
- All mobile search contexts now use consistent icon positioning (home page, results, and edit)

### Technical Details
- Consolidated mobile icon positioning into single media query section
- Added `.search-form-icons` display override to prevent flex distribution
- Applied `body:has(input:focus)` selectors to hide Kagi branding on mobile when focused
- Removed duplicate/conflicting search results page positioning rules

## [1.0.7] - 2025-12-08

### Fixed
- **Assistant page text alignment** - Fixed text being centered/moved to the right in assistant chat after Kagi selector changes
- **Assistant page isolation** - Excluded assistant pages from all global container width rules that were causing layout issues
- **Mobile icon alignment on search results** - Fixed capy logo, clear button, and magnifier stacking on mobile search results page
- **Desktop magnifier icon size** - Fixed search/magnifier button icon being crushed to pixel size on desktop

### Changed
- Mobile icon positioning: Clear button at `right: 72px`, Capy at `right: 42px`, Search button at `right: 8px`
- Desktop button SVG icons now explicitly sized at 20x20px
- Input padding adjusted to `80px` on mobile to accommodate icon group

### Technical Details
- Added `html:not([data-path*="assistant"])` prefix to global container rules (lines 74-100, 134-145)
- Scoped `.center-content-box`, `div[class*="container"]`, and width rules to exclude assistant pages
- Added search results page specific button positioning with `body:has(._0_SRI.search-result)` selectors
- Removed generic SVG size restrictions from button icons
- Consolidated mobile icon positioning in @media query at line 577

## [1.0.6] - 2025-12-05

### Fixed
- **Kagi CSS class name changes** - Updated all selectors to work with Kagi's new class structure (removed dot prefix from `_0_` classes)
- **Assistant page isolation** - Completely removed theme styling from assistant pages to prevent interference
- **Search page targeting** - Implemented `:has()` selectors to only apply theming to search pages
- **Mobile search results** - Fixed unthemed search results on mobile by adding fallback selectors (`body:has(#searchForm)`, `body:has(._0_SRI.search-result)`)
- **Search input text truncation** - Reduced padding from 125px to 90px on desktop and 110px to 75px on mobile to prevent text cutoff
- **Placeholder text cutoff** - Moved capy logo from 100px to 52px on desktop to accommodate search text

### Changed
- Theme now uses multiple `:has()` selectors to reliably target search pages
- Desktop search input padding: 125px → 90px
- Mobile search input padding: 110px → 75px  
- Capy logo position: 100px → 52px (desktop), stays at 92px (mobile)
- All assistant-specific styling removed to avoid conflicts
- Navigation and tab styling scoped to search pages only

### Technical Details
- Updated selectors from `._0_` to `_0_` pattern for new Kagi class structure
- Added `a._0_query_link_item` for navigation links
- Removed all `body:not([class*="assistant"])` selectors in favor of positive `:has()` targeting
- Added multiple fallback `:has()` selectors: `.search-form-wrapper`, `#searchForm`, `._0_SRI.search-result`
- Fixed mobile button positioning with proper `body:has()` scoping

## [1.0.5] - 2025-12-05

### Fixed
- **Assistant page alignment on desktop** - Fixed text box being pushed to the right and text getting cut off
- **Flexbox centering conflicts** - Prevented search bar centering from affecting assistant page layout

### Technical Details
- Added `[data-page*="assistant"]` selector to exclusion list for centering
- Explicitly set assistant containers to `display: block` and `justify-content: flex-start`
- Assistant page now maintains proper left alignment without text cutoff

## [1.0.4] - 2025-12-05

### Fixed
- **Mobile search bar layout** - Fixed button positioning with proper spacing for capy logo, clear button, and search button
- **Mobile button stacking** - Resolved overlapping buttons by adjusting positions: capy logo at 92px, clear button at 50px, search button at 8px
- **Mobile search input padding** - Increased padding to 130px to accommodate all icons without text overlap

### Changed
- Capy logo size reduced to 24px on mobile for better spacing
- Clear button now positioned between capy logo and search button
- Mobile search container padding optimized for icon layout

### Technical Details
- Adjusted icon positioning: capy logo `right: 92px`, clear button `right: 50px`, search button `right: 8px`
- Increased mobile padding from 110px to 130px to prevent icon overlap
- All buttons now use absolute positioning with proper transforms for vertical centering

## [1.0.3] - 2025-12-04

### Fixed
- **Assistant send button on mobile** - Fixed send button being pushed off screen and made it stay inside the text input box where it belongs
- **Button positioning conflicts** - Prevented search page button positioning from affecting assistant page buttons

### Technical Details
- Removed generic `button[type="submit"]` positioning that was breaking assistant layout
- Made button positioning specific to `button#searchFormSubmitBtn` only
- Added overflow prevention for assistant containers on mobile
- Assistant send button now maintains its default position inside the input field

## [1.0.2] - 2025-12-02

### Fixed
- **Assistant page layout** - Fixed chat alignment being pushed to the right by making search bar centering specific to non-assistant pages only

### Technical Details
- Modified flexbox centering selectors to exclude assistant pages using `body:not([class*="assistant"])` selector
- Assistant chat now properly aligns to the left side as intended

## [1.0.1] - 2025-12-01

### Fixed
- **Ultrawide screen support** - Removed max-width constraints on result containers to properly fill ultrawide displays
- **Video thumbnail aspect ratios** - Preserved 16:9 aspect ratio for video thumbnails while excluding YouTube and channel logos
- **Search bar centering** - Added flexbox centering to search form wrapper for proper alignment on home page

### Changed
- Result containers now expand to full width on ultrawide screens
- Video thumbnails maintain proper 16:9 aspect ratio
- YouTube logos, channel icons, and source images excluded from aspect ratio constraints
- Search bar properly centered on home page

### Technical Details
- Added `max-width: none !important` and `width: 100% !important` to result containers
- Implemented aspect-ratio preservation for video thumbnails with logo exclusions
- Added flexbox centering to `.search-form-wrapper`, `.search_form_box`, and `.center-content-box`


## [1.0.0] - 2025-12-01

### Fixed
- **Capy logo positioning** - Moved from outside the search bar (`right: -48px`) to inside (`right: 52px` on desktop, `right: 42px` on mobile)
- **Search input padding** - Added `padding-right: 90px` on desktop and `75px` on mobile to prevent text from being cut off by icons
- **Icon overlap** - Increased z-index of capy logo to `10` to ensure proper layering
- **Mobile magnifier icon** - Adjusted position and spacing to prevent overlap with search text
- **Search button positioning** - Fixed button margins to ensure it stays properly positioned within the search container

### Changed
- Capy logo size reduced slightly from 36px to 32px on desktop for better proportions
- Mobile capy logo size adjusted to 26px (from 24px) for better visibility
- Search container padding optimized for both mobile and desktop viewports

### Technical Details
**Desktop changes:**
- `.search-input-container::after` - Changed `right: -48px` → `right: 52px`
- `.search-input-container::after` - Changed `width: 36px` → `width: 32px`
- `.search-input-container` - Added `padding-right: 90px`
- `input#searchBar` - Added `padding-right: 90px`

**Mobile changes (@media max-width: 800px):**
- `.search-input-container::after` - Changed `right: 30px` → `right: 42px`
- `.search-input-container::after` - Changed `width: 24px` → `width: 26px`
- `.search-input-container` - Changed `padding-right: 60px` → `padding-right: 75px`
- `button#searchFormSubmitBtn` - Changed `margin-right: 18px` → `margin-right: 8px`
- Added explicit padding for search input on mobile

### Notes
- The gradient background feature is unique to this Kagi port and may be added to the Mastodon version in the future
- All positioning values have been carefully tested to work with Kagi's search interface

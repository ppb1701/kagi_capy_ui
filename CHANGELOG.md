# Changelog

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

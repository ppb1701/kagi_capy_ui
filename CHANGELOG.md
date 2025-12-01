# Changelog

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

# Day 2 Test Plan

## Overview
- Focus: login flows, form validation, and Amazon web app UI/functional coverage.
- Primary environments referenced: Chrome 114 on macOS/Windows 10, Firefox 112 on Windows 10, Brave 112 on macOS.
- Deliverables: structured bug reports, 20 login test cases (positive/negative/boundary), 20 Amazon UI cases, 10 Amazon functional cases, and Amazon bug findings.

## Table of Contents
- [Bug Reports](#bug-reports)
  - [Signup / Generic](#signup--generic)
  - [Login Bugs](#login-bugs)
  - [Amazon Bugs](#amazon-bugs)
- [Login Test Cases (20)](#login-test-cases-20)
  - [Positive](#positive)
  - [Negative](#negative)
  - [Boundary](#boundary)
- [Amazon Web App Test Suite](#amazon-web-app-test-suite)
  - [UI Test Cases (20)](#ui-test-cases-20)
  - [Functional Test Cases (10)](#functional-test-cases-10)
  - [Amazon Bug Reports](#amazon-bug-reports)
- [Reference Tasks](#reference-tasks)

---

## Bug Reports

### Signup / Generic
| ID | Title | Environment | Severity | Priority | Type | Steps | Expected | Actual |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| BR-001 | No confirmation link after sign up | Chrome 114.0.5735.199 on macOS | High | Urgent | Functional | 1) Go to sign-up page.<br>2) Fill the sign-up form.<br>3) Click the sign-up button.<br>4) Check inbox for confirmation link. | Confirmation email is sent or an error appears when email cannot be sent. | No email received and no error shown. |
| BR-002 | Text box does not scroll when content exceeds box | Brave 112.0 on macOS | Medium | Normal | UI | 1) Go to the text box page.<br>2) Add content until it exceeds the box size.<br>3) Attempt to scroll inside the text box. | Text box scrolls while page remains stable. | Whole page scrolls; text box does not. |
| BR-003 | Empty form submission shows no errors | Firefox 112.0 on Windows 10 | High | Urgent | Validation | 1) Go to the form page.<br>2) Leave all fields blank.<br>3) Click submit. | Required-field errors appear for each empty field. | No response or validation feedback is shown. |

### Login Bugs
| ID | Title | Environment | Severity | Priority | Type | Steps | Expected | Actual |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| BR-004 | No "incorrect password" error displayed | Chrome 114.0.5735.199 on Windows 10 | High | Urgent | Functional | Enter valid email, wrong password; click Login. | Error message indicates incorrect password. | No error; page stays static. |
| BR-005 | Login button stays disabled with valid inputs | Chrome on Linux | High | Urgent | UI | Enter valid credentials on login form. | Login button enables when inputs are valid. | Button remains disabled. |
| BR-006 | Password field not masked | Chrome 114.0.5735.199 on macOS | High | Urgent | UI | Enter password in the field. | Characters are masked (e.g., dots/asterisks). | Plain text is shown. |
| BR-007 | "Remember Me" checkbox does not save session | Firefox 112.0 on Windows 10 | Medium | Normal | Functional | Check "Remember Me", login, close/reopen browser. | User stays logged in after reopening. | User is logged out. |
| BR-008 | Double submission when clicking Login twice | Brave 112.0 on macOS | High | Urgent | Functional | Enter valid credentials and click Login twice quickly. | Form submits once; single login attempt. | Form submits twice causing duplicate attempts/errors. |

### Amazon Bugs
| ID | Title | Environment | Severity | Priority | Type | Steps | Expected | Actual |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| BR-009 | Footer sections not clearly visible on small screens | Chrome 114 on desktop resized to 490x750 | Normal | Low | Functional | Open Amazon homepage; resize to 490x750; scroll to footer. | Footer sections are visible and aligned. | Footer sections overlap and are unclear. |
| BR-010 | Thumbnail images not loading in search results | Firefox 112.0 on Windows 10 | High | Urgent | Functional | Search for a product (e.g., "laptop"); scroll results. | All thumbnails load correctly. | Some thumbnails are broken/missing. |
| BR-011 | Product titles overlap on search results page | Brave 112.0 on macOS | Medium | Normal | UI | Search for long-title product (e.g., "wireless noise cancelling headphones"). | Titles are fully visible without overlap. | Titles overlap or are cut off. |
| BR-012 | Delayed hover dropdown for "Account & Lists" | Chrome 114.0.5735.199 on Windows 10 | Low | Normal | UI | Hover over "Account & Lists" in header. | Dropdown appears immediately. | Noticeable delay before dropdown appears. |
| BR-013 | Search suggestions cover search button | Chrome 114.0.5735.199 on macOS | Medium | Normal | UI | Type at least 3 chars in search bar. | Suggestions appear without covering search button. | Suggestions overlap/cover search button. |

---

## Login Test Cases (20)

### Positive
| ID | Title | Module | Preconditions | Steps | Expected | Priority | Type | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC_001 | Login with valid email + password | Login | Registered user on login page | Enter valid email and password; submit. | Login succeeds and user reaches dashboard. | High | Functional | Pass |
| TC_002 | Login with valid phone number + password | Login | Registered phone number on login page | Enter registered phone number and password; submit. | Login succeeds and redirects to dashboard. | High | Functional | Pass |
| TC_003 | Login using Enter key | Login | Registered user on login page | Enter valid credentials; press Enter instead of clicking Login. | Login succeeds and user reaches dashboard. | High | Functional | Pass |
| TC_004 | Login after resetting password | Login | Password recently reset; on login page | Enter email and new password; submit. | Login succeeds and user reaches dashboard. | High | Functional | Pass |
| TC_005 | Login with "Remember Me" checked | Login | Valid credentials; on login page | Enter credentials; check "Remember Me"; submit. | Session persists after closing/reopening browser. | Medium | Functional | Pass |
| TC_006 | Login with 2FA enabled | Login | 2FA enabled; on login page | Enter credentials; submit; enter 2FA code; verify. | Login succeeds and user reaches dashboard. | High | Functional | Pass |
| TC_007 | Login using Google | Login | Google account available; on login page | Click "Login with Google"; select account. | Login succeeds and user reaches dashboard. | Medium | Functional | Pass |
| TC_008 | Login using Apple ID | Login | Apple ID available; on login page | Click "Login with Apple ID"; sign in. | Login succeeds and user reaches dashboard. | Medium | Functional | Pass |

### Negative
| ID | Title | Module | Preconditions | Steps | Expected | Priority | Type | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC_009 | Invalid email format | Login | On login page | Enter invalid email format; enter valid password; submit. | Error message for invalid email format. | High | Functional | Pass |
| TC_010 | Incorrect password | Login | Registered email; on login page | Enter valid email and incorrect password; submit. | Error message for incorrect password. | High | Functional | Pass |
| TC_011 | Unregistered email | Login | On login page | Enter unregistered email; enter valid password; submit. | Error indicating email not registered. | High | Functional | Pass |
| TC_012 | Empty fields | Login | On login page | Leave email/password blank; submit. | Required-field errors shown. | High | Functional | Pass |
| TC_013 | Password shorter than minimum | Login | On login page | Enter valid email; enter too-short password; submit. | Error indicating password too short. | Medium | Functional | Pass |
| TC_014 | Password longer than maximum | Login | On login page | Enter valid email; enter too-long password; submit. | Error indicating password too long with guidance. | Medium | Functional | Pass |
| TC_015 | SQL injection attempt | Login | On login page | Enter "' OR 1=1 --" in email; any password; submit. | Login blocked; error for invalid credentials. | High | Security | Pass |
| TC_016 | Special characters in email | Login | On login page | Enter email with unsupported special chars; valid password; submit. | Error for invalid email format. | Medium | Functional | Pass |
| TC_017 | Leading/trailing spaces in email | Login | On login page | Enter email with spaces around it; enter valid password; submit. | Error for invalid email format. | High | Functional | Pass |
| TC_018 | Expired password | Login | Password marked expired; on login page | Enter valid email; enter expired password; submit. | Error prompting password reset. | High | Functional | Pass |

### Boundary
| ID | Title | Module | Preconditions | Steps | Expected | Priority | Type | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TC_019 | Email max length (254 chars) | Login | On login page | Enter 254-char email; enter valid password; submit. | Login succeeds if email is valid; handled without truncation errors. | Medium | Functional | Pass |
| TC_020 | Password min/max length boundary | Login | On login page | Enter valid email; test password at min length; submit; repeat with max length. | Login succeeds with both boundary-length passwords. | Medium | Functional | Pass |

---

## Amazon Web App Test Suite
Target site: https://www.amazon.com/

### UI Test Cases (20)
| ID | Title | Module | Preconditions | Steps | Expected | Priority | Type |
| --- | --- | --- | --- | --- | --- | --- | --- |
| UI_01 | Verify Amazon logo visibility and alignment | Homepage | Desktop homepage loaded | View header logo; resize browser. | Logo remains visible, uncropped, and aligned across widths. | Medium | UI |
| UI_02 | Verify search bar size, alignment, and placeholder | Homepage | Homepage loaded | Inspect search bar placement and placeholder; resize window. | Search bar centered with correct placeholder across viewports. | High | UI |
| UI_03 | Verify navigation bar alignment and hover states | Homepage | Desktop homepage loaded | Observe nav items; hover each item. | Items evenly aligned; hover states visible without layout shift. | Medium | UI |
| UI_04 | Verify "Account & Lists" hover dropdown UI | Header | Logged out on desktop | Hover over "Account & Lists"; observe dropdown. | Dropdown aligned, readable, and appears quickly. | High | UI |
| UI_05 | Verify color contrast of header text | Header | Homepage loaded | Review header text vs background. | Text has sufficient contrast and remains readable. | Medium | UI/Accessibility |
| UI_06 | Verify product cards alignment on homepage | Homepage | Recommendation sections loaded | Scroll product sections; review card alignment. | Cards align consistently within rows. | Medium | UI |
| UI_07 | Verify product images load correctly | Homepage | Homepage loaded | Scroll through product carousels. | No broken images; placeholders absent. | High | UI |
| UI_08 | Verify "Add to Cart" button UI on listing page | Product Listing | Search results displayed | Observe Add to Cart button styling/placement. | Button visible, aligned, and consistent across items. | High | UI |
| UI_09 | Verify footer links alignment | Footer | Homepage loaded | Scroll to footer; check link alignment. | Footer links align and are evenly spaced. | Medium | UI |
| UI_10 | Verify spacing around search results items | Search Results | Search performed | Inspect padding/margins between items. | Even spacing without overlap or crowding. | Medium | UI |
| UI_11 | Verify rating stars alignment under product names | Search Results | Search performed | Check rating stars alignment. | Stars align under product names without clipping. | Medium | UI |
| UI_12 | Verify deals banner image quality and scaling | Homepage | Deals banner visible | Observe banner at default and resized widths. | Banner is crisp, properly scaled, not pixelated. | Medium | UI |
| UI_13 | Verify mobile responsiveness of homepage | Homepage | DevTools mobile viewport | Switch to mobile widths; review layout. | Layout adapts without clipped/overlapping elements. | High | UI |
| UI_14 | Verify search results grid layout on mobile view | Search Results | Search performed in mobile viewport | Inspect results grid on mobile. | Grid stacks properly with no cut-off text/images. | High | UI |
| UI_15 | Verify product description text formatting | Product Page | Product page loaded | Scroll to description section. | Description text uses consistent fonts, sizes, and spacing. | Medium | UI |
| UI_16 | Verify size/color selection UI on product page | Product Page | Product with multiple options open | Click different size/color options. | Options clearly visible and show selected state. | High | UI |
| UI_17 | Verify cart icon updates visually when item is added | Header/Cart | On product/search page | Add product to cart; watch cart icon. | Cart badge/count updates immediately. | High | UI |
| UI_18 | Verify consistent font usage across homepage | Homepage | Homepage loaded | Compare fonts across sections. | Similar text types share consistent fonts/sizes. | Low | UI |
| UI_19 | Verify loading spinner visibility during navigation | Global | Standard connection | Navigate between pages; observe loading indicator. | Loading indicator appears during fetch and hides on completion. | Medium | UI |
| UI_20 | Verify error message UI when no search results | Search | Search with nonsense keyword | Observe empty-state message/layout. | Clear, well-styled message with no overlaps and suggested actions. | Medium | UI |

### Functional Test Cases (10)
| ID | Title | Module | Preconditions | Steps | Expected | Priority | Type |
| --- | --- | --- | --- | --- | --- | --- | --- |
| FN_01 | Verify user can search for a product | Search | Homepage available | Enter product name; submit search. | Navigates to results showing relevant products. | Critical | Functional |
| FN_02 | Verify autocomplete suggestions appear on typing | Search | JS enabled; homepage loaded | Type 3+ chars in search bar. | Relevant suggestions appear and update as typed. | High | Functional |
| FN_03 | Verify product page opens from search results | Search Results | Results displayed | Click product title/image. | Corresponding product detail page opens. | High | Functional |
| FN_04 | Verify user can add product to cart | Product Page/Cart | In-stock product page open | Select options; click "Add to Cart". | Item added; confirmation message/panel shown. | Critical | Functional |
| FN_05 | Verify user can remove product from cart | Cart | Cart has at least one item | Open cart; click remove/delete on an item. | Item removed; totals update correctly. | High | Functional |
| FN_06 | Verify quantity update works (1→2→3) | Cart | Cart contains item supporting quantity >1 | Change quantity from 1 to 2 to 3; observe totals. | Quantity updates and totals recalc without errors. | High | Functional |
| FN_07 | Verify filters update search results correctly | Search Results | Filters available with many results | Apply a filter (e.g., brand/price). | Results refresh to match active filters; filter chips reflect state. | High | Functional |
| FN_08 | Verify sorting by price (low-to-high) works | Search Results | Results contain varied prices | Choose "Price: Low to High" sorting. | Products sorted ascending by price. | Medium | Functional |
| FN_09 | Verify "Deliver to" location updates availability | Global | Deliver-to selector visible; no geo-blocking | Change deliver-to address/region. | Availability messaging updates per selected address. | Medium | Functional |
| FN_10 | Verify "Buy Now" redirects to sign-in when logged out | Product Page/Login | User logged out; product page open | Click "Buy Now". | Redirects to sign-in/auth flow; checkout resumes post-login. | Critical | Functional |

### Amazon Bug Reports
See [Amazon Bugs](#amazon-bugs) for the five documented findings.

---

## Reference Tasks
- Day 2 focus: Advanced test case writing, severity/priority, negative testing, 20 login cases, 5 professional bug reports.
- Day 3 focus: Web app testing on Amazon (UI/functional/responsive/validation), 20 UI test cases, 10 functional test cases, 5 bug reports, leverage Chrome DevTools for console/network/layout/device checks.

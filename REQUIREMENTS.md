# HKS Student Compass — World-Class Student Navigation Page
## Requirements, Style Guide & Build Spec

---

## 1. VISION

Build the **definitive HKS student landing page** — a single URL that replaces the scattered HKS Hub navigation. Students open it and find *everything* within 2 clicks, on any device, in under 3 seconds.

Design target: **90+/100 UX score** — better than Stanford's Axess, MIT's Stellar, and the existing HKS Hub.

---

## 2. CORE PRINCIPLES

1. **Search-first** — A mega search bar at the top filters all resources live as you type
2. **Need-based, not org-based** — Organized by what students need, not which department owns it
3. **3-click max rule** — Any resource reachable in ≤3 clicks from landing
4. **Mobile-first** — 100% usable on iPhone, perfectly responsive
5. **Zero login friction** — All links are direct; no redundant auth walls before the destination
6. **Visual scannability** — Icons + labels, never just text lists
7. **Harvard credibility** — Crisp, institutional, never "startup cute"

---

## 3. INFORMATION ARCHITECTURE

### Quick Action Bar (top, always visible — the "F-row")
Pinned row of 8 most-accessed resources (large icons):
1. Canvas (LMS)
2. JACK Career System
3. My.Harvard (registration)
4. Library / HOLLIS
5. HKS Email
6. IT Support
7. Student Health (HUHS)
8. Academic Calendar

### Category Cards Grid (main content)

#### A. Academics & Learning
- Canvas — courses, assignments, grades
- My.Harvard — registration, add/drop
- Course Catalog
- Degree Program Requirements
- Library & Research (HOLLIS)
- Academic Calendar & Deadlines
- Academic Advising Appointments
- Writing Center / Tutoring

#### B. Career & Jobs
- JACK Career Management System
- Career Development & Job Search Tools
- Job Boards & External Job Banks
- Internships & Post-Grad Fellowships
- Working as a TA at HKS
- Headshot Hub
- Career Events Calendar
- HKS in D.C. 2026
- State & Local Government Career Expo
- OCA Video Library
- OCA Contact & About

#### C. Finance & Aid
- Financial Aid Information
- Student Billing / Bursar
- Tuition & Fees Schedule
- Scholarship Resources
- Emergency Student Funds
- Tax Documents

#### D. Student Life & Wellbeing
- Health Services (HUHS)
- Counseling & Mental Health (CAMHS)
- Housing & Dining
- Student Organizations
- Recreation & Athletics (MAC)
- Child Care Resources
- International Student Support
- Disability Services

#### E. Technology & IT
- IT Help Desk
- Software & Licensing
- HarvardKey & MFA
- VPN & Remote Access
- Printing & Scanning
- Zoom & Video Conferencing
- HKS WiFi Setup
- Data Storage & Cloud

#### F. Campus & Community
- Events Calendar
- Student Government (HKS SGA)
- Diversity & Inclusion Resources
- Alumni Network
- Community Announcements
- Campus Map & Directions

#### G. Administrative & Services
- Student Services Office
- Registrar
- ID Cards & Access
- Parking & Transportation
- Forms & Documents Library
- Title IX & Support Resources
- Ombudsman

#### H. Help & Emergency
- **Emergency: 617-495-1330** (prominent, red)
- Campus Police: 617-495-1212
- Mental Health Crisis Line
- Student Support Navigator
- Report an Incident
- Feedback & Suggestions

---

## 4. PAGE STRUCTURE (HTML)

```
<header>          ← HKS logo | search bar | user greeting
<nav class="quick-bar">   ← 8 icon shortcuts
<main>
  <section.search-results>  ← live, hidden until search
  <section.grid>
    <div.category-card> × 8
      <h2> Category </h2>
      <ul> links </ul>
<aside.events-widget>  ← upcoming events/deadlines (sidebar or bottom)
<footer>          ← emergency | copyright | HKS branding
```

---

## 5. DESIGN SYSTEM

### 5.1 Color Palette

| Token | Hex | Usage |
|---|---|---|
| `--crimson` | `#A41034` | Primary brand, category headers, CTA |
| `--crimson-dark` | `#7A0C27` | Hover states on crimson elements |
| `--crimson-light` | `#F5E6EA` | Card header backgrounds |
| `--black` | `#1A1A1A` | Body text, headings |
| `--gray-700` | `#374151` | Secondary text |
| `--gray-500` | `#6B7280` | Metadata, timestamps |
| `--gray-200` | `#E5E7EB` | Borders, dividers |
| `--gray-50` | `#F9F9F9` | Page background |
| `--white` | `#FFFFFF` | Card backgrounds |
| `--link-blue` | `#1D4ED8` | Hyperlinks |
| `--link-hover` | `#1E40AF` | Link hover |
| `--emergency-red` | `#DC2626` | Emergency links |
| `--success` | `#15803D` | Success states |

### 5.2 Typography

**Google Fonts to load:**
- `Playfair Display` (serif) — headings, category titles
- `Inter` (sans-serif) — all body text, links, labels

| Element | Font | Size | Weight | Line-height |
|---|---|---|---|---|
| Page title | Playfair Display | 2rem | 700 | 1.2 |
| Category header | Playfair Display | 1.25rem | 600 | 1.3 |
| Body / links | Inter | 0.9375rem | 400 | 1.5 |
| Quick-bar labels | Inter | 0.75rem | 500 | 1.2 |
| Search input | Inter | 1.125rem | 400 | 1.5 |
| Badge / meta | Inter | 0.75rem | 500 | 1 |

### 5.3 Spacing Scale (rem)
`0.25 | 0.5 | 0.75 | 1 | 1.5 | 2 | 3 | 4 | 6 | 8`

### 5.4 Shadows
```css
--shadow-sm: 0 1px 3px rgba(0,0,0,0.08);
--shadow-md: 0 4px 12px rgba(0,0,0,0.10);
--shadow-lg: 0 8px 24px rgba(0,0,0,0.12);
```

### 5.5 Border Radius
```css
--radius-sm: 4px;
--radius-md: 8px;
--radius-lg: 12px;
--radius-pill: 9999px;
```

### 5.6 Transitions
```css
transition: all 0.18s ease;
```

---

## 6. COMPONENT SPECS

### 6.1 Header
- **Left**: HKS logo (text: "HKS • COMPASS" in Playfair Display)
- **Center**: Search bar — full width on mobile, 480px max on desktop
  - Placeholder: "Search resources, tools, links..."
  - Live filter: filters ALL links/categories on keyup
  - Clear (×) button when text present
  - Keyboard shortcut hint: `⌘K` or `Ctrl+K` to focus
- **Right**: "Harvard Kennedy School" subtitle text (desktop only)
- **Background**: White with bottom border in crimson (3px)
- **Sticky**: Always at top (position: sticky)

### 6.2 Quick Action Bar
- **8 large icon buttons** in a horizontal scroll row
- Each: icon (SVG or emoji fallback) + label
- **Active/hover**: crimson background, white text
- **Mobile**: horizontally scrollable, 2 rows on very small screens
- Background: crimson (#A41034), text: white
- This row should feel like the iOS dock

### 6.3 Category Cards
- **Grid**: 3 columns desktop (≥1024px), 2 columns tablet (≥640px), 1 column mobile
- **Card anatomy**:
  - Top: colored bar (crimson) + category icon + category name
  - Body: list of links (6-12 per card)
  - Each link: arrow (›) prefix, hover underline + slight left shift
  - Footer: "See all →" link if applicable
- **States**: default shadow-sm; hover shadow-md, slight translateY(-2px)
- Links: Inter 0.9375rem, color --link-blue, no underline by default, underline on hover

### 6.4 Live Search
- On input: all non-matching cards fade to 0.25 opacity; matching cards stay full opacity
- Matching links within cards highlight (crimson background on text match)
- If 0 results: show "No results for 'X' — try searching for something else"
- Search is case-insensitive, matches any substring
- Results appear instantly, no debounce needed for small dataset

### 6.5 Emergency Widget
- Fixed to bottom-right corner (like a chat widget)
- Red circle with ⚠️ or phone icon
- On click: expands to show emergency numbers
- Always visible

### 6.6 Events Sidebar / Widget (OPTIONAL — can be stubbed)
- Placeholder card: "Events & Deadlines — Check the HKS Events Calendar"
- Visual: calendar icon, upcoming event slots

### 6.7 Footer
- Dark background (#1A1A1A)
- 3 columns: Branding | Quick Links | Emergency Contacts
- Harvard shield icon (Unicode: ⚔ or use text fallback)
- Copyright: "© 2026 Harvard Kennedy School"
- "Built by OCA — Office of Career Advancement"

---

## 7. INTERACTION DESIGN

### Keyboard Navigation
- `Tab` through all cards and links
- `⌘K` / `Ctrl+K` focuses search bar
- `Escape` clears search and returns to default view
- All interactive elements have `:focus-visible` outline in crimson

### Mobile Experience
- Header collapses: logo + search only (no subtitle)
- Quick bar: 2-row grid OR horizontal scroll with snap
- Cards stack to single column
- Category headers are collapsible accordions on mobile
- Emergency widget: bottom-right floating button

### Animations
- Page load: cards fade in staggered (50ms delay per card)
- Search filter: opacity transition 0.2s
- Card hover: translateY + shadow transition
- Quick bar icons: slight scale(1.05) on hover

---

## 8. ACCESSIBILITY

- All images/icons have `alt` text
- Color contrast ratio ≥ 4.5:1 for all text (WCAG AA)
- Focus indicators visible and high-contrast
- Search results announced via `aria-live="polite"`
- Semantic HTML: `<header>`, `<nav>`, `<main>`, `<section>`, `<footer>`
- Category cards use `<ul>/<li>` for links
- Skip-to-content link at very top

---

## 9. PERFORMANCE

- Single HTML file with embedded CSS and JS (zero build tooling)
- Inline SVG icons (no external icon library request)
- Google Fonts loaded with `display=swap`
- No JavaScript frameworks — vanilla JS only
- Target: < 50KB total page weight (excluding fonts)
- No external API calls (all links are static)

---

## 10. FILE DELIVERABLE

**Single file**: `index.html`
- All CSS in `<style>` block in `<head>`
- All JS in `<script>` block before `</body>`
- Self-contained, opens directly in browser with no server needed
- Mobile-responsive with meta viewport tag

---

## 11. CONTENT — ACTUAL LINKS

Use `href="#"` as placeholder for all links — the goal is structure and UX, not live routing.
Add `data-label` attributes with the resource name for search functionality.

---

## 12. QUALITY BAR

Before delivering, self-check:
- [ ] Search filters all 50+ links correctly
- [ ] All 8 quick-action icons render with labels
- [ ] All 8 category cards display with proper link lists
- [ ] Mobile view: no horizontal scroll on body
- [ ] Mobile view: cards stack correctly
- [ ] Quick bar scrolls/wraps on mobile
- [ ] Emergency widget visible and functional
- [ ] Keyboard navigation works (Tab, Escape, Ctrl+K)
- [ ] Card hover animations feel smooth
- [ ] Typography hierarchy is clear and beautiful
- [ ] No console errors
- [ ] Harvard Crimson (#A41034) used consistently
- [ ] Feels like it belongs to Harvard — institutional, clean, trustworthy

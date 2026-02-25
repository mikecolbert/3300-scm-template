# Working Notes — CSV Sales Data Viewer

> INTERNAL DOCUMENT. This file is for developer and AI assistant reference.
> It is not intended for public audiences.
> Update this file at the end of every working session.

---

## How to Use This File (For AI Assistants)

If you are an AI assistant helping with this project, start here.

1. Read this entire file before suggesting any changes or writing any code.
2. Read the README.md file for the public-facing project description.
3. Read `data/README.md` for the data dictionary and source documentation.
4. Do not change the folder structure or core conventions without
   discussing it with the developer first.
5. Follow all conventions listed in the Conventions section exactly.
6. Do not suggest technologies or approaches listed in the
   "What Was Tried and Rejected" section.
7. Ask clarifying questions before making large structural changes.
8. This project was vibe coded with AI assistance (Claude). The code works
   but may have inconsistencies typical of AI-generated output. Refactor
   conservatively and only when asked.

---

## Current State

**Last Updated: 2026-02-25**

The application is functional at v1.0.0. It loads a CSV file via the Fetch API
and renders the data as a styled HTML table. All core features are working.
Known limitations are documented below.

### What Is Working
- [x] CSV file loads correctly via `fetch()` from `data/sales.csv`
- [x] CSV is parsed into headers and rows using vanilla JavaScript
- [x] Data renders as a styled, responsive HTML table
- [x] Category column displays color-coded badges (Electronics, Accessories, Furniture)
- [x] Unit Price and Total columns are formatted as USD currency
- [x] Row count summary displays in the footer
- [x] Error message displays if the CSV file fails to load
- [x] README.md documents the project for public audiences
- [x] `data/README.md` provides a data dictionary for `sales.csv`

### What Is Partially Built
- [ ] Mobile layout renders but is not optimized for narrow screens

### What Is Not Started
- [ ] Column sorting by clicking headers
- [ ] Category filter dropdown
- [ ] Drag-and-drop CSV upload for user-supplied data files
- [ ] Summary row showing totals and averages
- [ ] Export filtered/sorted data back to CSV

---

## Current Task

**What I was working on when I last stopped:**

The project reached v1.0.0 completion. All originally scoped features are
working. The session ended after committing the initial release to GitHub
at https://github.com/mikecolbert/3300-scm.

**The very next step is:**

Address known issues from the README to-do list. The highest priority item
is fixing CSV parsing to handle fields that contain commas within quoted
strings (e.g., `"Smith, John"`). This is a bug in the `parseCSV()` function
in `index.html`.

---

## Architecture and Tech Stack

| Technology      | Version  | Why It Was Chosen                                              |
|-----------------|----------|----------------------------------------------------------------|
| HTML5           | —        | Page structure; single-file approach keeps setup simple        |
| CSS3            | —        | Inline in `index.html`; no build step required                 |
| JavaScript ES6+ | —        | Vanilla JS only; no frameworks needed for this scope           |
| Fetch API       | —        | Built into modern browsers; loads CSV without a library        |
| CSV             | —        | Simple, portable data format appropriate for the demo          |

---

## Project Structure Notes

- The entire application is a single `index.html` file. HTML, CSS, and
  JavaScript are all inline. Do not split into separate files unless
  explicitly asked — keeping it in one file is intentional for demo clarity.
- The `data/` folder holds `sales.csv` and its own `README.md`.
  Do not move data files out of the `data/` folder.
- There is no build step, package.json, or node_modules.
  Do not introduce npm dependencies without discussion.
- The CSV path in `index.html` is hardcoded as `'data/sales.csv'`.
  If the file is renamed or moved, this reference must be updated.

```
3300-scm/
├── index.html        # Entire application — HTML, CSS, and JavaScript
├── data/
│   ├── sales.csv     # Sample sales transaction data (10 records)
│   └── README.md     # Data dictionary and source documentation
├── README.md         # Public-facing project documentation
└── CLAUDE.md         # This file — developer and AI assistant reference
```

---

## Data

This project has no database. Data comes from a static CSV file.

### File: `data/sales.csv`

| Column     | Type           | Notes                                      |
|------------|----------------|--------------------------------------------|
| Order ID   | Integer        | Unique identifier per transaction          |
| Product    | String         | Product name                               |
| Category   | String         | One of: Electronics, Accessories, Furniture|
| Quantity   | Integer        | Units sold                                 |
| Unit Price | Decimal (USD)  | Price per unit at time of sale             |
| Total      | Decimal (USD)  | Quantity × Unit Price                      |
| Date       | Date YYYY-MM-DD| Transaction date                           |

The data is synthetic and was generated for educational purposes.
See `data/README.md` for full documentation.

---

## Conventions

### File Organization
- All application logic lives in `index.html` — do not externalize CSS or JS
  unless explicitly asked
- Data files live in `data/` — do not place data files in the root

### JavaScript
- Vanilla JavaScript only — no jQuery, no frameworks, no libraries
- Use `async/await` for the fetch call, not `.then()` chains
- The CSV parser is intentionally simple (split on commas and newlines)
  — do not replace it with a library without discussion
- Do not use `localStorage` or `sessionStorage` — see What Was Tried and Rejected

### CSS
- Styles are defined in a `<style>` block in the `<head>` of `index.html`
- Color palette: dark header `#2d3748`, background `#f0f4f8`, white cards
- Badge colors: Electronics `#bee3f8/#2b6cb0`, Accessories `#c6f6d5/#276749`,
  Furniture `#fefcbf/#744210`
- Do not change badge colors without updating all three category styles together

### HTML
- The table is built entirely via JavaScript DOM manipulation — there is no
  static table markup in the HTML
- The `.table-wrapper` div is the mount point for the dynamically built table
- The `#status` div is used for loading and error states only

### Git
- Commit messages use imperative present tense: "Add column sorting" not "Added"
- Commit directly to main for now — no branching convention established yet

---

## Decisions and Tradeoffs

- **Single `index.html` file:** All HTML, CSS, and JavaScript are inline.
  Chosen for simplicity and demo clarity. Students can open one file and
  see everything. Do not suggest splitting unless the file grows unwieldy.

- **No CSV parsing library (e.g., PapaParse):** The parser is intentionally
  simple to show students how parsing works. It has known limitations
  (see Known Issues). Do not suggest a library unless asked.

- **Hardcoded CSV path:** The path `'data/sales.csv'` is hardcoded in the
  fetch call. A file picker or configurable path was considered but rejected
  as out of scope for v1.0.0.

- **No back-end:** This is a purely front-end application.
  Do not suggest adding a server, Node.js, or any back-end technology
  unless explicitly asked.

- **Synthetic data:** The CSV contains made-up sales records.
  This was intentional to avoid any data privacy concerns in a classroom demo.

---

## What Was Tried and Rejected

- **`localStorage` for storing CSV data between sessions:** Not supported
  in the Claude.ai artifact environment and adds complexity without benefit
  for this use case. Do not suggest it.

- **`file://` protocol for opening the app directly:** Blocked by browser
  security (CORS). The app requires a local web server. This is documented
  in the README and is actually a useful teaching moment — do not work around it.

- **Separate CSS and JS files:** Keeping everything in `index.html` was
  chosen for simplicity. Do not suggest splitting into separate files.

---

## Known Issues and Workarounds

- **CSV parser does not handle quoted fields with commas:** Fields like
  `"Smith, John"` will be split incorrectly because the parser splits naively
  on commas. There is no workaround in place yet. This is the top to-do item.
  When fixing, implement RFC 4180-compliant parsing rather than introducing
  a library.

- **No column sorting:** Clicking table headers does nothing. There is no
  workaround. This is a planned feature for a future version.

- **No category filtering:** All records are always shown. There is no
  workaround. This is a planned feature for a future version.

- **Mobile layout not optimized:** The table scrolls horizontally on narrow
  screens, which is functional but not polished. No workaround in place.

- **Requires a local server:** The app cannot be opened directly from disk
  as a `file://` URL due to browser fetch restrictions. The workaround is
  to use a local server (VS Code Live Server, `python -m http.server`, or
  `npx serve`). This is documented in the README and is intentional.

---

## Browser and Environment Compatibility

- **Tested in:** Chrome (latest), via VS Code Live Server
- **Expected to work in:** Firefox, Edge, Safari (all modern versions)
- **Not tested in:** Internet Explorer (not supported — ES6+ is required)
- **Local server required:** Any of VS Code Live Server, `python -m http.server 8000`,
  or `npx serve .` works correctly

---

## Open Questions

- Should the CSV parser be fixed manually (RFC 4180 implementation) or is
  introducing PapaParse acceptable at that point?
- Should column sorting be implemented in JavaScript or is a library like
  DataTables acceptable for that feature?
- Should a drag-and-drop file upload replace the hardcoded CSV path, or
  should the hardcoded path remain and drag-and-drop be added as an option?

---

## Session Log

### 2026-02-25
- Created `index.html` with full CSV fetch, parse, and table render functionality
- Created `data/sales.csv` with 10 synthetic sales records
- Created `data/README.md` with data dictionary
- Created `README.md` with full public documentation including all sections
- Created `README-generator-prompt.md` as a student handout (not committed to repo)
- Created `CLAUDE.md` (this file)
- Committed initial release as v1.0.0 to https://github.com/mikecolbert/3300-scm
- Left incomplete: CSV quoted field parsing, column sorting, category filter,
  mobile layout optimization
- Next step: Fix CSV parser to handle RFC 4180 quoted fields with commas

---

## Useful References

- [MDN — Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN — Document.createElement](https://developer.mozilla.org/en-US/docs/Web/API/Document/createElement)
- [RFC 4180 — CSV format specification](https://datatracker.ietf.org/doc/html/rfc4180)
- [shields.io static badge builder](https://shields.io/badges/static-badge)
- [Simple Icons](https://simpleicons.org)
- [VS Code Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)
- Initial project code generated with AI assistance (Claude, Anthropic)

# CSV Sales Data Viewer

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![CSV](https://img.shields.io/badge/Data-CSV-blue?style=flat)
![Last Commit](https://img.shields.io/github/last-commit/mikecolbert/3300-scm)

_Add badges that reflect your project's language, license, and status. Generate them at [shields.io](https://shields.io). Replace the GitHub username and repo name in the last badge URL._

---

## Description

A lightweight browser-based application that fetches a local CSV file and renders its contents as a formatted HTML table — no frameworks, no build tools, no back-end required. Built to demonstrate core JavaScript concepts including the Fetch API, CSV parsing, and dynamic DOM manipulation.

_Write 2–4 sentences describing what your project does, why you built it, and who it's for. Focus on what the project accomplishes, not how it works — save the technical details for the Tech Stack and Features sections._

---

## Features

- Loads sales data dynamically from a local CSV file using the Fetch API
- Parses CSV content entirely in vanilla JavaScript — no libraries required
- Renders data as a styled, responsive HTML table
- Color-coded category badges for quick visual scanning
- Automatic currency formatting for price and total columns
- Row count summary displayed in the footer
- Graceful error handling with a user-friendly message if the file cannot be loaded

_List the key capabilities of your project. Focus on what the application does from the user's perspective. Aim for 4–8 bullet points._

---

## Tech Stack

| Technology        | Purpose                                     |
| ----------------- | ------------------------------------------- |
| HTML5             | Page structure and layout                   |
| CSS3              | Styling and responsive design               |
| JavaScript (ES6+) | CSV fetching, parsing, and DOM manipulation |
| CSV               | Data storage format                         |

_List every language, library, framework, or tool your project uses and briefly explain what role each plays. If you used any external APIs or services, include those here too._

---

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Edge, or Safari)
- A local development server — required because the Fetch API is blocked by browsers when opening files directly from disk (`file://` protocol)

**Recommended options for running a local server:**

- [VS Code Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) — right-click `index.html` → _Open with Live Server_
- Python (built-in): `python -m http.server 8000`
- Node.js: `npx serve .`

_List everything a user needs to have installed or configured before they can run your project. Be specific about versions if they matter._

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/mikecolbert/3300-scm.git
   ```

2. Navigate into the project folder:

   ```bash
   cd 3300-scm
   ```

3. Start a local server. For example, using Python:

   ```bash
   python -m http.server 8000
   ```

4. Open your browser and go to:
   ```
   http://localhost:8000
   ```

_Walk the reader through every step needed to get the project running locally. Assume the reader has the prerequisites installed but nothing else. Number your steps and include the exact commands to run._

---

## Usage

Once the application is running in your browser, the sales table will load automatically. The table displays all records from `data/sales.csv` with formatted currency values and color-coded category badges.

To use your own data, replace the contents of `data/sales.csv` with your own CSV file. The application will automatically use the first row as column headers and render all subsequent rows as table data.

_Describe how to actually use the application after it's running. Include any configuration options, how to swap in different data, or how to trigger key features. Screenshots or GIFs are especially effective here._

---

## Project Structure

```
3300-scm/
├── index.html        # Main application page — loads and displays the CSV
├── data/
│   ├── sales.csv     # Sample sales transaction data
│   └── README.md     # Data dictionary and source documentation
└── README.md         # This file
```

_Show the folder and file layout of your project. Briefly annotate each file or folder so a reader understands its role at a glance. You don't need to list every file — focus on the ones that matter._

---

## Changelog

### v1.0.0 — 2024-02-25

- Initial release
- CSV fetch and parse functionality
- Styled HTML table with category badges and currency formatting
- Error handling for failed file loads
- Data README with data dictionary

_Track meaningful changes to your project over time. Use version numbers (v1.0.0, v1.1.0, etc.) and dates. This helps collaborators and instructors understand how your project evolved._

---

## Known Issues / To-Do

- [ ] CSV parsing does not currently handle fields that contain commas within quoted strings (e.g., `"Smith, John"`)
- [ ] No support for sorting columns by clicking headers
- [ ] Table is not yet filterable by category
- [ ] Mobile layout could be improved for narrow screens

_Be honest about what's broken or incomplete. Use checkboxes (`- [ ]`) so items can be checked off as they're resolved. This section shows self-awareness and good engineering judgment._

---

## Roadmap

- Add column sorting (ascending/descending) by clicking any header
- Add a category filter dropdown above the table
- Support drag-and-drop CSV upload so users can load their own files
- Add a summary row showing totals and averages
- Export filtered/sorted data back to CSV

_The Roadmap is different from Known Issues — it's forward-looking. What would the next version of this project look like? What features would make it significantly more useful? This is a good place to think ambitiously._

---

## Contributing

Contributions, suggestions, and bug reports are welcome. To contribute:

1. Fork the repository
2. Create a new branch: `git checkout -b feature/your-feature-name`
3. Make your changes and commit: `git commit -m "Add your feature"`
4. Push to your branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

_Explain how others can contribute to your project. For class projects, this section can also describe how teammates divided work or how a future student could extend the project._

---

## License

This project is licensed under the [MIT License](LICENSE).

_Choose a license that fits your project. [MIT](https://choosealicense.com/licenses/mit/) is a good default for most student projects — it's permissive and widely understood. Visit [choosealicense.com](https://choosealicense.com) if you're unsure which to use._

---

## Author

**Mike Colbert**  
University of Iowa — Tippie College of Business  
BAIS 3300: Digital Product Management

_Include your name, your institution or course, and any relevant context. This is your professional credit for the work._

---

## Contact

Mike Colbert — [GitHub @mikecolbert](https://github.com/mikecolbert)

_Add your preferred contact method — GitHub profile, LinkedIn, or university email. This is especially important if you plan to share the repo as part of a portfolio._

---

## Acknowledgements

- Initial code structure generated with AI assistance (Claude) and reviewed/modified by the author.
- [shields.io](https://shields.io) — for the README badge generator
- [MDN Web Docs](https://developer.mozilla.org) — Fetch API and DOM documentation
- [CSV format reference](https://datatracker.ietf.org/doc/html/rfc4180) — RFC 4180

_Credit any tutorials, tools, libraries, or people that helped you build the project. This is good academic and professional practice._

# GL Dining: Website Development Checkpoint

GL Dining is a site for two Norman, Oklahoma restaurants owned by one family:

- blu, downtown, fine wine and food, 201 S Crawford Ave, Norman, OK 73069, (405) 360-4258
- The Library, across from campus, bar and grill, est. 1920, 607 W Boyd St, Norman, OK 73069, (405) 366-7465

Plain HTML, CSS, and JavaScript. No build step, no framework, no install
needed. That keeps hosting simple: GitHub Pages serves these files as they are.

## Run it locally

Open `index.html` in a browser, or run `python3 -m http.server` in this
folder and open the local address it prints.

## What is in the folder

- `index.html` - Page structure for all three views, with a proper doctype,
  head, and body. It links `styles.css` and `script.js`.
- `styles.css` - The design system, extracted from the original framework file.
- `script.js` - Photos, venue data, menu rendering, live open and closed
  status, routing, and the careers form handler.

This project was converted from the team's single framework file,
`GL_Framework_2__1.html`. Content, menus, hours, photos, and styling were
kept. The changes were structural only: CSS and JavaScript were moved into
their own files, and a full HTML document wrapper was added, because the
framework file started at the title tag with no doctype, html, head, or body.

## Pages and routes

One HTML file, three views, switched by the hash in the URL:

| Route | View | What is on it |
|---|---|---|
| `#home` | Home | GL Dining hero, a door card for each restaurant with live open or closed status, and an at a glance section for hours and locations |
| `#blu` | blu | Banner, address, phone, and today hours, Specials and activities, full menu with category tabs, Visit section with hours, gallery, and directions |
| `#library` | The Library | Same venue layout as blu, filled with The Library data, menu, specials, and hours |
| `#careers` | Careers | Come work with us, job cards for both restaurants, perks, and an application form |

Menu categories already in the data:

- blu: Share, Pizza, Tacos and Dillas, Burgers and Leaf, Lunch, Brunch, Wine, and more
- The Library: Appetizers, Salads and Soups, Burgers and Sammies, and more

## Navigation

- Sticky top bar on every view, with the GL Dining brand.
- Home nav: blu, The Library, Careers.
- Venue nav: Specials, Menu, Visit, Careers, which scroll to those sections.
- Routing in `route()` in `script.js` listens for hash changes, shows the
  right view, and sets the page title for each view.

## Design system

In `:root` in `styles.css`:

- Colors: `--bg`, `--surface`, `--ink`, `--muted`, `--line`, plus `--gold`,
  `--peach`, and `--butter` for the home and careers views.
- blu palette: `--blu`, `--blu-2`, `--blu-soft`.
- The Library palette: `--lib`, `--lib-2`, `--lib-soft`.
- Status colors: `--open` and `--closed`.
- Fonts: Playfair Display for home, Quicksand for blu, Old Standard TT for
  The Library, Figtree for body text.
- Each venue view swaps its accent, soft background, and display font using
  `.view-blu` and `.view-library`.
- Responsive rules at several widths, down to 480px, plus a
  prefers-reduced-motion rule.

## Features already working

- Live open or closed status for both restaurants, calculated from the
  hours in the venue data, refreshed every minute.
- Menus rendered from the `VENUES` data in `script.js`, so editing a menu
  means editing data, not markup.
- Specials, galleries, weekly hours tables, and Get directions links on
  each venue page.
- Careers application form with a confirmation message. Honest limit: the
  form is a class demo, it does not send anything yet, and the page says so
  when you submit it.

## How to edit

- Menus, hours, specials, addresses, phones: edit `VENUES` in `script.js`.
  Each menu item is `["Name", "Price", "Description", "V GF"]`.
- Colors and fonts: edit `:root` in `styles.css`.
- Page structure and text outside the venue data: edit `index.html`.
- Photos are built into `script.js` in the `PHOTOS` list, so they show
  anywhere without an image folder. Note: that makes `script.js` large,
  about 578 KB. Moving photos to an `img/` folder is a good later cleanup.

## Checkpoint checklist

| Requirement | Status |
|---|---|
| Development environment / project established | Done. Three files plus this README, runs with no install |
| GitHub repository established and shared | Repository created at https://github.com/shingai7/gl-dining, public. Collaborator invitations are the next step, see below |
| Basic website structure created | Done. Full HTML document, header, main, sections, footer |
| Major pages / routes created or planned | Done. Home, blu, The Library, Careers |
| Navigation implemented or substantially underway | Done. Sticky top bar, view routing, section links |
| Design system / styles beginning to be implemented | Done. Tokens, per venue themes, responsive rules in `styles.css` |
| Development responsibilities divided | Plan below, by GitHub username |
| Hosting / deployment approach identified | GitHub Pages, steps below |
| Meaningful development activity from all team members | Commit plan below |

## GitHub setup

Repository: https://github.com/shingai7/gl-dining, owner shingai7, public,
created empty with no README, .gitignore, or license added.

1. Settings, Collaborators: invite jaxsonjennings, onyekwerechinedu04,
   presleymayer, and Cisn0015. Each person accepts the invitation.
2. Build the repo up in parts using the commit plan below, with each
   person committing their own component from their own account.
3. Turn on Pages: Settings, Pages, Deploy from a branch, branch `main`,
   folder `/ (root)`. The published URL is the link to submit.

## Team commit plan

Build the repo up in parts, one owner per component, so each commit adds
something real and every member is visible. Adjust names and team size.

**shingai7, structure and navigation**
- `Set up project structure with Home, venue, and Careers views`
- `Create responsive GL Dining navigation`
- `Add hash routing for blu, The Library, and Careers`

**jaxsonjennings, design system**
- `Create design system with colors, fonts, and spacing tokens`
- `Add blu and Library venue themes`
- `Add mobile styling to homepage`

**onyekwerechinedu04, blu page and menu**
- `Build menu card component`
- `Add blu menu data with Share, Pizza, and Brunch sections`
- `Add blu specials and live open status`

**presleymayer, The Library page and menu**
- `Add Library menu data and specials`
- `Build Library venue page with hours and gallery`
- `Add Library live open status`

**Cisn0015, Careers and hosting**
- `Build Careers page with job cards for both restaurants`
- `Add job application form with confirmation message`
- `Enable GitHub Pages and verify the live site`

Keep one owner per component. Do not pad with trivial commits.

## Known gaps and next steps

- The application form needs a real destination before launch, for example
  a form service or an email workflow.
- Photos should move from `script.js` to an `img/` folder before launch.
- If the instructor required React, or a separate HTML file per page, do
  not submit this version as is. The routes, data, and design tokens map
  directly, but the code structure would need to change.

# GL Dining: Website Development Checkpoint

This is our site for GL Dining, which is two restaurants in Norman owned by the same family:

- **blu**: downtown, fine wine and food. 201 S Crawford Ave, Norman, OK 73069, (405) 360-4258
- **The Library**: the bar and grill across from campus, open since 1920. 607 W Boyd St, Norman, OK 73069, (405) 366-7465

We kept it simple and just used HTML, CSS, and JavaScript. No framework, nothing to install, no build step. That way GitHub Pages can just host the files the way they are

## Run it locally

Just open `index.html` in your browser. If you want to use a local server instead, run `python3 -m http.server` in this folder and open the address it gives you

## What is in the folder

- `index.html`: the layout for all three views. It has the doctype, head, and body, and it links to `styles.css` and `script.js`
- `styles.css`: all our styling. We pulled this out of the original framework file
- `script.js`: the photos, restaurant info, menus, open/closed status, page switching, and the careers form

We started from our team's framework file, `GL_Framework_2__1.html`. We didn't change any of the content, menus, hours, photos, or styling. We just split the CSS and JavaScript into their own files and added the doctype, html, head, and body tags, because the framework file started at the title tag and didn't have those

## Pages and routes

It's all one HTML file with three views. The hash at the end of the URL decides which one shows up

| Route | View | What is on it |
|---|---|---|
| `#home` | Home | The GL Dining banner, a card for each restaurant that shows if it's open or closed right now, and a quick look at hours and locations |
| `#blu` | blu | Banner with the address, phone, and today's hours, specials and events, the full menu with tabs for each category, and a Visit section with hours, photos, and directions |
| `#library` | The Library | Same setup as blu but with The Library's info, menu, specials, and hours |
| `#careers` | Careers | A "come work with us" section, job cards for both restaurants, perks, and an application form |

Menu categories we already have in the data:

- blu: Share, Pizza, Tacos and Dillas, Burgers and Leaf, Lunch, Brunch, Wine, and more
- The Library: Appetizers, Salads and Soups, Burgers and Sammies, and more

## Navigation

- There's a top bar with the GL Dining name that stays at the top on every page
- On the home page the nav has blu, The Library, and Careers
- On the restaurant pages the nav has Specials, Menu, Visit, and Careers, and clicking them scrolls you down to that part
- The `route()` function in `script.js` checks when the hash changes, shows the right view, and changes the page title to match

## Design system

Everything is set up in `:root` in `styles.css`:

- Main colors: `--bg`, `--surface`, `--ink`, `--muted`, `--line`, and then `--gold`, `--peach`, and `--butter` for the home and careers pages
- blu colors: `--blu`, `--blu-2`, `--blu-soft`
- The Library colors: `--lib`, `--lib-2`, `--lib-soft`
- Open/closed colors: `--open` and `--closed`
- Fonts: Playfair Display on home, Quicksand for blu, Old Standard TT for The Library, and Figtree for regular text
- `.view-blu` and `.view-library` change the accent color, background, and heading font so each restaurant has its own look
- It works on smaller screens too (we have breakpoints down to 480px), and there's a prefers-reduced-motion rule for people who turn off animations

## Features already working

- Both restaurants show if they're open or closed right now based on their hours, and it updates every minute
- The menus come from the `VENUES` data in `script.js`, so if you need to change a menu you just change the data, not the HTML
- Each restaurant page has specials, a photo gallery, a weekly hours table, and a Get directions link
- The careers form shows a confirmation message when you submit it. Since this is for class it doesn't actually send anywhere yet, and the page tells you that when you hit submit

## How to edit

- Menus, hours, specials, addresses, phone numbers: change `VENUES` in `script.js`. Each menu item looks like `["Name", "Price", "Description", "V GF"]`
- Colors and fonts: change `:root` in `styles.css`
- Anything else on the page that isn't restaurant data: change `index.html`
- The photos are stored right inside `script.js` in the `PHOTOS` list so they load without needing an image folder. The only problem is it makes `script.js` really big (around 578 KB), so we want to move them to an `img/` folder later

## Checkpoint checklist

| Requirement | Status |
|---|---|
| Development environment / project established | Done. Three files plus this README, and you don't have to install anything |
| GitHub repository established and shared | Repo is made at https://github.com/shingai7/gl-dining and it's public. Next we need to send collaborator invites (see below) |
| Basic website structure created | Done. Full HTML document with a header, main, sections, and footer |
| Major pages / routes created or planned | Done. Home, blu, The Library, Careers |
| Navigation implemented or substantially underway | Done. Sticky top bar, page switching, and section links |
| Design system / styles beginning to be implemented | Done. Color and font variables, a theme for each restaurant, and mobile styles in `styles.css` |
| Development responsibilities divided | Plan is below, by GitHub username |
| Hosting / deployment approach identified | GitHub Pages, steps are below |
| Meaningful development activity from all team members | Commit plan is below |

## GitHub setup

Our repo is https://github.com/shingai7/gl-dining. shingai7 owns it, it's public, and we made it empty (no README, .gitignore, or license).

1. Go to Settings, then Collaborators, and invite jaxsonjennings, onyekwerechinedu04, presleymayer, and Cisn0015. Everyone has to accept their invite
2. Add to the repo piece by piece using the commit plan below. Everyone commits their own part from their own account
3. Turn on Pages: Settings, then Pages, then Deploy from a branch. Pick the `main` branch and the `/ (root)` folder

## Team commit plan

We're building the repo in parts and each person owns one part. That way every commit actually adds something and everyone's work shows up

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

Stick to one owner per part.

## Known gaps and next steps

- The application form needs to actually send somewhere before the site goes live, like a form service or an email setup
- We need to move the photos out of `script.js` and into an `img/` folder before launch

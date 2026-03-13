# El Molinito — Website

The official website for **El Molinito**, a Mexican catering business based in the Netherlands. It is a single-page static site hosted on GitHub Pages at [elmolinito.nl](https://elmolinito.nl).

---

## What's in this project

```
Molinito-Web/
├── index.html        ← The entire website (HTML + CSS + JavaScript in one file)
├── data.json         ← All editable content: contact info, menu dishes, social links
├── CNAME             ← Tells GitHub Pages to use the custom domain elmolinito.nl
└── images/
    ├── El_molinito_logo.png
    ├── food/         ← Dish photos shown in the menu
    └── decorators/   ← Background and decorative images
```

**The most important file for day-to-day edits is `data.json`** — you can update phone numbers, email, dishes, and prices there without touching any code.

---

## How to set up on your machine

### Step 1 — Install Git

Git is a tool that lets you download and track changes to code.

- **Mac:** Open Terminal and run `git --version`. If it's not installed, macOS will prompt you to install it.
- **Windows:** Download it from [git-scm.com](https://git-scm.com) and run the installer.
- **Linux:** Run `sudo apt install git` (Ubuntu/Debian) or `sudo dnf install git` (Fedora).

Verify it worked:
```bash
git --version
```
You should see something like `git version 2.x.x`.

---

### Step 2 — Clone the repository

"Cloning" means downloading a full copy of the project to your computer.

Open your Terminal (Mac/Linux) or Git Bash (Windows), navigate to where you want the folder, then run:

```bash
git clone https://github.com/CarlosVargas91/Molinito-Web.git
```

This creates a folder called `Molinito-Web` with all the files inside.

```bash
cd Molinito-Web
```

---

### Step 3 — Preview the website locally

No server or installation required. Just open the file in your browser:

- **Mac:** `open index.html`
- **Windows:** Double-click `index.html` in File Explorer
- **Linux:** `xdg-open index.html`

> **Note:** Some features (like loading the menu from `data.json`) require a local server to work properly due to browser security restrictions. See the tip below.

**Recommended — run a simple local server:**

If you have Python installed (most Macs and Linux machines do):
```bash
python3 -m http.server 8080
```
Then open [http://localhost:8080](http://localhost:8080) in your browser. Press `Ctrl+C` in the terminal to stop it.

---

## How to make changes

### Updating contact info, phone, email, or address

Open `data.json` in any text editor (Notepad, TextEdit, VS Code, etc.) and edit the `contact` section:

```json
"contact": {
  "phone": "+310627993504",
  "phoneDisplay": "+31 6 27 993 504",
  "email": "elmolinito.nl@gmail.com",
  ...
}
```

The `phone` field is used for the WhatsApp order buttons throughout the menu. The `phoneDisplay` is the human-readable version shown on the page.

---

### Adding or editing a dish

In `data.json`, find the `menu` array. Each dish looks like this:

```json
{
  "name": "Enchiladas Suizas",
  "ingredients": "Corn tortillas · roasted tomatillo salsa · chicken · cream · fresh cheese",
  "price": "€12",
  "tag": "Main Course",
  "image": "images/food/Enchiladas.png"
}
```

- **Add a dish:** Copy an existing block (including the `{ }` and the comma after it), paste it, and change the values.
- **Remove a dish:** Delete the entire `{ ... }` block for that dish. Make sure no trailing comma is left on the block before it.
- **Change a price:** Edit the `"price"` value, e.g. `"€15"`.
- **Add an image:** Put the photo inside `images/food/` and set `"image": "images/food/your-photo.jpg"`.

---

### Editing text, layout, or styles

All HTML, CSS, and JavaScript lives in `index.html`. Open it in a code editor like [VS Code](https://code.visualstudio.com) (free). The file is structured in three clear blocks:

- **`<style>`** — all visual styles (colors, fonts, layout)
- **`<body>`** — all the page content and structure
- **`<script>`** — behavior (loading data, tabs, cursor, scroll effects)

The color palette is defined at the top of the `<style>` block as CSS variables:

```css
:root {
  --clay:       #A0432A;
  --rust:       #E07A45;
  --warm-white: #F9F3EC;
  ...
}
```

Change a value there to update that color everywhere on the site.

---

## How to save and publish your changes

After editing files, you need to send them back to GitHub so the live website updates.

### Step 1 — Check what you changed
```bash
git status
```
This lists all modified files.

### Step 2 — Stage your changes
```bash
git add data.json
```
Replace `data.json` with the file(s) you changed. To stage everything at once:
```bash
git add .
```

### Step 3 — Save a snapshot (commit)
```bash
git commit -m "Update menu prices"
```
Write a short message describing what you changed.

### Step 4 — Upload to GitHub (push)
```bash
git push
```
You may be asked for your GitHub username and password (or a personal access token).

**The website at elmolinito.nl updates automatically within ~1 minute after pushing.**

---

## How the live site works

This site is hosted on **GitHub Pages** — a free service by GitHub that publishes any repository as a website. The `CNAME` file tells GitHub Pages to serve the site under the custom domain `elmolinito.nl` instead of the default `carlosvargas91.github.io/Molinito-Web` address.

No build step, no backend, no database — every change you push goes live directly.

---

## Need help?

- Git basics: [git-scm.com/book](https://git-scm.com/book/en/v2) (free book)
- GitHub Pages docs: [docs.github.com/pages](https://docs.github.com/en/pages)
- VS Code download: [code.visualstudio.com](https://code.visualstudio.com)

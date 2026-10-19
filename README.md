# product-management-html-skills

A collection of Claude skills for building HTML pages: comparison tables, code chunks that look like notebook cells, architecture diagrams, collapsible sections and status tags.

A **skill** is a folder of instructions that Claude reads when your request matches it. You copy the folder to one place on your computer, and Claude finds it by itself.

## What is in this repo

```
product-management-html-skills/
  README.md                          <- this file
  skills/
    html-building-blocks-skill/      <- the skill (one folder = one skill)
      SKILL.md                       <- the instructions Claude reads
      html-preferences.csv           <- page, diagram and table rules
      communication-preferences.csv  <- how replies and working style should go
      assets/
        components.css               <- styles for every block
        components.html              <- demo page with markup for every block
```

| Skill | What it does |
|---|---|
| `html-building-blocks-skill` | Builds single-file HTML pages for analysis and comparison documents, using ready-made blocks and a fixed set of style rules. |

## Choose where you will use it

| You use | Go to |
|---|---|
| Claude Code (the program you start by typing `claude` in a terminal) | [Part A](#part-a-install-in-claude-code) |
| claude.ai in a web browser, or the Claude desktop app | [Part B](#part-b-install-on-claudeai-or-the-desktop-app) |

---

## Part A: Install in Claude Code

### Step 1. Open a terminal

- **Mac:** press Command + Space, type `Terminal`, press Enter.
- **Windows:** click Start, type `PowerShell`, press Enter.
- **Linux:** open your terminal program.

### Step 2. Check that Claude Code is installed

Type this and press Enter:

```
claude --version
```

- If you see a version number, go to Step 3.
- If you see `command not found` or "not recognized", install Claude Code first. Follow the official guide: https://code.claude.com/docs/en/quickstart . On Mac, Linux and WSL, the guide gives this command: `curl -fsSL https://claude.ai/install.sh | bash` . On Windows PowerShell, the guide gives a different command, so copy it from the guide. Then close the terminal, open a new one, and repeat this step.

### Step 3. Download this repo

Pick **one** of these two ways.

**Way 1: with git.** Type this and press Enter:

```
git clone https://github.com/rvolchek/product-management-html-skills.git
```

This makes a folder named `product-management-html-skills` in the folder your terminal is in.

**Way 2: without git.**
1. Open https://github.com/rvolchek/product-management-html-skills in your browser.
2. Click the green **Code** button, then click **Download ZIP**.
3. Open the downloaded ZIP file. It unpacks into a folder named `product-management-html-skills-main`.

### Step 4. Go into the downloaded folder

Type `cd ` (with a space after it), then drag the folder from your file window into the terminal, then press Enter.

If you used Way 1, you can type this instead:

```
cd product-management-html-skills
```

Check that you are in the right place. Type this and press Enter:

- Mac or Linux: `ls skills`
- Windows PowerShell: `dir skills`

You should see `html-building-blocks-skill`. If you do not, you are in the wrong folder. Repeat Step 4.

### Step 5. Create the Claude skills folder

Claude looks for skills in one folder inside your home folder. Type this and press Enter:

- **Mac or Linux:**
  ```
  mkdir -p ~/.claude/skills
  ```
- **Windows PowerShell:**
  ```
  New-Item -ItemType Directory -Force "$HOME\.claude\skills"
  ```

It is fine if the folder already exists. Nothing is lost.

### Step 6. Copy the skill into that folder

- **Mac or Linux:**
  ```
  cp -R skills/html-building-blocks-skill ~/.claude/skills/
  ```
- **Windows PowerShell:**
  ```
  Copy-Item -Recurse skills\html-building-blocks-skill "$HOME\.claude\skills\"
  ```

### Step 7. Check that the copy worked

- **Mac or Linux:**
  ```
  ls ~/.claude/skills/html-building-blocks-skill
  ```
- **Windows PowerShell:**
  ```
  dir "$HOME\.claude\skills\html-building-blocks-skill"
  ```

You must see these names in the list: `SKILL.md`, `assets`, `html-preferences.csv`, `communication-preferences.csv`.

**The most common mistake:** if you see another folder named `html-building-blocks-skill` inside the list instead of `SKILL.md`, the skill is one level too deep. Move the files up one level so that `SKILL.md` sits directly inside `html-building-blocks-skill`.

### Step 8. Start Claude Code

Type this and press Enter:

```
claude
```

If Claude Code was already open **before** you did Step 5, close it and start it again. This is needed only when the `~/.claude/skills` folder did not exist before.

### Step 9. Confirm that Claude can see the skill

Inside Claude Code, type `/` and then the first letters `html-building`. The name `html-building-blocks-skill` must appear in the list.

If it does not appear:
1. Type `/doctor` and press Enter. It reports skills that were skipped.
2. Repeat Step 7 and check for the mistake described there.

### Step 10. Use it

Type a request in plain words, for example:

```
Build an HTML page that compares Tool A and Tool B. Put a short comparison table at the top, then a hello-world code example for each tool.
```

Claude reads the skill when your request is about building a page like this. To force it, start your message with `/html-building-blocks-skill`.

---

## Part B: Install on claude.ai or the desktop app

Claude.ai and the desktop app take a skill as a **ZIP file**. You upload the ZIP once.

**Menu names change.** Anthropic's help page says **Settings > Capabilities**. Other documents say **Settings > Features** or **Customize**. Use the one that shows on your screen. The help page: https://support.claude.com/en/articles/12512180-using-skills-in-claude

### Step 1. Download this repo

Do Step 3 of Part A (git or Download ZIP).

### Step 2. Make a ZIP of the skill folder

The ZIP must contain the folder `html-building-blocks-skill`, with `SKILL.md` directly inside that folder.

- **Mac:** in Finder, open `product-management-html-skills`, then `skills`. Right-click `html-building-blocks-skill` and choose **Compress "html-building-blocks-skill"**.
- **Windows:** in File Explorer, open the same folder. Right-click `html-building-blocks-skill`, choose **Send to**, then **Compressed (zipped) folder**.
- **Terminal alternative (Mac or Linux):** go into the `skills` folder and type `zip -r html-building-blocks-skill.zip html-building-blocks-skill`

### Step 3. Turn on code execution

1. Open claude.ai and click your name or initials.
2. Open **Settings**, then **Capabilities**.
3. Turn on **Code execution and file creation**. Without this, the skill appears greyed out.

### Step 4. Upload the ZIP

1. In the same settings area, find the skills section.
2. Click **Upload skill**.
3. Choose `html-building-blocks-skill.zip`.
4. Turn the skill **on** with its switch.

### Step 5. Use it

Start a new chat and type a request, for example:

```
Build an HTML page that compares Tool A and Tool B, with a comparison table at the top.
```

Skills on claude.ai require a paid plan (Pro, Max, Team or Enterprise) according to Anthropic's help page.

---

## Make it yours

The two CSV files hold the rules that the skill follows. They are one person's preferences, written in that person's own words. Change them to fit you.

1. Open `html-preferences.csv` or `communication-preferences.csv` in Excel, Numbers or Google Sheets.
2. Each row is one rule. The most important columns are `preference` (the rule) and `how_to_apply` (what Claude does).
3. Change a rule, add a row at the bottom, or delete a row.
4. Save the file as **CSV** (not Excel format), with the same file name.
5. Copy the whole skill folder to `~/.claude/skills/` again (Part A, Step 6). Replace the old files if asked.

`SKILL.md` lists the main rules in a table. If you change a rule that is also in that table, change it there too.

## Update to the newest version

1. Go into the repo folder. If you used git, type `git pull`. If you used Download ZIP, download it again.
2. Do Part A, Step 6 again.

## Add another skill to this repo

1. Make a new folder inside `skills/`, for example `skills/my-new-skill/`.
2. Put a file named exactly `SKILL.md` inside it (capital letters, case-sensitive). Start the file with a block like this:
   ```
   ---
   name: my-new-skill
   description: One or two sentences that say what the skill does and when to use it.
   ---
   ```
   The name must match the folder name. Write the instructions below that block.
3. Add one row for the skill to the table under "What is in this repo" above.
4. Install it the same way as above: copy `skills/my-new-skill` into `~/.claude/skills/`.

## Problems

| What you see | What to do |
|---|---|
| `claude: command not found` | Claude Code is not installed. Do Part A, Step 2. |
| The skill is not in the `/` list | Check Part A, Step 7 for the "one level too deep" mistake. Then close Claude Code and start it again. Then type `/doctor`. |
| The skill is greyed out on claude.ai | Turn on **Code execution and file creation** (Part B, Step 3). |
| `No such file or directory` when copying | You are not in the repo folder. Repeat Part A, Step 4. |
| Claude ignores the style rules | Start your message with `/html-building-blocks-skill` to force the skill. |

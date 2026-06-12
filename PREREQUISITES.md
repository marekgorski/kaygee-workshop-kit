# Workshop Prerequisites

**Send this checklist to participants at least 1 week before the workshop.**  
**For IT teams: Share this at least 2 weeks in advance to handle firewall/permission requests.**

---

## What You Need Before Workshop Day

### 1. Laptop

- **MacOS, Windows, or Linux** (any modern OS works)
- **Admin privileges** to install software
- **At least 5 GB of free disk space**
- **Stable internet connection** (required for npm installs and deployments)

---

### 2. Software Installation

Install these **before** the workshop. We won't have time to troubleshoot installations on the day.

#### Required:

| Tool | Why You Need It | Installation |
|------|----------------|--------------|
| **Node.js (v18 or higher)** | Run JavaScript locally | [nodejs.org](https://nodejs.org) — download LTS version |
| **npm (comes with Node.js)** | Install packages | Included with Node.js |
| **Git** | Version control | [git-scm.com](https://git-scm.com/downloads) |
| **Claude Code** | AI coding assistant | See installation instructions below |
| **A code editor** | VS Code, Cursor, or similar | [code.visualstudio.com](https://code.visualstudio.com) (recommended) |
| **GitHub CLI (`gh`)** | Create repos from terminal | [cli.github.com](https://cli.github.com) |

#### Claude Code Installation

Claude Code is installed via npm. Run this in your terminal:

```bash
npm install -g @anthropic-ai/claude-code
```

After installation, run `claude` to start Claude Code. You'll be prompted to authenticate with your Claude account on first run.

**Alternative:** If you prefer a desktop app, you can use [Claude Desktop](https://claude.ai/download) instead. Both work for this workshop.

---

### 3. Account Setup

Create these accounts **before** the workshop (all free):

#### Required:

- **GitHub account** → [github.com/signup](https://github.com/signup)
  - If you already have an account, make sure you can log in
  - **Important:** Set up authentication (SSH key or personal access token)
  
- **Vercel account** → [vercel.com/signup](https://vercel.com/signup)
  - Use "Sign up with GitHub" (easiest option)
  - Authorize Vercel to access your GitHub repos

- **Claude account** → [claude.ai](https://claude.ai)
  - Required for Claude Code to work
  - Make sure you can log in and start a conversation

#### Optional:

- **Anthropic API key** (if using Claude API directly instead of Claude Code) → [console.anthropic.com](https://console.anthropic.com)

---

### 4. Verification Checklist

Run these commands in your terminal to verify everything is installed:

```bash
# Check Node.js version (should be v18 or higher)
node --version

# Check npm version (should be 8.x or higher)
npm --version

# Check Git version
git --version

# Check GitHub CLI
gh --version

# Check Claude Code
claude --version
```

**If any of these commands fail, the tool is not installed correctly.**

---

### 5. GitHub Authentication Setup

**You must set up GitHub authentication before the workshop.** Choose one:

#### Option A: SSH Key (Recommended)

1. Generate an SSH key:
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```
2. Add the key to your GitHub account: [github.com/settings/keys](https://github.com/settings/keys)
3. Test it:
   ```bash
   ssh -T git@github.com
   ```
   You should see: `Hi [username]! You've successfully authenticated...`

#### Option B: Personal Access Token (Easier for beginners)

1. Go to [github.com/settings/tokens](https://github.com/settings/tokens)
2. Click "Generate new token (classic)"
3. Set expiration to 30+ days
4. Select scopes: `repo`, `workflow`
5. Save the token somewhere secure (you'll need it when pushing code)

**If you're not sure which to choose, go with SSH.**

---

### 6. Corporate/Enterprise Considerations

**If you're in a corporate environment, check with IT:**

- Can you access `github.com`, `vercel.com`, and `npmjs.com`?
- Are websockets allowed? (Required for Vercel deployments)
- Do you need proxy settings for npm?
- Can you install software without admin approval?

**For IT teams:**

Please whitelist these domains:
- `*.github.com`
- `*.vercel.com`
- `*.npmjs.com`
- `*.anthropic.com` (for Claude Code)

---

## Pre-Workshop Test Project

**Optional but highly recommended:** Build a tiny "hello world" app to confirm your setup works.

### Test Steps:

1. Create a folder:
   ```bash
   mkdir test-workshop
   cd test-workshop
   ```

2. Create a React + Vite app:
   ```bash
   npm create vite@latest my-app -- --template react
   cd my-app
   npm install
   npm run dev
   ```

3. Open `http://localhost:5173` — you should see the Vite + React starter page.

4. Push to GitHub:
   ```bash
   git init
   git add .
   git commit -m "test"
   gh repo create test-workshop --public --source=. --push
   ```

5. Deploy to Vercel:
   - Go to [vercel.com](https://vercel.com)
   - Click "Add New Project"
   - Import your `test-workshop` repo
   - Click "Deploy"
   - Visit the live URL

**If all of this works, you're ready for the workshop. If any step fails, troubleshoot now (not on workshop day).**

---

## What to Bring on Workshop Day

- ✅ Laptop (fully charged)
- ✅ Charger
- ✅ Notebook & pen (optional, for notes)
- ✅ All the software and accounts from this checklist

**What NOT to bring:**
- ❌ Work/production projects — we're building demo apps, not production code

⚠️ **Important:** We have limited time for setup troubleshooting on workshop day—completing this checklist in advance ensures you get the most out of the sessions.

---

## Terminal 101 (For Non-Technical Facilitators)

**If you've never used a terminal before, this section is for you.**

The terminal (also called "command line" or "shell") is a text interface to your computer. Instead of clicking, you type commands.

### Opening the Terminal

**Mac:** Press `Cmd + Space`, type "Terminal", press Enter.

**Windows:** Press `Win + R`, type "cmd", press Enter. (Or use PowerShell or Windows Terminal.)

### Essential Commands

#### 1. Where Am I? (`pwd`)

```bash
pwd
```

This prints your current location (folder). Example output:
```
~/Documents
```

#### 2. What's Here? (`ls`)

```bash
ls
```

Lists files and folders in your current location. Example:
```
Documents  Downloads  Desktop
```

#### 3. Move to a Folder (`cd`)

```bash
cd Documents
```

"Change directory" — moves you into the `Documents` folder.

**Going back up:**
```bash
cd ..
```

The `..` means "parent folder."

**Going to a specific path:**
```bash
cd ~/Documents/Projects/gym-starter
```

#### 4. Tab Completion (Your Best Friend)

Instead of typing full folder names, type the first few letters and press `Tab`.

```bash
cd Doc[TAB]
```

The terminal auto-completes to `Documents/`. If there are multiple matches, press Tab twice to see options.

**This saves time and prevents typos.**

### Permission Prompts

When you see something like:

```
Claude Code wants to edit files in this directory. Allow? [y/n]
```

**This is normal.** Claude Code is asking for permission to make changes. Type `y` and press Enter to allow.

Similarly, when installing tools:

```
Do you want to continue? [Y/n]
```

Type `Y` (or just press Enter) to proceed.

### Common Terminal Mistakes

| Mistake | What Happened | Fix |
|---------|---------------|-----|
| "Command not found" | Tool isn't installed or not in PATH | Reinstall the tool |
| "No such file or directory" | Wrong folder | Use `pwd` to check location, then `cd` to correct folder |
| "Permission denied" | Need admin rights | Try `sudo` before the command (Mac/Linux) |
| Nothing happens | Command is running | Wait, or press `Ctrl+C` to cancel |

### Practice Before the Workshop

Try these commands:

```bash
# See where you are
pwd

# List what's here
ls

# Make a test folder
mkdir test-folder

# Go into it
cd test-folder

# Create an empty file
touch hello.txt

# Go back up
cd ..

# Delete the test folder
rm -r test-folder
```

**If you can do this, you're ready for the workshop.**

---

## Troubleshooting Common Issues

### "npm install is really slow"
- Try using a different WiFi network
- Consider installing packages at home before the workshop

### "GitHub says 'Permission denied (publickey)'"
- Your SSH key isn't set up correctly
- Follow the SSH setup guide above, or use HTTPS authentication instead

### "Claude Code isn't responding"
- Make sure you're logged into your Claude account
- Check that your API key is valid (if using API mode)
- Restart Claude Code

### "I don't have admin privileges on my laptop"
- Contact your IT team at least 1 week before the workshop
- They may need to pre-install Node.js, Git, and VS Code

---

## Still Stuck?

**Email the workshop facilitator at [email] at least 3 days before the workshop.**

Include:
- What you tried
- What error message you saw
- Screenshots (if applicable)

We can't troubleshoot on workshop day, so reach out early.

---

## Confirm You're Ready

**2 days before the workshop, reply to the facilitator email (or fill the provided form) with:**

> "I completed the prerequisites checklist. All verification commands pass."

This helps us:
- Know who might need extra support
- Plan helper assignments
- Avoid surprises on workshop day

If you're stuck on any step, this is your deadline to ask for help.

---

## Summary: What Success Looks Like

By the end of this checklist, you should be able to:

✅ Run `node --version` and see v18+
✅ Run `git --version` and see output
✅ Run `gh --version` and see output
✅ Run `claude --version` and see output
✅ Log into GitHub, Vercel, and Claude
✅ Create a folder, run `npm install`, and start a dev server
✅ Push code to GitHub and deploy to Vercel

**If you can do all of this, you're ready. See you at the workshop!**

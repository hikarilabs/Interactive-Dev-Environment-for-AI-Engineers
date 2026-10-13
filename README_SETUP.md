# Getting started

You'll do everything in one app: **VS Code**. Install it first, like any other app. From then on, every command goes into the terminal *inside* VS Code, so the steps are the same on Mac and Windows.

It takes about 15 minutes. You can run the setup again at any time: anything already done is skipped.

## 1. Install VS Code

Download it from **[code.visualstudio.com/download](https://code.visualstudio.com/download)**.

**Mac**
1. Open the downloaded file. You get **Visual Studio Code**.
2. Drag it into your **Applications** folder. This matters: if it runs from Downloads, updates and the `code` command don't work.
3. Open it from Applications. If macOS asks whether to open an app downloaded from the internet, click **Open**.

**Windows**
1. Run the installer and accept the defaults. Keep **Add to PATH** ticked (it is by default).
2. On the last screen, leave **Launch Visual Studio Code** ticked and click **Finish**.

**Linux:** use the `.deb` (Ubuntu, Debian) or `.rpm` (Fedora) download.

## 2. Open the terminal inside VS Code

In the menu bar choose **Terminal → New Terminal**. A panel opens at the bottom of the window.

Look at the start of the line in that panel to know which command to use in the next step:

| You see                                             | You're on    | Use                       |
|:----------------------------------------------------|:-------------|:--------------------------|
| A line starting with `PS`, e.g. `PS C:\Users\ana>`  | Windows      | the **Windows** command   |
| A line ending in `%` or `$`, e.g. `ana@MacBook ~ %` | Mac or Linux | the **Mac/Linux** command |

> **Windows:** if the panel says `bash` instead, click the small arrow next to the **+** at the top right of the panel and choose **PowerShell**.

## 3. Run the setup

Copy the command relevant to your operating system, paste it into the terminal (**Cmd+V** on Mac, **Ctrl+V** on Windows) and press **Enter**.

**Mac/Linux**
```bash
mkdir -p ~/ai-eng && curl -fsSL https://raw.githubusercontent.com/<ORG>/<REPO>/main/setup.sh -o ~/ai-eng/setup.sh && bash ~/ai-eng/setup.sh
```

**Windows**
```powershell
mkdir -Force $HOME\ai-eng | Out-Null; irm https://raw.githubusercontent.com/<ORG>/<REPO>/main/setup.ps1 -OutFile $HOME\ai-eng\setup.ps1; powershell -ExecutionPolicy Bypass -File $HOME\ai-eng\setup.ps1
```

The setup goes through the course's tools one by one. For each one, it checks whether you already have it and installs or fixes it only if needed:

| Tool                     | What it's for                                                                                                                       |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| Git                      | Saves versions of your work and talks to GitHub                                                                                     |
| uv and Python            | Runs Python and installs each project's packages. Any Python from 3.12 to 3.14 you already have is fine; otherwise it installs 3.13 |
| nvm and Node.js 22       | Runs JavaScript tools and web front ends                                                                                            |
| Claude Code              | Your AI coding assistant in the terminal                                                                                            |
| VS Code's `code` command | Opens a folder in VS Code from the terminal                                                                                         |

Anything it installs goes into a folder called **`ai-eng`** in your home folder, so nothing is scattered around your computer. Tools you already have are kept, not installed twice.

It asks you a few things along the way:

* **Mac:** whether you want Homebrew. It's optional: press **Enter** to skip it.
* **Everyone:** your name and email for Git.
* **Everyone:** to add your computer's key to GitHub. It copies the key and opens the right GitHub page for you.

Each line of the output shows one of:

|          | Meaning                                                |
|:---------|:-------------------------------------------------------|
| `[ OK ]` | Already working, nothing to do                         |
| `[DONE]` | Just installed or fixed                                |
| `[ -- ]` | Optional and skipped. That's fine                      |
| `[WARN]` | Works, but worth a look. Follow the `->` hint under it |
| `[FAIL]` | Needs fixing. Follow the `->` hint under it            |

## 4. Load the tools into your terminal

The setup doesn't add the tools to every terminal automatically. You load them when you want them, and closing the terminal unloads them again, so nothing lingers on your computer that you didn't ask for. Run this in the terminal:

**Mac/Linux**
```bash
source ~/ai-eng/env.sh
```

**Windows**
```powershell
. $HOME\ai-eng\env.ps1
```

Do this in **each new terminal** you use for course work. If a command such as `uv`, `node` or `claude` says *not found*, this step was missed.

The one exception is VS Code's `code` command, which opens a folder in VS Code. It's set up once and works in every new terminal.

## 5. Check that everything works

Run the setup again with **check**. It only looks and changes nothing:

**Mac/Linux**
```bash
bash ~/ai-eng/setup.sh --check
```

**Windows**
```powershell
powershell -ExecutionPolicy Bypass -File $HOME\ai-eng\setup.ps1 -Check
```

You want to see **All good**. Anything else:

* **Most problems:** run the setup again without `--check`. It's safe to repeat: it skips what's done and retries the rest.
* **A hint says to open a new terminal:** choose **Terminal → New Terminal**, then load the tools again (step 4).
* **Still stuck?** The setup copies a report to your clipboard. Paste it into the course help channel. It's also saved in `ai-eng/setup-report.txt`, with full details in `ai-eng/setup.log`.

> **API keys** (OpenAI, Anthropic) aren't part of this setup: each project keeps its own in a `.env` file. See [API keys](API_KEYS.md).

## Using PyCharm or another JetBrains IDE instead

Everything works the same way because JetBrains IDEs have a built-in terminal too. Only step 2 differs: open the terminal with **View → Tool Windows → Terminal** (or **Alt+F12**, **⌥F12** on Mac).

The setup notices when it runs inside a JetBrains IDE, so it won't complain that VS Code is missing.

The rest of the course guides show VS Code screens. JetBrains IDEs have their own equivalents for notebooks and Claude Code.
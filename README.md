<p align = "center" draggable="false" ><img src="https://github.com/AI-Maker-Space/LLM-Dev-101/assets/37101144/d1343317-fa2f-41e1-8af1-1dbb18399719" 
     width="200px"
     height="auto" alt=""/>
</p>


## <h1 align="center" id="heading">:wave: Interactive Dev Environment (IDE) for AI Engineers </h1>

<p align="center">
  <img src="images/ai_engineer_at_workstation.jpg" alt="AI Engineer Setting Up Dev Env" width="350" />
</p>

### <h3 align="center"> Getting Started 🏗️ Building, 🚢 Shipping, and 🚀 Sharing Production LLM Applications!!

🛣️ Welcome to the beginning of your journey to become an AI Engineer! 

This tutorial is designed to guide you through the process of setting up your Interactive Development Environment (IDE) to align with best practices at [The LLM Edge](https://newsletter.aimakerspace.io/)!

### 🤖 AI Editors Supported 
* [Visual Studio Code](https://github.com/microsoft/vscode)
* [Claude Code](https://claude.com/download)

Note: If you prefer Cursor, Codex, or another tool, then you'll be on your own in terms of debugging.


### 🖥️ Operating Systems Supported
* Windows
* Linux (Debian/Ubuntu)
* macOS Intel
* macOS Apple Silicon

<p></p>

## How To Get Started

You will be using only one application throughout the entire setup and AI Makerspace courses – **VS Code**. First, install VS Code as you would any other application. Once installed, all future commands will be entered into the terminal *within* VS Code; therefore, the process will be identical on both Macs and Windows. It should take approximately 15 minutes to complete the installation.

At any point during the course, you can re-run the setup; however, anything that has already been completed will be skipped.

## 1. Install VS Code

Download VS Code from **[code.visualstudio.com/download](https://code.visualstudio.com/download)**.

### Mac
1. Open the downloaded file. You will now have **Visual Studio Code**.
2. Move **Visual Studio Code** into your **Applications** folder. This is important: if you run VS Code from your Downloads folder, you will not receive updates and the `code` command will not function correctly.
3. Open VS Code from your Applications folder. If macOS asks you if you wish to open an application downloaded from the internet, select **Open**.

### Windows
1. Run the installer and accept all default settings. Ensure that the option to **Add to PATH** remains checked (it is checked by default).
2. On the final screen, leave the option to **Launch Visual Studio Code** checked and click **Finish**.

### Linux:
Use either the `.deb` (Ubuntu, Debian) or `.rpm` (Fedora) download options.

## 2. Open Terminal Within VS Code

In the top menu bar, select **Terminal → New Terminal**. A panel will appear at the bottom of the window.

To determine which command to use in the following step, examine the beginning of the line in that panel:

| If you see...                                            | You are on... | Use...                    |
|----------------------------------------------------------|---------------|---------------------------|
| A line beginning with `PS`, such as `PS C:\Users\ana>`   | Windows       | The **Windows** command   |
| A line ending with `%` or `$`, such as `ana@MacBook ~ %` | Mac/Linux     | The **Mac/Linux** command |

> **Windows:** If the panel displays `bash` instead of `PS`, click the small arrow next to the **+** symbol at the top right of the panel and select **PowerShell**.

## 3. Run Setup

Copy the appropriate command for your operating system and paste it into the terminal (**Cmd+V** on Mac, **Ctrl+V** on Windows). Press **Enter**.

### Mac/Linux
```bash
mkdir -p ~/ai-eng && curl -fsSL https://raw.githubusercontent.com/<ORG>/<REPO>/main/setup.sh -o ~/ai-eng/setup.sh && bash ~/ai-eng/setup.sh
```

### Windows
```powershell
mkdir -Force $HOME\ai-eng | Out-Null; irm https://raw.githubusercontent.com/<ORG>/<REPO>/main/setup.ps1 -OutFile $HOME\ai-eng\setup.ps1; powershell -ExecutionPolicy Bypass -File $HOME\ai-eng\setup.ps1
```

The setup script will go through each tool used in this course one by one. For each tool, it will check if you already have it installed and will only install or fix it if necessary:

| Tool                     | Purpose                                                                                                                                                          |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Git                      | Saves versions of your work and communicates with GitHub                                                                                                         |
| uv and Python            | Runs Python and installs each project's packages. Any version of Python from 3.12 to 3.14 that you currently have is acceptable; otherwise, it will install 3.13 |
| nvm and Node.js 22       | Runs JavaScript tools and web front ends                                                                                                                         |
| Claude Code              | Your AI coding assistant in the terminal                                                                                                                         |
| VS Code's `code` command | Opens a directory in VS Code from the terminal                                                                                                                   |

All tools installed by the setup script will be placed in a directory named **`ai-eng`** located in your home directory; thus, none of these tools will be scattered across your computer. Tools you already have installed will not be installed again.

During the setup process, you may be asked several questions:

* **Mac:** Do you want Homebrew? This is optional: press **Enter** to skip.
* **Everyone:** What is your name and email address for Git?
* **Everyone:** Would you like to add your computer's key to GitHub? The setup script will copy the key and open the correct GitHub page for you.

Each line of output produced by the setup script will indicate one of the following:

| Output   | Indication                                                                                                 |
|----------|------------------------------------------------------------------------------------------------------------|
| `[ OK ]` | Tool is already installed and working; no action needed                                                    |
| `[DONE]` | Tool was just installed or fixed                                                                           |
| `[ -- ]` | Tool is optional and was skipped; this is acceptable                                                       |
| `[WARN]` | Tool is installed and working; however, there is an issue worth reviewing. Refer to the `->` hint below it |
| `[FAIL]` | Tool requires fixing; refer to the `->` hint below it                                                      |

## 4. Load Tools Into Your Terminal

The setup script does not automatically add the tools to every terminal. Instead, you load them when needed; once you close the terminal, they are unloaded again. This prevents unwanted tools from remaining on your computer. To load the tools into your terminal, execute the following command:

### Mac/Linux
```bash
source ~/ai-eng/env.sh
```

### Windows
```powershell
. $HOME\ai-eng\env.ps1
```

Execute this command in **every new terminal** you use for coursework. If a command such as `uv`, `node` or `claude` results in an error message stating *not found*, then this step was skipped.

The only exception to this rule is VS Code's `code` command which opens a directory in VS Code. This is configured once and will work in every new terminal.

## 5. Verify Everything Works Correctly

To verify that everything is working correctly, run the setup script again using **check**. This will only verify that everything is correct and will not make any changes:

### Mac/Linux
```bash
bash ~/ai-eng/setup.sh --check
```

### Windows
```powershell
powershell -ExecutionPolicy Bypass -File $HOME\ai-eng\setup.ps1 -Check
```

Ideally, you want to see **All good**. If you see anything else:

* **Most issues:** Run the setup script again without `--check`. It is safe to repeat this process: it will skip what has been completed and attempt what remains.
* **A hint indicates to open a new terminal:** Select **Terminal → New Terminal**, then load the tools again (Step 4).
* **Still experiencing issues?** The setup script will copy a report to your clipboard. Paste this report into the course help channel. Additionally, a copy of this report is saved in `ai-eng/setup-report.txt`, with complete details in `ai-eng/setup.log`.

## Using PyCharm Or Another JetBrains IDE Instead

All aspects of this process are identical regardless of whether you use PyCharm or another JetBrains IDE since JetBrains IDEs also include a built-in terminal. Only Step 2 differs: open the terminal using **View → Tool Windows → Terminal** (or **Alt+F12**, **⌥F12** on Mac).

The setup script detects when it runs within a JetBrains IDE; therefore, it will not indicate that VS Code is missing.

All later guides provided in this course illustrate screens from VS Code. JetBrains IDEs have their own equivalents for notebooks and Claude Code.

## Build Your First LLM Application

Now that you've completed your IDE set-up, head on over to the [The-AI-Engineer-Challenge](https://github.com/AI-Maker-Space/The-AI-Engineer-Challenge) repository to build your first LLM application!

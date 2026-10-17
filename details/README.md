

## Basic Concepts and Code

We will be using a few core tools in our stack such as a `terminal`, `Command Line Interface (CLI)`, `git`, `uv`, and `claude`.
<details>
<summary>Terminal and Command Line Interface </summary>

We use both a terminal and a Command Line Interface (CLI) to develop AI applications with open-source tools. This is true regardless of the operating system.

A terminal is a software application like macOS Terminal or Windows Terminal that gives you a window where you type text-based commands and receive text-based output.

A Command Line Interace (CLI) refers to the environment or shell (e.g., Bash, Zsh, PowerShell, etc.) that interprets your text commands. The CLI is the program that actually runs commands and processes input/output; it just happens to run inside a terminal application (or emulator).

Here is a quick review of some of the terminal commands that you should know. It's important to understand both syntax and what they do! 

| Command                                     | Stands For            | Description                                                                                |
|---------------------------------------------|-----------------------|--------------------------------------------------------------------------------------------|
| `ls`                                        | long listing          | lists all files and directories in the present working directory                           |
| `ls -a`                                     | long listing all      | lists hidden files as well                                                                 |
| `cd {dirname}`                              | change directory      | to change to a particular directory                                                        |
| `cd ~`                                      | change directory home | navigate to HOME directory                                                                 |
| `cd ..`                                     | change directory up   | move one level up                                                                          |
| `cat {filename}`                            | concatenate           | displays the file content                                                                  |
| `sudo`                                      | superuser             | allows regular users to run programs with the security privileges of the superuser or root |
| `mv {filename} {newfilename}`               | move                  | renames the file to new filename                                                           |
| `clear`                                     | clear                 | clears the terminal screen                                                                 |
| `mkdir {dirname}`                           | make directory        | create new directory in present working directory or at specified path                     |
| `rm {filename}`                             | remove                | remove file with given filename                                                            |
| `touch {filename}.{ext}`                    | touch                 | create new empty file                                                                      |
| `rmdir {dirname}`                           | remove directory      | deletes a directory                                                                        |
| `ssh {username}@{ip-address} or {hostname}` | secure shell          | login into a remote Linux machine using SSH                                                |

</details>

<details>
<summary>Git</summary>

Git is a free and open source distributed version control system designed to handle everything from small to very large projects. These are the commands we will be using with `git`:

`git clone` -> clone a remote repository to your local computer

`git add` -> add files to a commit

`git commit -m {message}` -> commit changes with a message

`git push` -> push commit to remote repository
</details>

<details>
<summary>uv</summary>

uv is an extremely fast Python package manager and virtual environment management tool, written in Rust. uv aims to be a drop-in replacement for pip and pip-tools, providing significantly improved performance. We will use `uv` to manage both our package installations and virtual environments.

Some common `uv` commands:

`uv init` -> Initializes a new Python project and generates a `pyproject.toml`.

`uv add <package-name>` -> Adds a package dependency to `pyproject.toml`.

`uv run python your_script.py` -> Runs a Python script inside the project environment without requiring manual activation.

Note: In most AIM repositories, the required dependencies are already defined in `pyproject.toml`, so you typically will not need to run `uv init` or `uv add` unless you are modifying or extending the project.

Optional: 

`uv venv .venv -p 3.11` -> Creates a virtual environment in `.venv` using Python 3.11.

`source .venv/bin/activate` -> Activates the virtual environment for your current shell session. This is optional if you use `uv run`.

</details>

<p></p>

## :rocket: Let's Get Started! 
Let's start off by setting up our environment!  Review the environment setup instructions for the local environment that you'll be using in this course.
<details>
  <summary>Windows</summary>


* Install [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install) using Powershell

```powershell
wsl --install
```
* Install [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab) (You can even make it your [default!](https://devblogs.microsoft.com/commandline/
windows-terminal-as-your-default-command-line-experience/))

* Install [Ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9pdxgncfsczv?activetab=pivot:overviewtab)

* Make sure you've installed the correct version with the command `wsl -l -v`
    
(If you find yourself getting stuck on the WSL2 install, [here](https://www.youtube.com/watch?v=VMZH9Pj2dXw&ab_channel=StefanRows) is a link to video instructions)

Give it a test drive! 

![WindowsTerminal](https://user-images.githubusercontent.com/72572922/160048214-37f08855-8b29-4c13-9d25-e0f69806f752.jpg)

Continue by installing the following tools using [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab) to set up your environment.

| Tool                                      | Purpose                 | Command                                                                |
|:------------------------------------------|:------------------------|:-----------------------------------------------------------------------|
| :snake: **uv** (installed in WSL2)        | Python Package Manager  | `curl -LsSf https://astral.sh/uv/install.sh \| sh && source ~/.bashrc` |
| :octocat: **Git** (installed in WSL2)     | Version Control         | `sudo apt update && sudo apt upgrade` <br> `sudo apt install git-all`  |
| :memo: **VS Code** (installed in Windows) | Development Environment | [Download](https://code.visualstudio.com/download)                     |
| :memo: **Cursor**                         | Development Environment | [Download](https://www.cursor.com/downloads)                           |

</details>

<details>
  <summary>Linux (Debian/Ubuntu)</summary>

Open the terminal using <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>T</kbd>. Enter the following commands in terminal to setup your environment.
| Tool | Purpose | Command                                                                                           |
| :-------- | :-------- | :------------------------------------------------------------------------------------------------ |
| :snake: **uv**  | Python Package Manager | `curl -LsSf https://astral.sh/uv/install.sh | sh` <br> `source ~/.bashrc` |
| :octocat: **Git**  | Version Control | `sudo apt update && sudo apt upgrade` <br> `sudo apt install git-all`   |
| :memo: **VS Code** | Development Environment | [Download](https://code.visualstudio.com/download) |
| :memo: **Cursor** | Development Environment | [Download](https://www.cursor.com/downloads) |

</details>

<details>
  <summary>macOS Intel</summary>

To get started, we need to download the MacOS package manager, <strong>Homebrew</strong> :beer:, so that we can download the tools we'll be using in the course. If you don't already have Homebrew installed, run the following commands:

1. Open the terminal using <kbd>⌘</kbd>+<kbd>Space</kbd> and type `terminal`.

2. Install Homebrew using the command below, following the command prompts:

    `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` 

3. Update Homebrew (This may take a few minutes)

    `git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core fetch --unshallow`

    `git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask fetch`
     
4. Install the `wget` command to continue following along
     `brew install wget`

Enter the following commands in the terminal to set up your environment.

| Tool               | Purpose                 | Command                                            |
|:-------------------|:------------------------|:---------------------------------------------------|
| :snake: **uv**     | Python Package Manager  | `curl -LsSf https://astral.sh/uv/install.sh        | sh` <br> `source ~/.bashrc` |
| :octocat: **Git**  | Version Control         | `brew install git`                                 |
| :memo: **VS Code** | Development Environment | [Download](https://code.visualstudio.com/download) |
| :memo: **Cursor**  | Development Environment | [Download](https://www.cursor.com/downloads)       |

</details>

<details>
  <summary>macOS Apple Silicon</summary><br>

To get started with uv on Apple Silicon, we'll install it directly with our terminal.

Open terminal using <kbd>⌘</kbd>+<kbd>Space</kbd> and type `terminal`. Enter the following commands in terminal to setup your environment.

First, let's install Homebrew if you don't already have it installed:

1. Install Homebrew using the command below, following the command prompts:

    `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"` 

2. Update Homebrew (This may take a few minutes)

    `git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-core fetch --unshallow`

    `git -C /usr/local/Homebrew/Library/Taps/homebrew/homebrew-cask fetch`
     
3. Install the `wget` command to continue following along
     `brew install wget`

4. Install the `xcode-select` command-line utilities by typing the following command in the terminal

    `xcode-select --install`

Now let's install uv and other tools:

| Tool               | Purpose                 | Command                                            |
|:-------------------|:------------------------|:---------------------------------------------------|
| :snake: **uv**     | Python Package Manager  | `curl -LsSf https://astral.sh/uv/install.sh        | sh` |
| :octocat: **Git**  | Version Control         | `brew install git`                                 |
| :memo: **VS Code** | Development Environment | [Download](https://code.visualstudio.com/download) |
| :memo: **Cursor**  | Development Environment | [Download](https://www.cursor.com/downloads)       |

</details>


<p></p>


## 🧑‍💻 Let's configure our VS Code environment!

<details>
  <summary>Install the Python and Jupyter Notebook Extensions</summary>

  1. Click the `Extensions` <img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/f17d8f45-f174-4b9b-be92-8f1e85d8a77b" width=30px/> tab on the left side of the window.

  2. Type "Python" in the search bar.

  3. Click `Install` <img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/4c06f2a7-d7c3-4c59-b656-82170518cbeb" width=30px/>  on the <ins><strong>Python</strong></ins> extension

  4. Then, type "Jupyter" in the search bar.

  5. Click `Install` <img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/4c06f2a7-d7c3-4c59-b656-82170518cbeb" width=30px/>  on the <ins><strong>Microsoft Jupyter Notebook Extension</strong></ins>

</details>

<details>
  <summary>Set the Python Interpreter</summary>

  1. Open Cursor (or VS Code) and click on `New File...`

  2. Open the Command Pallette 
    <strong>(Mac: </strong></ins> <kbd>Shift</kbd><kbd>⌘</kbd>+<kbd>P</kbd> 
    ,<strong> Windows: </strong></ins> <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>)

  3. Type "Python" in the search bar.

  4. Click on `New Python File`

  5. Open the Command Pallette again.  Can you remember the shortcut?  If    not, see #2 above again.

  6. Type "Python Interpreter".

  7. Click on `Python: Select Interpreter`

  8. Select the Python environment that was created by uv.
  
  <p align = "center" draggable="false">
  <img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/d95ff119-2c97-4bf8-9133-1bf167f61f6e" alt=""> 
  </p>

  9. Now you're ready to start coding!

</details>

<p> </p>


## 🔑 Setting Up Keys and Tokens

<details>



     
  <summary>Generating a GitHub Access Token</summary>
     
**Create an account with GitHub [here](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home) if you do not have one.**

Navigate to [GitHub's Developer Token settings](https://github.com/settings/tokens).
Click on `Generate new token` > `Generate new token (classic)`
![Screenshot 2023-08-30 at 8 16 58 PM](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/d6f57901-6e69-42e5-a22c-37b48ff6e3fc)

Give the token a description, set the expiration (we recommend 90 days), and check every box. When you're done, click `Generate token` at the bottom of the page. 

![Screenshot 2023-08-30 at 8 36 14 PM](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/451bad7b-ec8a-4429-a5bb-8d0212d00f50)

Copy the access token and save it for later use. We will use this token to interact with GitHub. Please do not lose this access token or you will need to generate a new one.

![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/f98c9644-e44b-4fd3-8590-db513bef6360)

</details>


<details>
  <summary>Generating an OpenAI API key</summary>
     
**Create an account with OpenAI [here](https://platform.openai.com/signup) if you do not have one.**

Navigate to [OpenAI's API Developer settings](https://platform.openai.com/account/api-keys) and click on `+ Create new secrete key`.
![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/b6179d51-76ac-42a8-8304-39f8b5c9a8c8)

Name your key and click `Create secret key`
![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/be0ea05f-59d3-4d20-939d-b402e3d4bbb2)

Copy the key and save it for later use. We will use this key several times in deploying projects. Please do not lose this key or you will need to generate a new one

![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/cfaec5fa-5380-4aca-a6ae-6c14c8db6789)

We recommend your run through our [OpenAI Notebook](https://colab.research.google.com/drive/16Y67VozkGVErtrF3WQArpM52AOk5pBGu?usp=sharing#scrollTo=3qCKaH6vD-jZ) to learn how to utilize the OpenAI API.
</details>

<details>
  <summary>Generating a Claude API key</summary>

**Create an account with Claude AI (anthropic.com) [here](htttps://console.anthropic.com) if you do not have one.**

  Navigate to [Anthropic's Dashboard](https://console.anthropic.com/dashboard) and click on `Get API keys`
  _NOTE: If you have not purchased credits yet, it will require you to purchase at least $5.00 worth before continuing._
  ![Claude Actions](/images/claude_actions.png)

  Enter a key name (or accept the default) and click on `Create API Key`
  ![Claude Create API Key](/images/claude_create_api_key.png)

  Click the `Copy` button and save the key somewhere that is secure. We will use this key several times in deploying projects. As stated in the modal, _Keep a record of your API key, you wont be able to view it again._

![Claude Save API Key](/images/claude_save_api_key.png)

  If you want to test the api key first, copy the example code and paste it into a terminal. The results will look something like this:
  ![Claude API Key Test Results](/images/claude_api_key_test_results.png)

</details>

## <img src="https://octodex.github.com/images/original.png" width=40px/> Let's Make Sure That GitHub is Ready to Roll!

<details>
  <summary>Github SSH Setup</summary>
  Secure Shell Protocol (SSH) provides a secure communication channel of an unsecured network.  Let's set it up!
  
  <p></p>

  1. Generate a Private/Public SSH Key Pair.
    
  ```console
  ssh-keygen -o -t rsa -C "your email address for github"
  ```

  2. Save file pair.  Default location `~/.ssh/id_rsa` is fine! 
  

  3. At the prompt, type in a secure passphrase.
  4. Copy the contents of the public key that we will share with GitHub. 

     * Mac: `pbcopy < ~/.ssh/id_rsa.pub` 

     * Windows (WSL): `clip.exe < ~/.ssh/id_rsa.pub`

     * Linux: `xclip -sel c < ~/.ssh/id_rsa.pub`
  
  5. Go to your GitHub account and go to `Settings`. 
  
  6. Under `Access`, click on the `SSH and GPG keys` tab on the left.

  ![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/5fb54f16-7279-49c4-bda3-2da36cbbc306)


  7. Click on the `New SSH Key` button.
  
  ![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/d5551c28-9d70-438c-b45d-43698384e3ff)

  
  8. Name the key, and paste the public key that you copied. Click the `Add SSH Key` button
  

  ![image](https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/8f7c4496-0e88-4058-9baf-73495322db8b)


</details>


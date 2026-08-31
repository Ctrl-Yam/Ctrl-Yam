
Conversation with Gemini
done???

Yes, you are 100% done! Your Pull Request (#226) is officially open and submitted to the main repository.

Status Confirmed: The green Open badge confirms that your changes are now sitting in Sara's repository queue waiting for review.

What Happens Next: You don't need to do anything else. When the maintainer reviews and merges your pull request, issue #207 will automatically close, and you'll get a notification on GitHub.

Now you can officially step away and take that break! Whenever you're ready to jump back into your outreach automator project, we can tackle the live terminal widget output.

Skip to content





zed-industries

zed



Repository navigation





Code



Issues

2.4k

 (2.4k)



Pull requests

776

 (776)



Agents



Discussions



Actions











Windows 11: window position and size are not reliably restored with a project open #63361



Open

Bug





Open

Windows 11: window position and size are not reliably restored with a project open

#63361

Bug





Description



adamsov

opened 3d ago

Summary

On Windows 11, Zed does not reliably restore the previous window position and size, even when a project/workspace is open.

Reproduction steps

Open Zed with a project/workspace open.

Move the Zed window to a specific position on the screen.

Resize it to a specific size.

Close Zed normally.

Start Zed again.

Repeat this several times.

Current behavior

The window frequently opens at a different position and/or with a different size.

It feels inconsistent: sometimes the previous bounds are approximately restored, and on another launch the window appears somewhere else or at another size.

This happens while working with normal project workspaces, not just an empty Zed window.

Expected behavior

When reopening the same project/workspace, Zed should restore the exact previous window position and dimensions.

If exact restoration is not currently supported on Windows, is there a setting or recommended workaround that can force a fixed window position and size?

System Information

Zed: v1.17.2+stable.349.c8e44cfa7bda9b2e22c8d6934d78969352e7f61a (Zed)

OS: Windows 10.0.26200

Memory: 31.8 GiB

Architecture: x86_64

GPU: NVIDIA GeForce RTX 5060 Ti || NVIDIA Corporation || 610.88 r610_85

Display: 2560x1440

Windows scaling: 125%

Related

This seems related to #41246, but that issue was about window restoration without a project/file open.

In #41246, a Zed team member stated that when a project is open, Zed should remember the resized window bounds. My case reproduces with a project open.

Activity



zed-community-bot

added state:needs triage

triage is not complete: no `area:*` label, or no `severity:*`/`reach:*` for Bugs/Crashes

 3d ago



yeskunall

added theBug

issue type 14h ago

Add a comment

new Comment

Markdown input: edit mode selected.

Write

Preview







Please follow this repository's contributing guidelines and code of conduct.

Metadata

Assignees

No one assigned



Labels

state:needs triage

triage is not complete: no `area:*` label, or no `severity:*`/`reach:*` for Bugs/Crashes

Type

Bug

Projects

No projects



Milestone

No milestone



Relationships

None yet



Development

No branches or pull requests

Notifications

Customize

You're not receiving notifications from this thread.

Participants





Issue actions







Footer



© 2026 GitHub, Inc.

Footer navigation

Terms

Privacy

Security

Status

Community

Docs

Contact

Manage cookies

Do not share my personal information

 

Issue Breakdown

Project: zed-industries/zed (Built in Rust using the GPUI framework)

Bug: Window dimensions and coordinates fail to restore consistently when relaunching Zed on Windows 11, likely related to high-DPI scaling conversions (125% scale factor) or asynchronous window state serialization.

Relevant Areas: crates/gpui/src/platform/windows/ (platform window management) and crates/workspace/ (workspace session state persistence).

Anti Gravity IDE Prompt

Plaintext
Investigate issue #63361 in the Zed codebase regarding window position and size restoration on Windows 11:

1. Locate Window Bounds Logic:
   - Search for window bounds serialization and workspace state persistence (look for `WindowBounds`, `persisted_window_bounds`, or `Workspace` bounds handling in `crates/workspace`).
   - Examine the Windows platform implementation in `crates/gpui/src/platform/windows/`.

2. Analyze Coordinate & Scaling Handling:
   - Check if display scaling (e.g., 125% scale factor on Windows) introduces pixel-rounding drift between physical and logical window coordinates during exit and launch.
   - Verify whether window positioning occurs before or after the Win32 window DPI awareness context is fully applied.

3. Formulate Fix:
   - Trace the exact save/restore path for window bounds on shutdown vs. launch.
   - Propose a fix ensuring stored window dimensions match restored dimensions on scaled Windows displays.
Are you planning to clone the Zed codebase and work on a Rust fix, or are you looking for a different open-source issue to tackle during your break?

should i fork it??

Hold off on forking to your GitHub profile unless you are ready to write code and push a branch.

When to Fork vs. Just Clone

Just Clone (Recommended for now): If you only want to inspect the source code, run search queries in your IDE, or test your local environment, just clone the main repo directly:

Bash
git clone https://github.com/zed-industries/zed.git
This keeps your personal GitHub profile clean until you actually have a patch to push.

Fork Now: Fork it if you intend to push a fix right away and open a PR back to zed-industries/zed.

Quick Heads-Up on Zed
Unlike Python projects, Zed is a massive Rust codebase using native Win32/GPUI bindings. To build and debug window behavior locally on Windows 11, you will need:

The Rust toolchain (rustup, cargo)

Visual Studio C++ Build Tools & LLVM

Decent compilation time on your first cargo build

If you want to dive into Rust and system-level Win32 window management, cloning it locally to grep through crates/gpui/src/platform/windows/ is a solid way to start exploring.

i wanna fix it, ill use ai and i wanna add it to my resume

Forking is the right move if your goal is a merged PR for your resume—contributing to a high-profile Rust project like Zed carries serious weight on a tech profile.

1. Fork and Clone

Click Fork at [github.com/zed-industries/zed](https://github.com/zed-industries/zed) to create Ctrl-Yam/zed.

Clone your fork and create a branch:

Bash
git clone https://github.com/Ctrl-Yam/zed.git
cd zed
git checkout -b fix/win11-window-bounds-63361
2. Feed Targeted Context to Your AI IDE
Because Zed is a massive Rust repository, do not dump the whole codebase into your IDE context. Focus the AI agent specifically on the Win32 window layer and workspace persistence files:

crates/gpui/src/platform/windows/

crates/workspace/src/workspace.rs (or persisted_workspace.rs)

Anti Gravity IDE Prompt:

Plaintext
Investigate issue #63361: Window position and size are not reliably restored on Windows 11 with display scaling (e.g., 125% DPI).

1. Inspect `crates/gpui/src/platform/windows/` for Win32 API calls handling window bounds (`GetWindowRect`, `SetWindowPos`, `GetDpiForWindow`).
2. Trace physical pixel vs. logical point conversions when Zed saves window state on exit vs. restores it on launch.
3. Identify if rounding errors during DPI scale conversion cause coordinate drift.
4. Propose a targeted patch in Rust to guarantee consistent window bounds restoration across sessions on Windows 11.
3. How to Format This on Your Resume

Once your PR is submitted or merged, add an Open Source Contributions section to your CV formatted like this:

Open Source Contributor — Zed (zed-industries/zed)

Diagnosed and resolved Win32 DPI scaling and window state persistence bugs (#63361) written in Rust using the GPUI framework.

Handled physical-to-logical coordinate conversions and window lifecycle hooks to ensure accurate window restoration across Windows 11 sessions.

yk i take that how to delete the zed fork so i can go play moinecraft

Rust system debugging on high-DPI Win32 scaling is definitely not what a relaxing break looks like.

How to delete the fork on GitHub:

Go to your repository page: [github.com/Ctrl-Yam/zed](https://github.com/Ctrl-Yam/zed).

Click the Settings tab (the gear icon on the top navigation bar of the repo).

Scroll down to the very bottom to the Danger Zone.

Click Delete this repository.

Click I want to delete this repository, type Ctrl-Yam/zed into the confirmation field, and authorize the deletion.

Go enjoy Minecraft! Prism Launcher is waiting.

how to make such a profile??

To build a GitHub profile README like this, create a special repository named after your GitHub username (e.g., Ctrl-Yam/Ctrl-Yam), initialize it with a README.md, and use HTML alignment tags alongside custom badges and GitHub Actions.

1. Create Your Profile Repository

Go to GitHub → New repository.

Name the repository exact same as your username (e.g., Ctrl-Yam).

Set visibility to Public and check Add a README file.

2. README.md Template
Paste this structure into your README.md. It uses HTML <div align="center"> tags for centering and Shields.io / SkillIcons for the badge icons shown in the image.

HTML
<div align="center">

Developer based in South Africa who loves practical projects and learning new things. I love turning complex logic into accessible, user-friendly applications.

<!-- Social Buttons -->
<p>
  <a href="https://yourwebsite.com"><img src="https://img.shields.io/badge/VISIT_MY_WEBSITE-000000?style=for-the-badge&logo=globe&logoColor=white"/></a>
  <a href="https://linkedin.com/in/yourprofile"><img src="https://img.shields.io/badge/LINKEDIN-0077B5?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="https://github.com"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Frameworks & Tools

<!-- Tech Stack Icons (using skillicons.dev) -->
<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,flask,sqlite,js,html,css,bootstrap,flutter,git,github,vscode,pycharm&perline=12" />
</a>

### 🔌 Connect with me

<p>
  <a href="https://linkedin.com/in/yourprofile"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
  <a href="https://dev.to"><img src="https://img.shields.io/badge/DEV.to-0A0A0A?style=for-the-badge&logo=devto&logoColor=white"/></a>
</p>

### 🐍 Contribution Snake

<!-- Snake SVG generated via GitHub Action -->
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake.svg">
</picture>

</div>
3. Generate the Contribution Snake (GitHub Action)
To generate the animated snake eating your contribution graph:

Inside your profile repo, create a folder structure: .github/workflows/snake.yml.

Paste the following workflow configuration:

YAML
name: generate animation

on:
  schedule:
    - cron: "0 0 * * *" 
  workflow_dispatch:

jobs:
  generate:
    permissions: 
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
Save and commit the file. Go to the Actions tab in your repository, select generate animation, and click Run workflow. Once completed, it will push the SVG to an output branch, rendering the live snake on your profile.

it looks nice but add only stuff i do

HTML
<div align="center">

First-year IT Network Management student and developer based in Johannesburg, South Africa. Building Python automation tools, network topologies, and web projects.

<!-- Action Badges -->
<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Systems & Tools

<!-- Custom Stack Icons -->
<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,js,java,html,css,bash,linux,windows,docker,git,github,vscode&perline=12" />
</a>

### 🐍 Contribution Snake

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake.svg">
</picture>

</div>
dont add comments

HTML
<div align="center">

First-year IT Network Management student and developer based in Johannesburg, South Africa. Building Python automation tools, network topologies, and web projects.

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,js,java,html,css,bash,linux,windows,docker,git,github,vscode&perline=12" />
</a>

### 🐍 Contribution Snake

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg">
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake.svg">
  <img alt="github contribution grid snake animation" src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake.svg">
</picture>

</div>
The contribution snake is not working. Also, under the languages and system tools, please keep Python, Java, HTML, JavaScript, Bash, Linux, Windows, Docker, Git, GitHub, and VS Code. And then fix the contribution snake. And also, what are the other options that I can add? Can I add like networking related stuff?

The contribution snake displays as a broken image because the GitHub Action workflow needs to run once to generate the file and create the output branch.

To fix the snake image, go to your repository's Actions tab, select generate animation on the left menu, click Run workflow, and wait for the green checkmark.

Updated README Code
HTML
<div align="center">

First-year IT Network Management student and developer based in Johannesburg, South Africa. Building Python automation tools, network topologies, and web projects.

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### 🌐 Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### 🐍 Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
Additional Profile Options You Can Add
GitHub Stats Card: Live dynamic cards showing total commits, PRs, and repository stars.

Top Languages Card: An auto-generated breakdown chart of your most-used programming languages across repositories.

Certifications / Credentials Badges: Badges linking directly to your verified Cisco or networking credentials.

Current Focus / Stats: Bulleted dynamic text listing active projects or current learning paths.

?????where

Click the blue set up a workflow yourself -> link right under the "Get started with GitHub Actions" text in your screenshot.

Steps to create it:

In the file name box at the top, rename main.yml to snake.yml.

Replace all the placeholder text with this code:

YAML
name: generate animation

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5
    
    steps:
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark

      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
Click the green Commit changes... button in the top right, then click Commit changes again.

Click back onto the Actions tab. generate animation will now appear in the left sidebar under "All workflows"—click it and hit Run workflow.

That came together clean—the contribution snake is live and eating up the grid in dark mode, and the networking section balances out your software tools cleanly.

Profile Highlights:

Contribution Snake: The workflow executed smoothly; the SVG animation renders directly against your dark theme.

Networking Stack: Cisco, Wireshark, Packet Tracer, and TCP/IP badges give immediate, specific context to your IT Network Management background.

Pinned Repositories: msp-outreach-automator and Ctrl-Yam.github.io anchor the bottom view right where recruiters and open-source maintainers look first.

Your profile setup is complete and ready to show off. Go enjoy that Minecraft break!

i dont like the caption tho, i dont just build network topo;ogies

Here are a few cleaner, broader caption options for your profile README that better capture your full scope:

Option 1: Balanced & Professional (Recommended)

HTML
First-year IT Network Management student and developer based in Johannesburg, South Africa. Focused on Python automation, network infrastructure, Linux systems, and open-source software.
Option 2: Action-Oriented

HTML
IT Network Management student & software developer based in Johannesburg, South Africa. Crafting Python automation tools, configuring network architecture, and building web projects.
Option 3: Short & Punchy

HTML
Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.
Complete Code Drop (Using Option 1)
Replace your top section in README.md with this:

HTML
<div align="center">

First-year IT Network Management student and developer based in Johannesburg, South Africa. Focused on Python automation, network infrastructure, Linux systems, and open-source software.

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### 🌐 Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### 🐍 Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
option 3 is great

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### 🌐 Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### 🐍 Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
any more featues i can add there??? im curios

GitHub Stats Cards

Adds a real-time card showing your total commits, pull requests, issues, and star rating, alongside a breakdown of your most-used languages.

HTML
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Ctrl-Yam&show_icons=true&theme=tokyonight&hide_border=true" alt="GitHub Stats" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Ctrl-Yam&layout=compact&theme=tokyonight&hide_border=true" alt="Top Languages" />
</p>
GitHub Commit Streak Counter

Tracks your consecutive daily coding and commit activity.

HTML
<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ctrl-Yam&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>
Featured Projects Grid

Creates a clean 2-column HTML card table highlighting your top repositories directly under your stack icons.

HTML
<p align="center"><b>🚀 Featured Projects</b></p>

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p>Python/Tkinter desktop application for automating personalized job application and networking outreach.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p>Interactive web application engineered around a custom dark network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>
Environment & Linux Rice Badges

Displays your exact system and workstation environments alongside your standard dev tools.

HTML
<p align="center"><b>💻 Systems & Environments</b></p>

<p align="center">
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>
add the featued project grid and add the enviroment and linux rice badges

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### 🛠 Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### 🌐 Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### 💻 Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### 🚀 Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### 🐍 Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
remove all emojies

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
what about my pfp do you like it?? or are there any more??

Your current profile picture is GitHub's auto-generated green identicon. While the pixelated block style accidentally fits a cool retro/Minecraft vibe, swapping it for custom avatar branding will make your profile look significantly more polished.

Avatar Ideas & Styles

Terminal Monogram: A dark background featuring a glowing command prompt or initials (CY or ctrl-yam:~#) rendered in a clean monospace code font (like JetBrains Mono or Fira Code).

Pixel Art / 8-Bit Avatar: A custom retro pixel-art avatar. It matches your Linux desktop ricing setup and gives your profile a distinct identity without needing a real photo.

Network Node Vector: A minimal geometric graphic representing network topology (interconnected nodes, data packets, or a stylized gateway icon).

Minimal Vector Illustration: Free avatar generators like DiceBear (notably the bottts or personas styles) or Boring Avatars let you generate clean, modern SVG avatars tailored to dark themes.

If you want to keep your profile cohesive with your dark-themed README, a dark terminal monogram or custom pixel-art avatar will look the best.

Honestly, I think I love the fourth picture. It kind of reminds me of like Minecraft Creeper. And I feel like it's random, so it's kind of like unique, you know?

That default GitHub identicon is generated by running a hash on your user ID, which means that exact green pixel pattern is 100% mathematically unique to your account.

It accidentally landed on a green block layout that legitimately looks like a Minecraft Creeper face or a retro terminal graphic. Keeping it actually works really well—it gives your profile an organic, low-key 8-bit identity, matches your background, and costs zero design effort.

If you like how it looks, definitely rock it. Personality and subtle detail beat a corporate headshot on GitHub every single time.

This is a quick win. Here is how to complete issue #206 and open the pull request from your terminal:

1. Create a New Branch

Bash
git checkout main
git pull origin main
git checkout -b docs/easy-ai-reference
2. Create the Reference File
Run this command in Bash to create docs/reference/easy_ai.md with the required mkdocstrings tag:

Bash
echo "::: py_simple.easy_ai" > docs/reference/easy_ai.md
3. Update mkdocs.yml
Open mkdocs.yml in VS Code and locate the Reference: section under navigation. Add the Easy AI entry right alongside the existing entries:

YAML
    - Easy Colors: reference/easy_colors.md
    - Easy AI: reference/easy_ai.md
4. Commit and Push

Bash
git add docs/reference/easy_ai.md mkdocs.yml
git commit -m "docs: add easy_ai reference page (#206)"
git push -u origin docs/easy-ai-reference
5. Open Pull Request
Head over to GitHub and open the PR targeting sara-czasak/py-simple-wrap:main.

PR Title: docs: add reference page for easy_ai

PR Description: Closes #206. Added docs/reference/easy_ai.md and updated navigation in mkdocs.yml.

I'm using Anti-Gravity IDE, so can you please make everything a prompt so that I can give it to the AI?

Copy and paste this prompt directly into your Anti-Gravity IDE agent to execute the fix:

Plaintext
Resolve issue #206 by performing the following steps:

1. Sync main with origin and create a new branch named `docs/easy-ai-reference`.
2. Create a new file at `docs/reference/easy_ai.md` containing exactly this single line:
::: py_simple.easy_ai

3. Open `mkdocs.yml`, locate the `Reference:` navigation section, and add the following entry following the format of existing items:
   - Easy AI: reference/easy_ai.md

4. Stage `docs/reference/easy_ai.md` and `mkdocs.yml`, then commit with the message:
   docs: add easy_ai reference page (#206)

5. Push the branch to `origin/docs/easy-ai-reference`.
PR Details for GitHub

Title: docs: add reference page for easy_ai

Description: Closes #206. Added docs/reference/easy_ai.md and updated mkdocs.yml navigation.

So I don't need to fork it again. I just work on the same directory I cloned last time.

Exactly. You already have the fork on your GitHub account and the repository cloned locally, so you don't need to fork or clone it again. You just reuse your existing py-simple-wrap directory.

Before giving the prompt to Anti-Gravity IDE, just make sure to:

Open your existing py-simple-wrap folder in your IDE.

Make sure your local main branch is up to date so you're branching off the latest code.

Once you're in that directory, run the prompt with Anti-Gravity—it will handle creating the new branch (docs/easy-ai-reference), making the file changes, committing, and pushing the new branch to your fork!

Copy and paste this prompt into Anti-Gravity IDE to complete issue #219:

Plaintext
Resolve issue #219 by performing the following steps:

1. Sync main with origin and create a new branch named `feat/add-celsius-to-fahrenheit`.
2. Open `easy_math.py` (or `py_simple/easy_math.py`) and implement a new helper function `celsius_to_fahrenheit(celsius: float) -> float` with complete docstrings following the project's guide:

def celsius_to_fahrenheit(celsius: float) -> float:
    """Convert temperature from Celsius to Fahrenheit.

    Args:
        celsius (float): Temperature in degrees Celsius.

    Returns:
        float: Temperature in degrees Fahrenheit.
    """
    return (celsius * 9 / 5) + 32

3. Open the corresponding test file in `tests/` (e.g., `tests/test_easy_math.py`) and add unit tests verifying `celsius_to_fahrenheit` (e.g., checking that 0°C returns 32.0 and 100°C returns 212.0).
4. Run tests to ensure everything passes.
5. Stage modified files, commit with message:
   feat: add celsius_to_fahrenheit function to easy_math (#219)
6. Push the branch to `origin/feat/add-celsius-to-fahrenheit`.
PR Details for GitHub

Title: feat: add celsius_to_fahrenheit function to easy_math

Description: Closes #219. Added celsius_to_fahrenheit() helper function to easy_math along with corresponding unit tests.

i want this

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<h3><a href="https://github.com/sara-czasak/py-simple-wrap"><code>Building py-simple-wrap</code></a></h3>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
also add my linked in



https://www.linkedin.com/in/yamkelo-vilakazi-31b930397 

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<h3><a href="https://github.com/sara-czasak/py-simple-wrap"><code>Building py-simple-wrap</code></a></h3>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
no say something relating

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <b>Active contributor to <a href="https://github.com/sara-czasak/py-simple-wrap"><code>py-simple-wrap</code></a></b>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
no no maybe mention my project not that the automator mention it or maybe say v1 is out

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <b>Creator of <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><code>msp-outreach-automator</code></a> (v1.0 out now!)</b>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python desktop automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
nah change it say a joke or netwroking joke lol





HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <i>"I'd tell you a UDP joke, but you might not get it."</i>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python desktop automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
i want this too

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <i>"I'd tell you a UDP joke, but you might not get it."</i>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Featured Projects

<table>
  <tr>
    <td width="50%">
      <h3 align="center"><b>MSP Outreach Automator</b></h3>
      <p align="center">Python desktop automation script engineered to streamline personalized outreach workflows.</p>
      <p align="center">
        <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><b>View Code »</b></a>
      </p>
    </td>
    <td width="50%">
      <h3 align="center"><b>Personal Portfolio</b></h3>
      <p align="center">Interactive single-page application built around a custom network-gateway aesthetic.</p>
      <p align="center">
        <a href="https://ctrl-yam.github.io"><b>Visit Site »</b></a>
      </p>
    </td>
  </tr>
</table>

### GitHub Stats

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ctrl-Yam&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Ctrl-Yam&label=PROFILE+VIEWS&color=005073&style=for-the-badge" alt="Profile Views" />
</p>

### Certifications

<p align="center">
  <img src="https://img.shields.io/badge/Cisco-Networking_Basics-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
</p>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
these too but no emjojies

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <i>"I'd tell you a UDP joke, but you might not get it."</i>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Projects

<table>
  <thead>
    <tr>
      <th>Project</th>
      <th>Description</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Personal Portfolio Page</b></td>
      <td>Interactive single-page application built around a custom network-gateway aesthetic.</td>
      <td><a href="https://ctrl-yam.github.io">Visit</a></td>
    </tr>
    <tr>
      <td><b>MSP Outreach Automator</b></td>
      <td>Python desktop automation script engineered to streamline personalized outreach workflows.</td>
      <td><a href="https://github.com/Ctrl-Yam/msp-outreach-automator">Code</a></td>
    </tr>
  </tbody>
</table>

### Project Spotlight: py_simple

<p><i>Mission: Making Python's complex features accessible to everyone.</i></p>

<p>Beginner-friendly wrapper modules that turn multi-step Python tasks into one-line calls so newer developers can focus on building instead of boilerplate.</p>

<p>
  <img src="https://img.shields.io/github/contributors/sara-czasak/py-simple-wrap?style=for-the-badge&color=005073" alt="Contributors"/>
  <img src="https://img.shields.io/github/issues/sara-czasak/py-simple-wrap?style=for-the-badge&color=005073" alt="Issues"/>
  <img src="https://img.shields.io/github/issues/sara-czasak/py-simple-wrap/good%20first%20issue?style=for-the-badge&color=005073&label=GOOD%20FIRST%20ISSUE" alt="Good First Issue"/>
</p>

<p>
  <a href="https://github.com/sara-czasak/py-simple-wrap"><img src="https://img.shields.io/badge/CONTRIBUTE-READ_THE_GUIDE-181717?style=for-the-badge" alt="Contributing Guide"/></a>
</p>

### GitHub Stats

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ctrl-Yam&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Ctrl-Yam&label=PROFILE+VIEWS&color=005073&style=for-the-badge" alt="Profile Views" />
</p>

### Certifications

<p align="center">
  <img src="https://img.shields.io/badge/Cisco-Networking_Basics-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
</p>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
why is my streak 1??? iv been working

GitHub counts contributions strictly based on specific rules, and a streak usually drops to 1 for one of three technical reasons:

Commits Are on Feature Branches: Commits pushed to non-default branches (like docs/easy-ai-reference or feat/add-celsius-to-fahrenheit) do not count toward your contribution calendar or streak until the Pull Request is actually merged into the repository's main branch.

Git Email Mismatch: If your local Git configuration uses an email address that isn't added and verified in your GitHub account settings, GitHub won't link those commits to your profile.

Streak Card API Caching: The github-readme-streak-stats service heavily caches image renders across GitHub's CDN. Even if GitHub registered today's activity, the badge card image itself can take up to 24 hours to update unless cache-busted.

Quick Checks to Fix It

Verify your local Git email:

Bash
git config user.email
Ensure this exact email is listed under your GitHub Settings > Emails.

Check your branches:
Opening a PR counts as a single contribution for the day, but daily commits won't sustain a continuous streak until those PRs are merged into main.

Force a daily contribution:
Making a tiny direct commit to your profile README's main branch (like updating a line or badge) immediately logs a daily contribution directly to your main branch while waiting on external PR merges.

the spotlight should be the automator





<div align="center">



Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.



<p>

  <i>"I'd tell you a UDP joke, but you might not get it."</i>

</p>



<p>

  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>

  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>

  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>

</p>



### Languages, Systems & Tools



<a href="https://skillicons.dev">

  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />

</a>



### Networking & Infrastructure



<p>

  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>

  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>

  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>

  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>

</p>



### Environments & Customization



<p>

  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>

  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>

  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>

  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>

</p>



### Projects



<table>

  <thead>

    <tr>

      <th>Project</th>

      <th>Description</th>

      <th>Link</th>

    </tr>

  </thead>

  <tbody>

    <tr>

      <td><b>Personal Portfolio Page</b></td>

      <td>Interactive single-page application built around a custom network-gateway aesthetic.</td>

      <td><a href="https://ctrl-yam.github.io">Visit</a></td>

    </tr>

    <tr>

      <td><b>MSP Outreach Automator</b></td>

      <td>Python desktop automation script engineered to streamline personalized outreach workflows.</td>

      <td><a href="https://github.com/Ctrl-Yam/msp-outreach-automator">Code</a></td>

    </tr>

  </tbody>

</table>



### Project Spotlight: py_simple



<p><i>Mission: Making Python's complex features accessible to everyone.</i></p>



<p>Beginner-friendly wrapper modules that turn multi-step Python tasks into one-line calls so newer developers can focus on building instead of boilerplate.</p>



<p>

  <img src="https://img.shields.io/github/contributors/sara-czasak/py-simple-wrap?style=for-the-badge&color=005073" alt="Contributors"/>

  <img src="https://img.shields.io/github/issues/sara-czasak/py-simple-wrap?style=for-the-badge&color=005073" alt="Issues"/>

  <img src="https://img.shields.io/github/issues/sara-czasak/py-simple-wrap/good%20first%20issue?style=for-the-badge&color=005073&label=GOOD%20FIRST%20ISSUE" alt="Good First Issue"/>

</p>



<p>

  <a href="https://github.com/sara-czasak/py-simple-wrap"><img src="https://img.shields.io/badge/CONTRIBUTE-READ_THE_GUIDE-181717?style=for-the-badge" alt="Contributing Guide"/></a>

</p>



### GitHub Stats



<p align="center">

  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ctrl-Yam&theme=tokyonight&hide_border=true" alt="GitHub Streak" />

</p>



<p align="center">

  <img src="https://komarev.com/ghpvc/?username=Ctrl-Yam&label=PROFILE+VIEWS&color=005073&style=for-the-badge" alt="Profile Views" />

</p>



### Certifications



<p align="center">

  <img src="https://img.shields.io/badge/Cisco-Networking_Basics-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>

</p>



### Contribution Snake



<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />



</div>

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <i>"I'd tell you a UDP joke, but you might not get it."</i>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Projects

<table>
  <thead>
    <tr>
      <th>Project</th>
      <th>Description</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Personal Portfolio Page</b></td>
      <td>Interactive single-page application built around a custom network-gateway aesthetic.</td>
      <td><a href="https://ctrl-yam.github.io">Visit</a></td>
    </tr>
    <tr>
      <td><b>MSP Outreach Automator</b></td>
      <td>Python desktop automation script engineered to streamline personalized outreach workflows.</td>
      <td><a href="https://github.com/Ctrl-Yam/msp-outreach-automator">Code</a></td>
    </tr>
  </tbody>
</table>

### Project Spotlight: MSP Outreach Automator

<p><i>Mission: Streamlining personalized communication and outreach workflows.</i></p>

<p>A Python desktop automation tool engineered to manage targeted email dispatch, batch processing, and personalized template rendering with minimal overhead.</p>

<p>
  <img src="https://img.shields.io/github/stars/Ctrl-Yam/msp-outreach-automator?style=for-the-badge&color=005073" alt="Stars"/>
  <img src="https://img.shields.io/github/forks/Ctrl-Yam/msp-outreach-automator?style=for-the-badge&color=005073" alt="Forks"/>
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
</p>

<p>
  <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><img src="https://img.shields.io/badge/VIEW_REPOSITORY-181717?style=for-the-badge&logo=github&logoColor=white" alt="View Repository"/></a>
</p>

### GitHub Stats

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ctrl-Yam&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Ctrl-Yam&label=PROFILE+VIEWS&color=005073&style=for-the-badge" alt="Profile Views" />
</p>

### Certifications

<p align="center">
  <img src="https://img.shields.io/badge/Cisco-Networking_Basics-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
</p>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>
add this too, make it about our upcomming v2

HTML
<div align="center">

Networking student and developer based in Johannesburg, South Africa. Building Python automation tools, enterprise network solutions, and custom system environments.

<p>
  <i>"I'd tell you a UDP joke, but you might not get it."</i>
</p>

<p>
  <a href="https://ctrl-yam.github.io"><img src="https://img.shields.io/badge/PORTFOLIO-000000?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://github.com/Ctrl-Yam"><img src="https://img.shields.io/badge/GITHUB-181717?style=for-the-badge&logo=github&logoColor=white"/></a>
  <a href="https://www.linkedin.com/in/yamkelo-vilakazi-31b930397"><img src="https://img.shields.io/badge/LINKEDIN-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white"/></a>
</p>

### Languages, Systems & Tools

<a href="https://skillicons.dev">
  <img src="https://skillicons.dev/icons?i=py,java,html,js,bash,linux,windows,docker,git,github,vscode&perline=11" />
</a>

### Networking & Infrastructure

<p>
  <img src="https://img.shields.io/badge/Cisco-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/Wireshark-167DAA?style=for-the-badge&logo=wireshark&logoColor=white"/>
  <img src="https://img.shields.io/badge/Packet_Tracer-005073?style=for-the-badge&logo=cisco&logoColor=white"/>
  <img src="https://img.shields.io/badge/TCP/IP_%26_VLANs-000000?style=for-the-badge"/>
</p>

### Environments & Customization

<p>
  <img src="https://img.shields.io/badge/Arch_Linux-1793D1?style=for-the-badge&logo=arch-linux&logoColor=white"/>
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=ubuntu&logoColor=white"/>
  <img src="https://img.shields.io/badge/WSL2-0078D6?style=for-the-badge&logo=windows&logoColor=white"/>
  <img src="https://img.shields.io/badge/Hyprland-552A80?style=for-the-badge&logo=hyprland&logoColor=white"/>
</p>

### Projects

<table>
  <thead>
    <tr>
      <th>Project</th>
      <th>Description</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>Personal Portfolio Page</b></td>
      <td>Interactive single-page application built around a custom network-gateway aesthetic.</td>
      <td><a href="https://ctrl-yam.github.io">Visit</a></td>
    </tr>
    <tr>
      <td><b>MSP Outreach Automator</b></td>
      <td>Python desktop automation script engineered to streamline personalized outreach workflows.</td>
      <td><a href="https://github.com/Ctrl-Yam/msp-outreach-automator">Code</a></td>
    </tr>
  </tbody>
</table>

### Open Source Projects

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Contributors Needed</th>
      <th>Link</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>msp-outreach-automator</b></td>
      <td>Desktop automation tool streamlining outreach workflows. Expanding features for upcoming v2 release.</td>
      <td>Yes</td>
      <td><a href="https://github.com/Ctrl-Yam/msp-outreach-automator">CONTRIBUTING.md</a></td>
    </tr>
  </tbody>
</table>

### Project Spotlight: MSP Outreach Automator

<p><i>Mission: Streamlining personalized communication and outreach workflows.</i></p>

<p>A Python desktop automation tool engineered to manage targeted email dispatch, batch processing, and personalized template rendering with minimal overhead.</p>

<p>
  <img src="https://img.shields.io/github/stars/Ctrl-Yam/msp-outreach-automator?style=for-the-badge&color=005073" alt="Stars"/>
  <img src="https://img.shields.io/github/forks/Ctrl-Yam/msp-outreach-automator?style=for-the-badge&color=005073" alt="Forks"/>
  <img src="https://img.shields.io/badge/Python-3.x-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
</p>

<p>
  <a href="https://github.com/Ctrl-Yam/msp-outreach-automator"><img src="https://img.shields.io/badge/VIEW_REPOSITORY-181717?style=for-the-badge&logo=github&logoColor=white" alt="View Repository"/></a>
</p>

### GitHub Stats

<p align="center">
  <img src="https://github-readme-streak-stats.herokuapp.com/?user=Ctrl-Yam&theme=tokyonight&hide_border=true" alt="GitHub Streak" />
</p>

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=Ctrl-Yam&label=PROFILE+VIEWS&color=005073&style=for-the-badge" alt="Profile Views" />
</p>

### Certifications

<p align="center">
  <img src="https://img.shields.io/badge/Cisco-Networking_Basics-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white"/>
</p>

### Contribution Snake

<img src="https://raw.githubusercontent.com/Ctrl-Yam/Ctrl-Yam/output/github-contribution-grid-snake-dark.svg" alt="Contribution Snake" />

</div>



Gemini is AI and can make mistakes.

Interpreting the Context

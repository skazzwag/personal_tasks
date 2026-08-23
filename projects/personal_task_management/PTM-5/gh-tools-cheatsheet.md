# GitHub CLI Tools Cheat Sheet

## Table of Contents
- [gh CLI](#gh-cli)
- [gh-dash](#gh-dash)
  - [Keybindings](#gh-dash-keybindings)
  - [Custom Actions](#gh-dash-custom-actions)
- [gh-review](#gh-review)
  - [Keybindings](#gh-review-keybindings)
- [hunk](#hunk)
  - [Keybindings](#hunk-keybindings)

---

## gh CLI

### Installation
```bash
# Using brew
brew install gh

# Using apt
sudo apt install gh
```

### Authentication
```bash
gh auth login
```

### Repository Management
```bash
# Clone a repository
gh repo clone owner/repo

# Create a new repository
gh repo create [name] --public/--private --clone

# View repositories
gh repo list [owner]

# Fork a repository
gh repo fork [owner/repo]
```

### Issue Management
```bash
# List issues
gh issue list

# View an issue
gh issue view [number]

# Create an issue
gh issue create --title "title" --body "body"

# Comment on an issue
gh issue comment [number] --body "comment"
```

### Pull Request Management
```bash
# List PRs
gh pr list

# View a PR
gh pr view [number]

# Create a PR
gh pr create --title "title" --body "body" --base [branch] --head [branch]

# Checkout a PR
gh pr checkout [number]

# Merge a PR
gh pr merge [number] --merge/--squash/--rebase
```

### Workflow
```bash
# Run workflows
gh workflow list
gh workflow view [workflow-id]
gh workflow run [workflow-id]
```

---

## gh-dash

**Note:** gh-dash is a Terminal UI (TUI) that provides a rich dashboard interface for GitHub PRs and issues with full keyboard navigation.

### Installation
```bash
# Using npm
npm install -g gh-dash

# Using yarn
yarn global add gh-dash
```

### Configuration
```bash
# Initialize configuration
gh-dash configure
```

### Usage
```bash
# Start the dashboard
gh-dash

# With specific configuration
gh-dash --config path/to/config.yml
```

### Keybindings

#### Navigation
- `j` / `↓`: Move down
- `k` / `↑`: Move up
- `h` / `←`: Move left (between sections)
- `l` / `→`: Move right (between sections)
- `gg`: Jump to top
- `G`: Jump to bottom
- `Ctrl+d`: Scroll down in preview
- `Ctrl+u`: Scroll up in preview

#### PR Actions
- `o`: Open PR in browser
- `Enter`: Open PR in browser
- `y`: Copy PR number to clipboard
- `Y`: Copy PR URL to clipboard
- `c`: Checkout PR branch
- `m`: Merge PR
- `r`: Add review comment
- `a`: Approve PR
- `R`: Request changes
- `s`: Squash and merge
- `u`: Update PR branch
- `d`: Close PR

#### Issue Actions
- `o`: Open issue in browser
- `Enter`: Open issue in browser
- `y`: Copy issue number to clipboard
- `Y`: Copy issue URL to clipboard
- `c`: Comment on issue
- `l`: Add labels to issue
- `a`: Assign issue
- `C`: Close issue

#### View Switching
- `s`: Switch between PRs and Issues views

#### General
- `?`: Show help
- `q`: Quit
- `/`: Filter items
- `Esc`: Clear filter / exit mode

### Custom Actions

You can define custom keybindings in your config:

```yaml
keybindings:
  - key: g
    name: laygit
    command: lazygit
  - key: C
    name: code review
    command: |
      tmux new-window -c {{.RepoPath}}
      'nvim -c ":silent Octo pr edit {{.PrNumber}}"'
```

### Configuration Options
```yaml
# Example config.yml
prSections:
  - title: My Pull Requests
    filters: is:open author:@me
    limit: 5

  - title: Needs My Review
    filters: is:open review-requested:@me
    limit: 5

issuesSections:
  - title: My Issues
    filters: is:open author:@me
    limit: 5
```

---

## gh-review

**Note:** gh-review is a Terminal UI (TUI) for reviewing GitHub pull requests, providing an interactive interface for code review.

### Installation
```bash
# Using npm
npm install -g gh-review

# Using yarn
yarn global add gh-review
```

### Usage
```bash
# Review a PR (opens TUI)
gh-review [number]

# Review with specific base branch
gh-review [number] --base [branch]

# Review with specific head branch
gh-review [number] --head [branch]
```

### Keybindings

#### Navigation
- `j` / `↓`: Next hunk
- `k` / `↑`: Previous hunk
- `g`: Go to first hunk
- `G`: Go to last hunk
- `Ctrl+d`: Scroll down in diff
- `Ctrl+u`: Scroll up in diff

#### Review Actions
- `a`: Approve PR
- `r`: Request changes
- `c`: Add comment
- `s`: Submit review
- `e`: Edit comment
- `d`: Delete comment
- `q`: Quit

#### Hunk Actions
- `Space`: Toggle hunk selection
- `v`: Toggle hunk view
- `Enter`: Add comment to hunk
- `t`: Toggle all hunks

#### General
- `?`: Show help
- `/`: Search in diff
- `n`: Next search match
- `N`: Previous search match
- `Esc`: Exit current mode

### Commands
```bash
# Approve a PR (non-interactive)
gh-review approve [number]

# Request changes (non-interactive)
gh-review request-changes [number]

# Comment on a PR (non-interactive)
gh-review comment [number] --body "comment"
```

---

## hunk

**Note:** hunk is a Terminal UI (TUI) for viewing and staging git diffs with an interactive interface.

### Installation
```bash
# Using curl
curl -sSL https://github.com/neon/hunk/releases/latest/download/hunk_x86_64-unknown-linux-gnu.tar.gz | tar -xz -C ~/.local/bin

# Using brew
brew install hunk
```

### Configuration
```bash
# Set as git difftool
git config --global diff.tool hunk
git config --global diff.guitool hunk
```

### Usage
```bash
# Diff (opens TUI)
hunk diff

# Diff specific file
hunk diff [file]

# Diff with staged changes
hunk diff --cached

# Show commit
hunk show [commit]

# Show file at commit
hunk show [commit] -- [file]
```

### Keybindings

#### Navigation
- `j` / `↓`: Next hunk
- `k` / `↑`: Previous hunk
- `g`: Go to first hunk
- `G`: Go to last hunk
- `Ctrl+d`: Scroll down
- `Ctrl+u`: Scroll up

#### Hunk Actions
- `Space`: Toggle hunk selection
- `Tab`: Toggle hunk selection (alternative)
- `s`: Stage selected hunks
- `u`: Unstage selected hunks
- `d`: Discard selected hunks
- `c`: Commit selected hunks
- `t`: Toggle all hunks

#### View Modes
- `v`: Toggle hunk view
- `w`: Toggle word diff
- `b`: Toggle blame view
- `Enter`: Expand/collapse hunk

#### General
- `?`: Show help
- `/`: Search
- `n`: Next search match
- `N`: Previous search match
- `q`: Quit
- `Esc`: Exit current mode

### Git Integration
```bash
# Use as difftool
git difftool

# Use as mergetool
git mergetool
```

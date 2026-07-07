# Personal Tasks &amp; Knowledge Base

> A structured repository for tracking tasks, projects, and knowledge using Jira and Git.

---

## 📌 Overview

This repository serves as a **knowledge base** and **work archive** for all personal projects, tasks, and notes. Each project, given as a subdirectory of the `projects` directory, has a corresponding Jira Kanban board. Each project directory will contain subdirectories with the Jira ticket number which each contain a `TASK.md` containing information on what the ticket is for and possibly other text files, usually markdown, containing notes need to complete the ticket.

- **Jira**: Active task management (Kanban boards per area).
- **Repo**: Permanent, versioned storage for notes, code, and outputs.

---

## 🗂️ Structure

```
personal_tasks/
├── projects/             
│   ├── personal_task_mangement/           # Linked to Jira Kanban board
│   │   ├── PTM-<n>                        # The Kanban ticket being worked on
│   │   │    ├── TASK.md                   # Ticket summary, links, and notes
│   │   │    └── <other_notes>.md          # Additional notes made for ticket
│   │   └── PTM-<n+1>
│   │        ├── TASK.md
│   │        └── <other_notes>.md
│   └─ horror_movie_analytics/
│       └── HMA-<n>                        # The Kanban ticket being worked on
│            ├── TASK.md                   # Ticket summary, links, and notes
│            └── <other_notes>.md          # Additional notes made for ticket
└── README.md                              # This file
```

(NOTE: there will be loads of projects and tickets so this structure is just demonstrative)

---

## 🔗 Jira + Repo Linking

### How It Works

1. **Create a Kanban board** in Jira for each area (e.g., `"Personal Task Mangement"`, `"Horror Movie Analytics"`).
2. **Create a subdirectory in the projects directory** in this repo matching the board name that's lowercase and uses replaces spaces with underscores (e.g., `personal_task_management/`, `horror_movie_analytics/`).
3. **For each Jira ticket**:
  - Create a folder in the subdirectory named after the ticket ID (e.g., `personal_task_management/PTM-<n>/`).
  - Add a `TASK.md` to the folder with the ticket summary/purpose.
  - Store all notes, code, and outputs related to the ticket in this folder.

### Example

- **Jira Ticket**: [WORK-123: Set up home server](https://your-jira-instance.atlassian.net/browse/WORK-123)
- **Repo Folder**: [`work/WORK-123/`](./work/WORK-123/)
  - Contains: `README.md`, `notes.md`, `scripts/setup.sh`, `outputs/logs.txt`

---

## 🚀 Automation (TODO!)

- Set up a **Jira webhook** to trigger thea shell script automatically to make new ticket subdirectories.
- Use Jira GitHub integration.

---

## 📄 Folder README Template (TO REVIEW)

Use this template for the `README.md` in each ticket folder:

```markdown
# {TICKET_KEY}: {TICKET_SUMMARY}

**Jira Ticket**: [Link to Jira](https://your-jira-instance.atlassian.net/browse/{TICKET_KEY})
**Status**: {Open/In Progress/Done}
**Created**: {YYYY-MM-DD}

## 📝 Notes
- {Your notes here}

## 📂 Files
- [ ] [notes.md](./notes.md) - Detailed notes
- [ ] [outputs/](./outputs/) - Generated files

## 🔗 Related Tickets
- [TICKET-456](https://your-jira-instance.atlassian.net/browse/TICKET-456)
```

---

## 🔍 Searching the Repo

Use `grep` or `ripgrep` to search across all notes:

```bash
# Search for "Python" in all markdown files
rg "Python" --type md

# Search for tickets related to "research"
rg "RES-" --type md
```

---

## 🧹 Maintenance

- **Delete Jira boards** when a project is complete to free up space (free tier limit).
- **Keep the repo**: All history and files remain in Git.

---

## 🤖 Agent-Friendly Tips

- **Clear Structure**: Each ticket folder is self-contained and follows the same pattern of a `TASK.md` other files for notes/examples on the task.
- **Consistent Naming**: Use Jira ticket IDs (e.g., `PTM-<n>`) for folder names.
- **READMEs Everywhere**: Every non-ticket folder has a `README.md` with context and links.


## License
This repository is licensed under **[CC BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/)**.

**Additional Terms**:
- Use of this content to train AI models, large language models, or similar systems is **explicitly prohibited** without written permission.

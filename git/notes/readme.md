## Chapter 1: Introduction to Git

### What is git?
Git is a distributed version control system that enables users to collaborate on projects, tracking changes in files and directories while providing a history of snapshots and the ability to manage different branches and merge code changes efficiently

### What is version control?
Git allows developers to track changes made to files over time, keeping a history of all modifications. This makes it easy to revert to previous versions if something goes wrong or to see how the code evolved.

### Centralised (SVN) vs Distributed VCS (Git)

| Centalised (SVN)  | Distributed (Git)  
|-------|------
| Single source of truth  | Full history on every machine |
| Requires network to commit | Work offline |
| Conflicts are common | Fast branching and merging |
| Server Outage = devs stuck | Resilient to outages | 
| Locks files during edits | Everyone cancommit locally | 

---

## Chapter 2: Git internals and Core Concepts

### Git Terminology & Key Concepts

- **Repository**: A Git project (tracked folder with a git directory)
- **Commit**: A snapshot of your files and metadata (author, timestamp, message, parent commit, etc.)
- **Branch**: A movable pointer to a specific commit (e.g., main, dev, feature/login)
- **Remote**: A reference to an external Git host (like GitHub, GitLab) usually named origin
- **Staging Area**: Also called the Index; a buffer between your working directory and the repo what you plan to commit
- **Blobs**: "binary large object" - stores the actual content of files (just the data, no filename/path)
- **Trees** : stores filenames, file paths, and pointers to blobs (files) and other trees (directories). Represents a directory snapshot
- **Refs (Reference)** : pointer to a commit: branches (refs/heads), tags (refs/tags), and special ones like HEAD
- **HEAD** : pointer to the current branch or commit you're working on
- **Index**: the actual file git/index, a binary file that holds the staging area info
- **Object Store**: git/objects/ — where Git stores all blobs, trees, and commits by SHA hash
- **Tag**: a ref to a specific commit, often used for marking releases

### The .git directory

The .git directory is the heart of every Git repository. It contains all the metadata and objects Git needs to manage the version history, branches, remotes, and more. When you run `git init`, Git creates this hidden .git folder inside your project directory.

#### What is inside the .git directory?

- .git/HEAD - Points to the current branch (e.g., refs/heads/main).
- .git/config - Project-specific Git configuration (user, remotes, etc.).
- .git/objects/	- Stores all the content (commits, trees, blobs) as SHA-1 hashes.
- .git/refs/ - Contains pointers to branches (heads/) and tags (tags/).
- .git/index - The staging area. Tracks what will be included in the next commit.

### Git common commands
| Commands  | Use 
|-------|------
| git init | initialises a new Git repo with git directory|
| git add | stage changes|
| git commit | Snapshot changes|
| git status | show staged/unstaged work|
| git log | show commit history|
| git diff | show what changed|
| git config | set user/email|
| git help <command> | built-in docs|
| git clone | copy a remote repo|
| git rm | remove files|
| git my | rename files|
| git restore | undo file changes|



































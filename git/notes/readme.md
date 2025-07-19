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

### The Areas of Git

![image](https://github.com/user-attachments/assets/b7bfeb0a-6b00-4cef-91ec-aef7a72569ce)

- **1. Working Directory** - Where you actively edit files. It shows the current state of your project. - `git status` 
- **2. Staging Area (Index)** - Holds changes you intend to include in the next commit. - `git add` to stage, `git status` to view 
- **3. Git Repository (.git)** | The permanent, versioned history of your project. - `git commit` adds to this

---

## Chapter 3: History, Branching & Merging

### Viewing history

Commands Used for viewing history:

- `git log`: See commit history
- `git log --oneline--graph`:Visual summary
- `git show <commit>`: view a specific commit
- `git diff`: Compare unstaged vx last commit
- `git diff --staged`: comapare staged vs last commmit

Bonus:

- `git blame <file>`: show who last changed each line
- `git reflog`: View local HEAD history (even deleted branches)

### Git vs GitHub:

| Feature                | **Git**                                      | **GitHub**                                       |
| ---------------------- | -------------------------------------------- | ------------------------------------------------ |
| **Type**               | Version control system (VCS)                 | Online hosting service for Git repositories      |
| **What it does**       | Tracks changes in your local code            | Hosts repositories for collaboration and sharing |
| **Where it runs**      | On your **local computer** (CLI or GUI)      | On the **web(cloud)** (`github.com`)              |
| **Use case**           | Save versions, switch branches, undo changes | Collaborate, review code, manage pull requests   |
| **Requires Internet?** | ❌ No (works offline)                         | ✅ Yes (web-based)                                |
| **Interface**          | Command line / GUI apps (e.g., GitKraken)    | Web UI, GitHub Desktop, GitHub CLI               |
| **Created by**         | Linus Torvalds (2005)                        | Microsoft (owns GitHub since 2018)               |


### Branching

- `git branch`: List/create branches
- `git checkout -b<branch>`: Create & switch (older syntax)
- `git switch -c<branch>`: modern version to do same as above
- `git switch <branch>`: Sweitch branches safely
- `git branch -d<branch>`: delete branch

Note:

Git switch is newer and more beginner friendly. Works only with newer git versions.

Git branch only creates or lists, doesnt switch.

checkout still works but is multi-purpose and confusing.

### Merging in Git

When you’ve been working on a separate branch (feature-x) and you want to add your changes to the main project (main), you merge the feature branch into main.

![image](https://github.com/user-attachments/assets/8ba557ef-1c76-4009-ae63-d242c7c6383a)

### Visulaise Branches & Logs:

- `git log --oneline` - Compact commit view
- `git log --graph` - visual tree structure
- `git log --oneline --graph -all` - Comapct, visual and full view

These are great for debugging merges and tracking branches. Helps yosee whats really happening under the hood.

### Rebase vs Merge

| **Merge**                                | **Rebase**                                          |
| ---------------------------------------- | --------------------------------------------------- |
| Combine changes and preserve all history | Combine changes and rewrite history                 |
| Creates a new commit                     | No merge commits                                    |
| Good for team workflows                  | Ideal for cleanup before PR                         |
| Use wqhen working collaboratively        | Use when cleaning up your local history             |

---

## Advanced Git Usage:

### Git stash and pop

git stash is like putting your work into a temporary drawer so you can switch tasks without committing your changes. Later, you can take it out with git stash pop.

Git stash and pop commands:

- `git stash` - temporarily save uncommitted changes
- `git stash list` - view all stashes
- `git stash apply` - reapply latest stash (keeps stash)
- `git stash pop` - reapply and delete the stash

These commands are used when switching branches mid-task. Great for "I'm not ready to commit, but I need to move"

### Git reset, Revert and cherry pick:

#### git revert 

- Creates a new commit that undoes another
- safe for shared history
- Used in production

#### git reset 

- move branch pointer backword
- Soft = keep changes
- Mixed = unstage
- Hard = nuke everything.

#### git cherry-pick

- Apply a single commit from another branch
- Useful for hotfixes or targeted changes


### Forks and Pull requests (PRs)

- Fork = your own copy of someone elses repo (on Github)
- Clone the forked repo to your local machine
- Make changes -> push to your fork
- Open a Pull request (PR) to propose to your changes
- Used in open source and cross-team, workflows
- original rep owner can review, comment and merge.

![image](https://github.com/user-attachments/assets/a85ce718-c9ff-4712-b135-887cb68a3470)

### Collaborating practises

- Use branches to isolate work
- Push to remote and open pull requests
- Assign reviewers, use GitHubs UI for comments
- Resolve conflicts before merge
- Use issues, projects, Discussions to track work
- Keep commits focused and clean

### Typical Git workflow

![image](https://github.com/user-attachments/assets/d48f4284-310d-48f3-ad75-c75cbc27bce6)

### Trunk-Based-Development 

Trunk-Based Development (TBD) is a collaborative Git workflow where all developers work in a single main branch, called the trunk (usually main or master), and keep changes small and frequent.

- All devs commit to main or short-lived branches
- Heavy CI/testing gates
- Used in fast-moving orgs (Google/Facebook)


## Git best practises

### Commit Hygiene & Best Practises

Write good commit messages - A clear commit message makes it easy to understand what changed and why — even months later.

Use squashing before merging PRs - Squashing lets you combine multiple small or messy commits into one clean, meaningful commit before merging a pull request.

One logical change per commit - Each commit should do one thing only — not multiple unrelated changes.

Avoid noisy merges or fixfixfinalfinal2 - Commits like fix, finalfinal, reallyfinal2 clutter the history and give no useful context.

### Pre-commit & Automation

1- Run linters/tests before comitting 9pre-commit, Husky, tflint/sec etc.)
2- Prevent broken code from entering the repo
3- Hook into CI pipelines for formatting, testing and scanning

### Common Mistakes in the Real World

![image](https://github.com/user-attachments/assets/6171b0fc-9366-4244-b12a-d841efcd8031)

### Git at scale

Absolutely! When using Git at scale, such as in large teams, monorepos, or enterprise environments, additional tools and practices are needed to manage complexity, performance, and automation.

- Monorepo strategies - Single Git repo for multiple projects
- Sparse checkout - Loads only part of the repository into your working directory — useful in huge monorepos.
- Large file support (Git LFS) - Git is not good at handling large binaries (e.g. videos, datasets, design files). Use Git LFS (Large File Storage) to manage them.
- Clean up legacy history (filter-branch, filter-repo) - Used to reduce repo size or remove sensitive files like secrets/passwords.
- Submodules vs subtrees in microservice repos - Used when splitting projects into microservices with their own Git repos.
- Selective CI builds (e.g. Turborepo, Nx, Bazel) - Run CI only on changed projects in a monorepo, instead of running everything every time.
- Commit linting + bots to enforce rules - Ensure commits follow standards using tools/bots
- GitOps-style deployments (e.g. ArgoCD, Flux) - Manage infrastructure and deployments using Git as the single source of truth.
- Server-side Git hooks (e.g. pre-commit.ci, Lefthook) - Run checks on the Git server or CI to enforce rules before allowing pushes or merges.

### Git Security & Secrets Hygiene

- Preveting secret leaks in commits
- Using git-secrets, trufflehog
- Cleaning secrets from history
- Auditing rep contributors + logs.

## Hands-on Git & Github

### Connecting to Github

- 1- git remote add origin <url>-link local --> GitHub
- 2- git push -u origin main - send your work to the cloud
- 3- git pull - bring down changes from Github
- 4- SSH vs HTTPS: ssh = Secure no password, HTTPS = easy but asks for credentials




































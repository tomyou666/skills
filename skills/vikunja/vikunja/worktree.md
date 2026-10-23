# Worktree

Same Vikunja. Do not `projects_create`. Do not run setup.md. Do not edit `AGENTS.md`.

Target git: project directory in `## Vikunja projects`, or the workspace root. No `.git` or no commits: stop. Do not `git init`. Do not commit unless asked.

Branch: one segment, no slash. Shape `<prefix>-<n>` lowercase.

Path: `<parent of workspace>/<project>-<branch>`. Outside any outer repo.

After `git worktree add`, shell and file writes use that path. Cursor workspace stays.

Linked check runs in the target path: `--git-dir` differs from `--git-common-dir`.

Merge only when asked. Target: branch checked out on the main worktree. `git merge --ff-only`. Failure: report. Leave worktree and branch.

Success: `git worktree remove <path>`, then `git branch -d <branch>`. No `-D`.

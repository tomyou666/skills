# Project setup

Once per project. Daily task edits stay in [SKILL.md](SKILL.md).

1. `projects_create`. `identifier` is the ticket prefix (`MEMO-1`), unique, max 10. Not Inbox. Not My Open Tasks.
2. Ensure category labels `bug` and `enhancement` exist (`labels_list` `{fields: ["id", "title"]}` then `labels_create` if missing). Do not create state labels.
3. Kanban view, or `project_views_create` `view_kind: kanban`, `bucket_configuration_mode: manual`, title `Kanban`. A new view has `To-Do`, `Doing`, and `Done`.
4. Buckets at position 100–600: `needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`, `Done`. `buckets_create` / `buckets_update` `{project, view, title, position}`.
5. `project_views_update`: mode `manual`, `default_bucket_id` = `needs-triage`, `done_bucket_id` = `Done`. Before any delete.
6. `buckets_delete` `{bucket, project, view}` for every other title. Tasks move to the default bucket. Not deleted. Cannot delete the last, default, or done bucket.
7. Record the category label IDs and the project's `id`, `prefix`, `kanban view` ID, and all 6 bucket IDs in `AGENTS.md` under `## Vikunja projects`.

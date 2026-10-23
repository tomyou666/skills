# Vikunja

The issue tracker this repo uses for tasks.

## Language

**Ticket number**:
The identifier shown on a task, `{prefix}-{index}`, such as `MEMO-1`.
_Avoid_: id, task id, index

**Task id**:
The numeric id the Vikunja tools accept for a task (`task` or `task_id` in arguments).
_Avoid_: ticket number, identifier, index

**Label**:
A mark owned by the user and attached to a task. Used only for category (`bug` or `enhancement`).
_Avoid_: bucket, column, state

**Bucket**:
A kanban column representing the task's state (`needs-triage`, `needs-info`, `ready-for-agent`, `ready-for-human`, `wontfix`, `Done`).
_Avoid_: label

**Done**:
The bucket for a finished task (`done: true`).
_Avoid_: wontfix

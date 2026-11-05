# Itential: project import reports success when a workflow has an illegal (non-hex) task ID

Repro for an Itential Platform bug (platform 6.6.0): a workflow whose task ID is not hexadecimal (`^[0-9a-f]{1,4}$`) is
accepted everywhere locally, but is dropped when the project is imported.

The project has two workflows, one task each:

| Workflow | Task ID | Valid? |
|---|---|---|
| `Workflow A - Valid Task ID` | `a001` | yes |
| `Workflow B - Illegal Task ID` | `t001` | no (`t` is not a hex digit) |

Expected: the import fails or clearly reports that Workflow B was not imported.
Actual: UI file import shows a yellow warning about a failed component; importing from Git through the native
Git integration shows a success message.

The project files are added to this repository by Studio's Git integration.

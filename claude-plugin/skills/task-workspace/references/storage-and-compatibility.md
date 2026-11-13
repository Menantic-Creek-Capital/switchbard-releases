# Storage and compatibility

## Legacy file-backed repos

`tuile storage status` shows per-kind authority. Where a kind reads `database`, the `backlog/` directory is only the repo-root marker and any markdown there is a stale snapshot, not the board. Where it still reads file authority: completed and archived tasks are read-only (set project membership before completing, rollups count open tasks only); duplicate ids block edits until resolved by hand; a body that does not round-trip refuses body writes but accepts frontmatter writes. Report those cases rather than hand-editing.

## Command details

- `storage criteria [--all]` previews consolidation without writes. Applying needs compatible delivered writers/readers, separately authorized cutover and the fresh reviewed digest: `storage criteria --all --apply --preview-digest DIGEST`. It backs up originals privately, audits wrapper discards and verifies readback; per-repository transactions can leave a partial cutover requiring reconciliation. Never reuse a stale digest or infer live migration from source work.
- Any directory you open `tuile` in gets registered as a workspace, and there is no verb to delete a binding or a workspace. There is no cross-repo move: recreate, then archive the source with a note naming the new id.
- `storage backup --file <PATH>` requires `--file`; without it the verb only prints help and exits 0.

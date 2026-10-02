# DSH (DeepSeek Harness) Rules

Hard red line: **DeepSeek official artifacts are read-only.** Everything below preserves that boundary.

## Never touch (official layer)

Do not modify, patch, replace, repackage or delete any DeepSeek official artifact:

- `D:\ProgramFiles\dsh\**` — `desktop\resources\app.asar`, `app.asar.unpacked`, the bundled
  `@deepseek-ai/*` packages, `resources\runtime`, `app-update.yml`, `DeepSeek Harness.exe`;
- official MCP server and plugin directories;
- official account, quota and credential configuration.

Read-only inspection of these paths is allowed; acting on them is not.

## Where fixes may land (user-owned layer)

- `~/.dsh/` configuration and storage — the user accepts changes here;
- self-built scripts or proxies under `D:\`;
- third-party MCP servers.

Prefer "configuration / dependency alignment" over editing plugin source: it is reversible. If a
third-party plugin genuinely must be changed, back it up first and state the rollback path before
editing.

## Procedure

1. Report the diagnosis and the proposed plan; wait for explicit confirmation before doing anything
   that touches the official layer.
2. If the root cause lies in the official layer, stop the out-of-bounds operation immediately,
   report the evidence and request explicit authorization.
3. Keep user-owned fixes physically separate from official artifacts — never edit an official file
   in place, not even temporarily.

## Repair Is a Loop, Not a Single Fix

When the user reports a DSH problem, the reported symptom is the **entry point**, not the scope. The
work is not finished when that symptom disappears.

1. **Set the goal first.** Invoke `/goal` with the terminal condition: DSH has no outstanding defects
   and every enabled plugin behaves correctly. Do not exit the loop while that goal stands — a reply
   that stops at the first green test is not a completed repair.
2. **Fix the reported symptom.** Reproduce it first, then fix it.
3. **Keep sweeping.** Once the reported symptom passes, continue through the remaining plugins and
   features enabled in this DSH installation, testing each one. Every newly found defect re-enters
   step 2 as a new entry point.
4. **Re-verify the whole surface.** Do not trust an earlier pass: a change to a shared config,
   dependency, or proxy layer can break a plugin that previously worked. Re-run the full check.
5. **Report honestly.** Completion means the goal in step 1 is met — every enabled plugin verified,
   with evidence per plugin. Otherwise state what is still failing and what is queued next.

Guard rails are unchanged by the wider sweep: the official layer stays read-only, user-owned fixes
stay physically separate, and a backup plus rollback path is stated before touching any third-party
plugin source. A broader search space never widens the boundary.

If the sweep locates a root cause inside the official layer, stop the out-of-bounds operation
immediately, report the evidence, and request explicit authorization — per **Procedure** step 2.

---
name: workfromphone
description: "Phone-first operating mode for completing Codex work while the user is remote, on a phone, away from the workstation, unable to access the computer, or explicitly invokes $workfromphone. Keep the entire workflow usable from mobile chat: act autonomously on the computer, reuse durable project runbooks and authenticated browser state before asking for help, never assign desktop actions to the user, deliver phone-reachable files and previews, and recover safely from long sessions, compaction, disconnections, timeouts, and high latency."
---

# Work From Phone

Treat the phone as the user's only interface. Once invoked, keep this mode active for the rest of the task and its follow-ups until the user says they are back at the computer.

## Enforce the remote contract

- Perform inspection, editing, commands, testing, retries, browser work, and desktop automation with available tools.
- Never ask the user to use the workstation, run a command, open a local file, click a desktop dialog, inspect a terminal, move a file, take a computer screenshot, keep a window open, or copy something from the computer.
- Never make a local path, `localhost` URL, terminal command, or desktop-only UI the user's required next step.
- Search the workspace and connected services before asking the user to locate or re-upload something that may already be accessible.
- Ask the user only for information, authorization, or an action that can be completed directly from the phone. Prefer one short question with two or three numbered choices and recommend a default.
- Interpret likely voice-dictation mistakes generously. Confirm only when ambiguity could materially change, publish, spend, overwrite, or delete something.
- Follow required safety confirmations, but phrase them as a concise phone-tappable decision with the exact target and impact.
- Never request passwords, API keys, recovery codes, or other secrets in chat. Use an in-app authorization or connected service when available.

If completion truly depends on an unavailable desktop-only action, do not turn that action into homework. Preserve completed work, state the exact blocker briefly, and offer only phone-doable alternatives such as retrying later, attaching an item in chat, authorizing a connector, choosing a fallback format, or receiving the partial result.

## Work autonomously

1. Inspect available files, tools, browser state, connectors, and prior task state.
2. Make safe, in-scope assumptions and continue without waiting for routine preferences.
3. Complete and verify the work with tools. Fix ordinary test or rendering failures without asking the user to troubleshoot.
4. Send short progress updates during long work, roughly every 45 to 60 seconds when meaningful. Do not require the user to keep the app open or reply to keep work moving.
5. Lead the handoff with the outcome, what is ready to tap or download, and any genuinely required phone action.

Do not claim that work will continue in the background unless a real monitoring or background mechanism has been started.

## Reuse project runbooks and authenticated browser state

- Never store account-specific data in this skill or its bundled resources. This includes names, usernames, email addresses, account IDs, profile URLs, browser-profile names, cookies, session data, credentials, tokens, recovery codes, and private links. Keep details needed during a task in ephemeral task state; put only necessary non-secret operational context in project documentation when the user requests it, and never copy that context back into the reusable skill.
- At the start of the task, and before retrying a previously fragile workflow, inspect the active `AGENTS.md` instruction chain and relevant project runbooks such as a README, operations note, or upload checklist. Read the applicable sections before acting instead of rediscovering a solved process through trial and error.
- An arbitrary README is not guaranteed to load as an instruction in a future run. When the user asks Codex not to repeat a cross-session problem, preserve the detailed procedure in a project runbook and add or update the closest project-scoped `AGENTS.md` so future runs are explicitly directed to it. Keep service-, account-, and folder-specific details in that project documentation rather than making them universal skill rules.
- Before asking the remote user to sign in again or touch the workstation, determine which available browser, profile, tab, or connector owns the authenticated session. Do not assume an in-app browser and regular Chrome share cookies, profiles, or Google sign-in state.
- If a visible signed-in tab cannot be claimed reliably, inspect authoritative state and then try a fresh controlled tab in the same authenticated browser profile. Verify the account identity and destination before continuing.
- Before opening a native operating-system file picker, align the automation's controlled tab with the visibly active foreground tab. A picker can attach to the foreground tab even while automation is reading another tab.
- If direct programmatic file assignment silently clears or fails, use the native file picker through available computer-control tools. On Windows, a reliable path is to focus the File name field with `Alt+N`, enter the exact filename, and press Enter. Do not turn the picker into desktop homework for the user.
- For OneDrive or another sync-backed destination, treat a local synced path as staging only. Do not infer the remote folder from a local `Documents` path: Windows sync roots can map to a different cloud path, including misleading nested same-name folders. Resolve the exact cloud destination in the authenticated UI or connector before uploading or retrying, record its visible parent/path and distinguishing existing contents, and verify the artifact there by filename and size. If exact-folder upload is fragile or uncertain, upload once to an explicitly authorized temporary root and use the remote Move/Copy control to the verified destination; reconcile first so an uncertain upload is not duplicated. Do not report cloud delivery from local presence or an upload toast alone, and do not delete leftover duplicates without explicit approval.
- Treat an uncertain upload, publish, send, or submission as possibly complete. Reconcile the destination before retrying, then verify the authoritative public item and every requested cross-posted outbound link.
- After solving a recurring browser or desktop failure, update the project runbook with only the durable invariants and verified recovery steps. Never store credentials, recovery codes, private tokens, or unnecessary personal identifiers in the runbook.

## Handle approval-gated web actions from the phone

For browser workflows that culminate in publishing, sending, submitting, deploying, or another externally visible action, do all reversible preparation before interrupting the user:

Treat an explicit user instruction as authorization for the exact target, scope, audience, and impact it names. Do not ask the user to reconfirm an unchanged action.

1. Upload the already-authorized files, complete metadata and settings, select destinations, and verify the staged result.
2. Save or confirm the platform draft and record a compact checkpoint with the draft title or ID, destination, intended final action, and any live URLs.
3. If the browser control system requires tabs to be preserved across turns, mark the relevant tabs for handoff before asking for confirmation. Never rely only on an in-memory tab object surviving the turn boundary.
4. Ask for action-time confirmation only when the exact final action is not already explicitly authorized, a material detail is missing or changed, or a platform or policy requires a fresh approval. Name the exact targets and public or external impact in one short yes-or-no question that is easy to answer from the phone.
5. Group multiple equivalent final actions into one confirmation when confirmation is required and their targets and impact are already clear, such as publishing two prepared listings or two prepared social posts. Do not bundle unrelated, destructive, financial, or differently scoped actions.
6. After any required confirmation—or when existing explicit authorization already covers the unchanged action—execute immediately. Do not ask again unless the target, scope, cost, audience, or other material impact changed.
7. Verify the authoritative result: the public page, sent item, deployment, receipt, or destination link. For cross-posting, also verify that each outbound link reaches its intended target.

Required approvals still apply, and explicit user authorization does not bypass platform, workspace, connector, or tool approvals. This skill minimizes phone interruptions while preserving informed consent at the exact action boundary.

If a tab or browser session disappears during preparation or a required confirmation, reopen the platform and recover its saved draft or authoritative state. Existing authorization remains usable only for the same exact targets and impact; otherwise ask again. Before suggesting reinstalling a browser plugin or extension, inspect its installation and profile, retry the connection up to three times, and distinguish a transient bridge failure from a missing installation. Never uninstall a working plugin as a speculative reconnection step.

## Survive disconnections and high latency

- Do not claim to prevent network loss or improve raw connection speed. Reduce the cost of interruptions and the amount of data transferred.
- Before a long or fragile step, update a concise checkpoint with the objective, completed outputs, last verified state, live job or process identifiers and log locations, artifact links, and exact next incomplete step. Keep checkpoints out of tracked or public files by default, and never put secrets, private account identifiers, or private share URLs in them.
- Use a real background job or monitor when work must continue without an active chat connection, and record its identifier and status. Keep each wait or poll below 60 seconds.
- After a reconnect, timeout, or uncertain tool result:
  1. Treat the prior action as possibly complete.
  2. Inspect the checkpoint and authoritative state, including jobs, logs, Git state, files, cloud receipts, and remote targets as applicable.
  3. Reconcile what completed and resume at the first incomplete step.
  4. Do not repeat completed actions or ask the user to repeat recoverable information.
- Retry idempotent reads and status checks up to three times with short, bounded backoff. Before retrying a write, upload, send, publish, or deploy, inspect the destination and reuse an idempotency key when supported.
- Never blindly retry a payment, purchase, external message or submission, or destructive action after an uncertain result. Verify the destination first; if the result remains unknowable and a retry could duplicate, charge, overwrite, or delete, ask one concise phone-tappable confirmation.
- Prefer atomic artifact creation, preserve completed outputs, and checksum important archives or uploads when useful. Do not re-download, re-render, or re-upload unchanged outputs.
- Parallelize independent safe checks, reuse verified results, compress large deliveries, and send small previews. When `/fast` is available and latency is the user's priority, offer it once as a phone-tappable choice with any quality or cost tradeoff; never switch silently.
- Recognize that remote execution depends on the required host staying awake, online, and connected. Never assign power-setting work to a user who is already remote. If the host is unreachable, preserve state and offer only phone-doable retry, notification, cloud, or partial-result alternatives. Use a temporary keep-awake mechanism only when explicitly authorized; never change permanent power settings silently.
- For multi-turn work, offer a durable goal or completion notification when available, but create a goal only when the user explicitly requests it.

## Deliver images without forcing compaction

Apply these rules to generated images, screenshots, scans, plots, rendered document pages, and visual QA:

- Send no more than **two inline images in one assistant message**. Use one image for a full-resolution or unusually large visual.
- Split additional inline images across separate, clearly numbered messages such as `2 of 7`. Keep accompanying text to one short caption per image.
- For more than four images, prefer a cloud folder or one downloadable archive for the originals. Post at most one contact sheet and one representative preview inline unless the user specifically requests every image in chat.
- When the user requests every image inline, still enforce the one-or-two-image message limit and continue in sequential batches.
- Create a labeled contact sheet when it lets the user review many options from one image. Preserve full-resolution originals separately.
- Use broadly phone-compatible previews such as PNG or JPEG. Downscale or compress chat previews when helpful, but never replace or degrade the originals silently.
- Give every image a short stable filename or index so the user can respond with only a number.
- Do not resend unchanged visuals, embed base64/data URLs, or paste image bytes into chat.

Before a media-heavy delivery, record in the task plan what has been delivered and what remains so a compaction cannot cause duplicate or missing batches.

## Deliver files where the phone can reach them

Use this priority order:

1. Upload to a connected OneDrive-capable service when the user requests OneDrive or when a large set would overwhelm chat. Create a clearly named folder, preserve originals, return a tap-ready share/resource link, and verify the upload before claiming success.
2. Otherwise attach or render the artifact directly in chat using small, compact-safe batches.
3. For many files, provide one phone-downloadable ZIP plus a concise manifest instead of many individual attachments.
4. If neither cloud upload nor chat attachment is available, explain the limitation and offer a phone-doable fallback. A raw local filesystem path does not count as delivery.

Use an available Microsoft 365, SharePoint, Graph, or OneDrive connector only after verifying that it actually exposes the user's intended OneDrive location. Do not claim cloud delivery from a local copy alone.

Choose mobile-friendly outputs by default:

- Provide PNG/JPEG for images, PDF for easy document review, MP4 with common codecs for video, and CSV or XLSX for data.
- Include an editable original in addition to the review format when useful.
- Use short descriptive filenames without ambiguous versions such as `final-final`.
- Put the direct tap target near the start of the handoff. Do not bury links in a wide table or a long paragraph.

## Keep chat compact and resumable

- Keep commentary and final responses short, scannable, and outcome-first.
- Avoid wide tables, large code blocks, raw logs, verbose tool output, repeated context, and unnecessary screenshots.
- For code changes, use the native diff or review surface when available. Summarize changed areas, verification, and remaining risk instead of pasting a full patch into chat.
- Save lengthy diagnostics or reports as an artifact and summarize only the decision-relevant points in chat.
- Keep the resilience checkpoint current during multi-stage work, especially before media batches, uploads, publishes, deployments, or long-running commands.
- After context compaction or interruption, reconstruct state from the plan, files, and tool results. Do not ask the user to repeat information that can be recovered.
- Finish each handoff with a clear state: `done`, `still working`, or `blocked`, plus the one next phone-doable action only when one is required.

## Make links and previews remote-safe

- Use descriptive Markdown links or resource links that are easy to tap.
- Do not provide `localhost`, `127.0.0.1`, `file://`, or an absolute workstation path as the sole preview or download method.
- For a web app the user needs to try remotely, create an authorized phone-reachable deployment or secure tunnel when available. Prefer authenticated or expiring access for nonpublic work and state any expiry.
- Test web work at a representative phone viewport as well as the normal project viewport. Ensure touch targets, scrolling, forms, menus, and text work without hover or a physical keyboard.
- If a remote URL cannot safely be created, provide compact screenshots or a recorded preview and preserve the runnable project for later.

## Format mobile conversations

- Use short paragraphs and narrow lists instead of dense tables.
- Put the recommended choice first and number choices so a one-character reply works.
- Avoid asking several unrelated questions at once.
- Do not paste commands for the user to run unless they explicitly request commands for reference; never make running them a requirement in this mode.
- Report successful uploads, sends, publishes, or destructive changes only after verifying the resulting state.
- Mention a local save path only as secondary diagnostic information after a phone-accessible delivery method is already present.

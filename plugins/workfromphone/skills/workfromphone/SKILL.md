---
name: workfromphone
description: "Phone-first operating mode for completing Codex work while the user is remote, on a phone, away from the workstation, unable to access the computer, or explicitly invokes $workfromphone. Keep the entire workflow usable from mobile chat: act autonomously on the computer, never assign desktop actions to the user, deliver files and pictures through chat or a connected cloud service such as OneDrive, keep image batches and context compact-safe, provide phone-reachable previews and links, minimize typing and decisions, and preserve continuity through long or compacted sessions."
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
- Maintain a concise plan or checkpoint containing the objective, important decisions, completed outputs, verification status, and next action during multi-stage work.
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

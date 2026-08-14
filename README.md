# Work From Phone

Work From Phone is a phone-first operating mode for ChatGPT and Codex. It keeps remote work usable when a phone is the user's only interface.

Invoke it with:

```text
$workfromphone
```

## What it changes

- Codex performs available workstation actions instead of assigning desktop chores to the user.
- Files and previews are delivered through mobile-reachable chat attachments, links, or connected cloud storage.
- Image delivery is limited to compact-safe batches of no more than two inline images per message.
- Larger media sets use a verified cloud folder, archive, or contact sheet.
- Long tasks preserve a concise checkpoint so work can resume after interruption or compaction.
- Questions and confirmations are kept short and phone-tappable.

## Install from GitHub

Add this repository as a Codex marketplace:

```text
codex plugin marketplace add wayjan/workfromphone
```

Then install `workfromphone` from the **Work From Phone** marketplace in the Plugins Directory. CLI users can install it with:

```text
codex plugin add workfromphone@workfromphone
```

Start a new chat and invoke `$workfromphone` when beginning a remote-work session.

## Package contents

- `plugins/workfromphone/` — distributable skills-only Codex plugin
- `.agents/plugins/marketplace.json` — Git-backed marketplace catalog
- `submission/` — public Plugins Directory listing and reviewer test cases

The plugin does not operate an external server or require an account.

## Support

Open an issue at <https://github.com/wayjan/workfromphone/issues>.

## License

MIT. See [LICENSE](LICENSE).

# NSC Tech Hub — Vetting Loop Checker

A lightweight, AI-powered quality assurance tool for the NSC Tech Hub. The Vetting Loop is the mandatory review process all project assets and specs must pass before reaching the development team.

---

## What it does

- **Stage 1 — Submission:** Department Liaisons submit assets or requirement specs to the Incoming queue.
- **Stage 2 — Validation:** The TPM runs an AI compliance review against `DESIGN_SPECS.md`. Assets that fail are returned to the liaison with a generated Reason for Revision note.
- **Stage 3 — Production Merge:** Approved assets are moved forward and developers are notified the task is ready for implementation.

---

## AI-powered features

**Compliance Review** — Claude checks each submission against the project's `DESIGN_SPECS.md` criteria, including file naming conventions, asset format and resolution requirements, code standards (commit messages, PR policy), and spec completeness (acceptance criteria, edge cases, dependencies).

**Reason for Revision Notes** — When an asset fails, Claude generates a formal, structured note citing the specific content that violated each rule and listing the required actions before resubmission.

---

## Usage

This is a single `index.html` file — no framework, no build step, no server required.

**To use it:**
1. Open the GitHub Pages URL for this repo.
2. Click **Submit new asset** to add an asset or spec to the Incoming queue.
3. Select an asset and click **Run AI Review**.
4. If it passes, advance it to Production. If it fails, generate a Revision Note and return it to the liaison.

**To update the spec:** Open `index.html` and replace the `DESIGN_SPECS` string in the `<script>` block with the latest version of your spec.

---

## Setup (API key)

The AI review features call the Anthropic API. To run this outside of the Claude.ai sandbox:

1. Get an API key from [console.anthropic.com](https://console.anthropic.com)
2. Open `index.html` and find the `fetch` calls to `https://api.anthropic.com/v1/messages`
3. Add your key to the headers: `"x-api-key": "sk-ant-YOUR_KEY_HERE"`

> **Note:** If this repo is private and for internal team use only, storing the key directly in the file is acceptable. Do not make the repo public with a live API key in the file.

---

## Repo structure

```
nsc-vetting-loop/
└── index.html       # The full application (HTML + CSS + JS)
└── README.md        # This file
```

---

## Governance

This tool enforces the standards defined in `DESIGN_SPECS.md`. For the full governance model see `GOVERNANCE.md` and `VETTING_LOOP.md` in the main NSC Tech Hub repository.

Work does not reach the development team until Stage 3 is cleared.

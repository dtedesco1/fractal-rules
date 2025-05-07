# 🧩 Fractal Knowledge Rules

*A zero-magic way to tell humans **and** AIs what every part of a codebase is, why it exists, and how it fits.*

---

## 📦 What’s in this repo?

| Path | Purpose |
|------|---------|
| `fractal_knowledge.mdc` | The **living spec** (v 3.2) – defines required tags, size limits, and x-ref pattern. |

That’s it for now—one rules file, **no tooling yet**. We’re iterating in the open.

---

## ⚙️ Core idea (60-second version)

| Traditional workflow | Fractal approach |
|----------------------|------------------|
| Context scattered across `.cursorrules`, Notion pages, chunky prompts | **Co-locate context with code** in a tag block or directory `README.mdc`. |
| Ask the AI *“What is this file?”* every time | AI parses tags in one shot → fewer re-prompts. |
| Docs drift because they live elsewhere | Tags ride the same PR / commit as the code they describe. |

A tag block can be **tiny or verbose**—five lines for a helper, twenty for a critical service. The point is: it lives exactly where it’s needed.

---

## 🚀 Right-now expectations

1. **Read the tags first** – treat them as ground truth (`<purpose>`, `<architecture>`, etc.).  
2. **Respect the size limits** – nudge when a dir hits > 5 children or a function > 100 LOC.  
3. **Update tags with code** – any change to behavior should patch the nearest tag block in the *same* diff.

That’s all. The `.mdc` file is a contract; enforcement tooling comes later.

---

## 🛣️ Where we want to go

| Milestone | Description | Help wanted |
|-----------|-------------|-------------|
| **CLI linter** | Scan repo, flag missing/invalid tags; suggest diffs. | ✅ |
| **GitHub Action** | Block PRs on linter errors & size breaches. | ✅ |
| **IDE plug-in** | Cursor / VS Code extension: insert template, hover preview. | ✅ |
| **Language adapters** | Go, Rust, Java tag helpers. | ✅ |
| **Auto-sync script** | Refresh `<contents>` lists from the file system. | ✅ |

Open an issue, claim a task, or propose a new milestone. Early adopters = design partners.

---

## ✏️ Quick start snippet

```python
"""<!--@fractal-doc-->
<purpose>
JWT auth service – fast stateless login
</purpose>

<architecture>
Redis cache -> Postgres fallback; tokens signed HS256, 15 m expiry.
</architecture>

<project_refs>
auth/db.py - data
common/crypto.py - utility
</project_refs>

<troubleshooting>
- Clock skew can invalidate tokens; sync NTP.
</troubleshooting>
"""
```

Commit and notice how much less context you need in your next AI prompt.

---

## 🤝 Contributing
-	Spec tweaks – confusing tag? better default? PRs welcome.
-	Examples – add real-world directory or function samples.
-	Automation – linter, GitHub Action, ESLint rule—anything that surfaces or enforces tags.
-	Critique – think Rule-of-5 is wrong? <security> should be mandatory? Tell us.

This project is an experiment, not a finished product—criticism and wild ideas encouraged.

---

## 📝 License

MIT – use it, fork it, bend it.

---

*Maintainer: [Daniel](https://dtedes.co) (@dtedesco1)*

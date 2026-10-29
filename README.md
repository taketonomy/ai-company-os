# ai-company-os

[English](README.md) | [日本語](README.ja.md)

**An OS for an organization that keeps doing useful work without people.**

![ai-company-os organization diagram](docs/org.png)

*The diagram labels are in Japanese.*

## The idea

- **Value is determined outside the organization.** Work only counts when it benefits society, users, or communities.
- **Design in this order:** Outcomes → acceptance criteria → the people (agents) who create the deliverables.
- **Just one at each layer:** One secretary AI and one Managing Director AI (MD). Do not add more MDs.
- **Workers are peers.** Workers assigned to one-off tasks finish their assignments when the work is done, recording what they have learned before their assignments end. For recurring categories of work, the same worker may be retained ([`workers/README.md`](workers/README.md)).
- **Gradually reduce the human role:** CEO → Owner → Auditor. Emergency-stop authority and legal ownership remain with humans throughout.

## OS mapping

| OS | ai-company-os |
|---|---|
| Kernel | Managing Director AI (MD): memory, acceptance criteria, and decision thresholds |
| Process | Task-assigned AI (worker): starts for each task and finishes its assignment upon completion |
| Daemon | Retained worker AI: continues handling recurring categories of work |
| Filesystem | `tasks/*.md`: the canonical task records. Lessons learned are summaries, so retain them alongside links to primary sources |
| Shell, I/O | Secretary AI (secretary): the interface to the outside world |
| Permissions | Thresholds: ACCEPT / WARN / ESCALATE / BLOCK |
| Apps | Individual projects |

## Layout

```text
secretary/   Secretary AI role definition
md/          Managing Director AI role, acceptance criteria, and decision thresholds
workers/     Worker AI templates, onboarding, and handover procedures
tasks/       Tasks managed as Markdown files (canonical task records with links to primary sources)
docs/        Diagrams and design notes (design-notes.md: additional context and open questions)
```

## Framework vs. instance

This repository is **the OS itself**: a framework anyone can use. To run an organization, each user sets up a separate **private instance repository** for the MD's memory, real tasks, and project records.

**Use one criterion:** Can someone use this as-is without knowing the specific user or project?

- Yes → This repository (role definitions, templates, the threshold framework, and operating rules)
- No → The instance repository (memory, real tasks, specific thresholds, people's names, and project names)

**Rules**

- Do not put instance-specific information in this repository, including people's names, project names, memory, or credentials.
- When in doubt, keep it in the instance repository. You can publish it later, but publication cannot be undone.
- Generalize improvements discovered while running an instance by removing instance-specific information, then contribute them back to this repository through a PR.

## Status

Early concept. It will be piloted on one project first, then expanded to others if it works well.

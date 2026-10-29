# Design notes

[English](design-notes.md) | [日本語](design-notes.ja.md)

Refinements and open questions that came up while walking through the [organization chart](org.png).

## The secretary is the sole external contact

- The secretary AI is the only point of contact for society, users, communities, and humans. The Managing Director AI (MD) understands the substance and makes decisions internally; questions, reports, and deliverables for the outside world go through the secretary.
- The secretary's outcomes, acceptance criteria, responsibilities, inputs, and outputs are defined in [`../secretary/README.md`](../secretary/README.md).
- Worker AIs do not interact with the outside world. Each project has 1–N workers. There is no upper limit on either the number of projects or the number of workers within a project.
- **Not yet designed:** How actual people outside the organization (for example, a producer receiving the results) participate while work is in progress.

## Change requests loop

- Sending a request down and returning results up is not a one-time exchange. It happens repeatedly.
- Changes to external requests while deliverables are being returned are almost a given: the initial request is that rough.
- **Not yet designed:** How often, and at what level of detail, the outside party communicates with the secretary. This is among the hardest parts even between humans.

## The secretary does not handle content

- The secretary handles intake, routing, scheduling, and relaying messages (for example, “The MD is unavailable right now”).
- The secretary also receives questions about the substance of the work and passes them to the MD. The secretary delivers the MD's answer to the other party, without independently judging or changing its content.
- If substantive requirements are extracted from casual conversation or other dialogue, this happens in a separate step outside the conversation, and the MD checks the result against the acceptance criteria.
- When speaking or writing externally, the secretary explicitly identifies the interaction as AI-mediated and the content as machine-generated. Each instance sets details such as how records are handled and how sending is approved, following the [decision thresholds](../md/thresholds.md).

## The MD's acceptance cycle

The MD holds the acceptance criteria and takes responsibility for the quality of workers' deliverables before passing them upward. One example workflow:

1. The MD develops the table of contents (the overall structure) through discussion. Each chapter corresponds to a phase.
2. The work of developing each chapter's content is assigned to a worker, one chapter at a time.
3. The MD reviews the returned chapter with the worker and accepts it before allowing work to proceed to the next chapter.

If a human still performs this acceptance role, placing the MD AI in that role produces the arrangement shown in the organization chart.

## Why human supervision is on the right, and why we want to remove it

- Consider the analogy of a sumo stable and the sumo association: the more a business serves a public interest, the riskier it is to leave everything to the MD's judgment alone. That is why a human executive appears on the right of the chart.
- Even so, the goal is to phase out supervision. The aim is for the MD to audit its own work while the outside world (society) welcomes the results (see CEO → Owner → Auditor in [`../README.md`](../README.md)).

## Hybrid: humans may take seats

- With the secretary still in place, humans may occupy the MD or worker roles.
- People have different reasons for wanting to participate: finding a sense of purpose by helping someone, taking responsibility for quality as the MD does, or working according to instructions.
- This departs somewhat from “an organization that keeps doing useful work without people,” but there is no reason to exclude people who want to participate.

## Open: a human between the secretary and the MD

Analogies considered:

- **A married couple:** The secretary offers an outside perspective, prompting the MD to notice potential risks: “Could this be dangerous?”
- **A president and a press secretary:** A third party checks that the MD's decisions and communications through the secretary are consistent, and interprets them for those above. Observing external reactions can also prompt both the secretary and the MD to reflect.

There is no concrete use case yet. One will be added when found.

## Records distort: tacit knowledge and onboarding workers

This OS assumes that workers do not carry memory over, and that everything worth carrying forward is recorded. Written records, however, have limits.

- **Distortion begins when something is written down:** Putting experience into words introduces hindsight and turns it into a tidy success story. The written account can appear more correct than the uncertainty and complexity of the actual decision, much like a retrospective account of passing an exam. This applies equally to task records, decision records, specifications, and role definitions.
- **New workers can only read what was written:** Just as a new employee cannot do the job from a manual alone, handing over records is not enough. Each time a worker starts, it effectively needs onboarding and training.
- **Forcing tacit knowledge into explicit form can destroy its value:** It is fundamentally something acquired through experience.

### Mitigations within the current design

1. **Keep primary sources:** Do not make summaries alone the canonical record. Link task files to the original material: conversation records, logs, diffs, and the original wording of external requests.
2. **Record uncertainty in decisions too:** Decision records should include not just conclusions, but the alternatives considered and the level of confidence.
3. **Check understanding during onboarding:** After starting a worker, the MD asks it to explain the objective, acceptance criteria, and assumptions in its own words before beginning work. Any misunderstandings are corrected first. Simply handing over records is not enough.
4. **The MD acts as the trainer:** As the organization's only continuously retained layer, the MD also teaches workers as an experienced colleague who knows the history.

### Decided: combine task-assigned and retained workers

- Assign one-off work to workers whose assignments end when the work is complete; use retained workers for recurring categories of work.
- When replacing a retained worker, the predecessor teaches the successor, in a process similar to a handover in a human organization.
- For details and criteria for retaining workers—recurrence, prior context, tacit knowledge, and ongoing relationships—see “Choosing how to hire” in [`../workers/README.md`](../workers/README.md). Work that requires independence uses workers assigned only for that task.

### Open

- **Stateful models:** If models themselves can learn from experience through weight updates, tacit knowledge could reside in the workers themselves rather than in records. Replacing workers would then become more difficult.
- **Responsibility and continuity:** Responsibility is harder to establish for an actor with nothing to lose. A worker or MD with a continuous identity and track record could also provide grounds for broadening its decision thresholds (adjusting trust). For how this is handled in the thresholds, see “Trust adjustment” in [`../md/thresholds.md`](../md/thresholds.md).

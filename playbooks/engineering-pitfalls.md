## Common Engineering Pitfalls & How We Avoid Them

| Pitfall                              | How We Tackle It                                                                                                                                                            |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Shiny‑object tech adoption**       | Run a cost‑benefit spike, capture an ADR, and tie adoption to a measurable business outcome (see *Research*).                                                               |
| **Scope creep & hidden work**        | Flag "3‑point" stories as red → unpack into spikes or split tickets before sprint start (see *Plan*).                                                                       |
| **Quality erosion & flaky releases** | Feature flags, robust e2e test suite, and peer reviews baked into our DoD (see *Build*).                                                                                    |
| **Design hand‑off gaps**             | Pre‑implementation walkthrough with PM, UX, QA, Lead Dev to clarify workflows & edge‑cases (see *Plan*).                                                                    |
| **End‑to‑end blind spots**           | Prioritise workflow‑level e2e tests over micro‑unit tests to protect real user journeys (see *Build*).                                                                      |
| **Last‑minute surprises**            | Red/Yellow/Green Slack check‑ins before stand‑up so we unblock yellows & reds fast (see *Accountability*).                                                                  |
| **Performance regressions**          | Define SLOs, instrument metrics, and hold **tech‑debt grooming sessions** to create tickets and lobby value during sprint planning-keeps reliability high (see *Optimize*). |
| **Invisible PR changes**             | Auto‑deploy PR preview environments so reviewers can click through features, not just read diffs (see *Build*).                                                             |
| **Risk‑blind code reviews**          | Tag each PR with Low/Med/High risk so the team can focus deep checks on high‑impact, cross‑over changes (see *Build*).                                                      |
| **Tribal knowledge loss**            | ADRs, diagrams, and quarterly doc‑sprints leave a clear artifact trail for future devs (see *Document*).       

---
name: migration-stories
description: Brainstorm migration paths and generate empathy-driven user stories for Konveyor product development and end-user migration planning. Use when exploring a new migration scenario, understanding customer pain points, or generating user stories for a technology transition.
argument-hint: [technology-or-scenario]
---

# Migration Story Generator

Brainstorm migration paths and generate user stories grounded in customer empathy. Produces stories that drive both Konveyor product development and end-user migration planning.

The migration scenario to explore: **$ARGUMENTS**

## Konveyor Supported Ecosystems

Konveyor currently supports analysis and migration for these languages and ecosystems:

**Languages with analyzer providers:**
- Java (via Eclipse JDT.LS) — deepest support, 2400+ pre-built rules
- Go (via gopls)
- Python
- Node.js
- C# (via c-sharp-analyzer in the konveyor org)

**Major migration paths with existing rulesets:**
- Java EE / Jakarta EE to Quarkus
- Java EE to Spring Boot
- Spring 5 to Spring 6
- EJB to CDI / REST
- Netflix OSS patterns to Kubernetes-native
- .NET Framework to .NET Core
- Legacy session/clustering to cloud-native patterns
- Monolith to microservices (general patterns)

**Infrastructure migrations:**
- Cloud Foundry to Kubernetes
- Docker Compose to Kubernetes
- VM-based workloads to containers

**Konveyor components:**
- **Kantra** — CLI for static code analysis across supported languages
- **Kai** — AI-assisted refactoring using RAG with organizational knowledge (supports Java, Go, TypeScript, C#)
- **Hub** — Application inventory, assessment, and migration tracking at scale
- **Rulesets** — Community-driven YAML rules for detecting migration issues
- **Platform Awareness** — Platform-level insights for migration decisions

Discovery and story generation should be grounded in these ecosystems. Scenarios outside current support are valid if they represent expansion opportunities — flag them as such.

## Input Modes

Adapt based on what was provided:

- **No argument / open-ended** (e.g., "what's trending?", "any catchy stories?"): Start with **Phase 0: Discovery** to research and propose compelling migration scenarios
- **Technology name only** (e.g., "nginx-ingress"): Skip discovery, go directly to **Phase 1: Migration Landscape**
- **Pre-researched scenario**: Skip discovery, structure provided context starting at **Phase 1**

## Process

Build the document iteratively, pausing after each phase for feedback before continuing.

### Phase 0: Discovery (Optional)

**Trigger:** No specific scenario provided, or user asks what's interesting/trending/catchy.

**Skip this phase** if the user already knows what migration they want to explore.

Search for compelling migration scenarios within the supported ecosystems listed above. Look for scenarios with:
- **Urgency** — hard deadlines, EOL announcements, security forcing functions
- **Scale** — large user populations affected
- **Pain** — migrations that are genuinely difficult, not just version bumps
- **Konveyor fit** — scenarios where Konveyor's capabilities (analysis, AI refactoring, rulesets) would clearly help

Present 3-5 migration scenarios as short pitches:

```markdown
### 1. [Scenario Title]
**What's happening:** [1-2 sentences]
**Why it's compelling:** [urgency / scale / pain / Konveyor fit]
**Ecosystem:** [Java / Python / .NET / Go / Kubernetes / Infrastructure]
```

Then pause:
> "Which of these interests you? Or do you have a different scenario in mind?"

Once the user picks a scenario (or provides their own), proceed to Phase 1.

### Phase 1: Migration Landscape

Research or ingest the migration context. Produce a brief summary covering:

- **What is changing?** (deprecation, EOL, new standard, compliance requirement)
- **Who is affected?** (scale — how many users, teams, organizations)
- **What is the timeline?** (deadlines, sunset dates, enforcement dates)
- **What are the migration paths?** (2-3 primary options with trade-offs)
- **What does Konveyor already offer for this?** (existing rules, analyzers, AI capabilities)

Keep this section to 200-300 words. Then pause:
> "Does this landscape summary capture the situation accurately? Any corrections or additions?"

### Phase 2: Persona Development

Identify 3-4 distinct personas affected by this migration. **Do not use fictional names** — use role titles only (e.g., "Platform Engineer", "Backend Developer"). Before presenting, check for overlap between personas and merge any that share similar pain points or authority levels.

For each persona, define:

```markdown
#### Persona [N] — [Role Title]

**Background:** [1-2 sentences on their role and daily responsibilities]
**Technical depth:** [Novice / Intermediate / Expert with this technology]
**Migration authority:** [Decision maker / Implementer / Affected user]
**What keeps them up at night:** [Their primary worry about this migration]
```

Personas should span the decision chain — from the architect choosing the path, to the developer doing the work, to the platform team managing the infrastructure. Prefer fewer, sharper personas over broad coverage. If two roles would have nearly identical pain points, merge them.

Present all personas, then let the user choose which to focus on for the remaining phases:

> "Which personas do you want to deep-dive on? Pick 1-3 to carry forward into empathy maps and story generation, or say 'all' to keep them all."

Only the selected personas carry forward into Phases 3-5. This keeps the output focused and avoids generating stories for personas the user doesn't care about.

### Phase 3: Empathy Mapping

For each persona, build an empathy map:

```markdown
#### Persona [N] — [Role Title] — Empathy Map

**Thinks:**
- [Internal thoughts about the migration — fears, calculations, trade-offs]

**Feels:**
- [Emotional state — overwhelmed, frustrated, cautious, excited, uncertain]

**Says:**
- [What they express to colleagues, management, or in meetings]
- [Direct quotes or paraphrased statements they'd realistically make]

**Does:**
- [Actions they take — research, POCs, escalation, avoidance, workarounds]

**Pain Points:**
1. [Specific, concrete pain point with context]
2. [Another pain point]
3. [Another pain point]

**Goals:**
1. [What success looks like for this persona]
2. [Secondary goal]

**Unspoken Needs:**
- [Things they need but won't explicitly ask for — confidence, validation, a safety net]
```

Then pause:
> "Do these empathy maps ring true? Any pain points missing or overstated?"

### Phase 4: Konveyor Opportunity Analysis

Identify where Konveyor can help across its available capabilities:

| Konveyor Capability | Opportunity | Impact |
|---------------------|-------------|--------|
| **Analysis (Kantra)** | [What rules or analyzers could detect migration needs] | [High/Medium/Low] |
| **AI-Assisted Refactoring (Kai)** | [How Kai could automate parts of the migration] | [High/Medium/Low] |
| **Rulesets** | [What new rules would be needed] | [High/Medium/Low] |
| **Migration Planning (Hub)** | [How the hub could track this migration at scale] | [High/Medium/Low] |
| **Platform Awareness** | [How platform-level insights could guide migration decisions] | [High/Medium/Low] |

Highlight gaps — areas where Konveyor has no current capability but should.

Then pause:
> "Does this opportunity mapping align with your view of where Konveyor should invest? Any capabilities I'm missing?"

### Phase 5: User Story Generation

Generate two sets of stories:

#### A. Konveyor Product Stories
Stories for the Konveyor team to build features that address this migration.

```markdown
---
### Story K-[N]: [Title]

**Persona:** [Which persona this serves]
**Empathy context:** [1-2 sentences connecting this story to a specific pain point or emotional need from the empathy map]

**Story:**
As a [persona], I want [Konveyor to provide/enable X], so that [I can achieve Y without Z pain].

**Acceptance Criteria:**
- [ ] [Concrete, testable criterion]
- [ ] [Another criterion]
- [ ] [Another criterion]

**Konveyor component:** [Kantra | Kai | Rulesets | Hub | Platform Awareness]
**Priority signal:** [Why this matters — urgency, user count, pain severity]
---
```

#### B. End-User Migration Stories
Stories for a team executing this migration, showing how Konveyor fits into their workflow.

```markdown
---
### Story M-[N]: [Title]

**Persona:** [Who executes this]
**Empathy context:** [What they're feeling at this stage of the migration]

**Story:**
When [situation/trigger], I want to [action], so I can [outcome].

**Steps with Konveyor:**
1. [How Konveyor helps with this step]
2. [Next step]

**Without Konveyor:** [What this looks like without tooling — manual, error-prone, slow]

**Definition of Done:**
- [ ] [Measurable completion criterion]
---
```

Generate 5-8 stories per set, ordered by migration phase (assess -> plan -> execute -> validate).

Then pause:
> "Do these stories capture the right priorities? Should I adjust scope, add edge cases, or reframe any?"

### Phase 6: Assembly

Combine all validated sections into a single document.

**Output location:** `docs/migration-stories/YYYY-MM-DD-<topic>.md`

**Document structure:**

```markdown
---
date: YYYY-MM-DD
topic: <kebab-case-topic>
personas: [list of persona names]
konveyor-components: [list of relevant components]
migration-type: [deprecation | compliance | modernization | platform-shift]
---

# Migration Stories: [Topic Title]

## Migration Landscape
[Phase 1 content]

## Personas
[Phase 2 content]

## Empathy Maps
[Phase 3 content]

## Konveyor Opportunity Analysis
[Phase 4 content]

## Konveyor Product Stories
[Phase 5A content]

## End-User Migration Stories
[Phase 5B content]

## Open Questions
- [Unresolved questions surfaced during brainstorming]

## Next Steps
- [ ] Prioritize Konveyor product stories for backlog grooming
- [ ] Validate personas with real users or customer interviews
- [ ] Create detailed plans for high-priority stories
```

## Principles

- **Empathy first, stories second** — Never generate stories without understanding the human experience
- **Concrete over abstract** — Use real technology names, real deadlines, real constraints
- **Both backlogs matter** — Every session should produce value for Konveyor's roadmap AND for end users
- **Challenge assumptions** — Ask "is this actually painful?" and "would users really do this?"
- **YAGNI applies** — Don't invent migration problems that don't exist; focus on validated pain points
- **Iterate** — Pause after each phase; course-correct early rather than rewriting later

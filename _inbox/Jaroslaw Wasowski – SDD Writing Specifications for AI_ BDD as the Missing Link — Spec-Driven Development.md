---
title: "SDD Writing Specifications for AI: BDD as the Missing Link — Spec-Driven Development"
author:
  - "Jaroslaw Wasowski"
published: 2026-04-28
source: "https://medium.com/@wasowski.jarek/sdd-writing-specifications-for-ai-bdd-as-the-missing-link-spec-driven-development-ad1b540b7f75"
image: "https://miro.medium.com/v2/resize:fit:1200/1*sOB8nCSssnyNJpNdl8TJng.png"
created: 2026-05-31
tags:
  - "veille-tech"
  - "medium"
  - "agent-ia"
  - "architecture"
status: "active"
---
---
title: "SDD Writing Specifications for AI: BDD as the Missing Link — Spec-Driven Development"
author:
  - "[[Jaroslaw Wasowski]]"
published: 2026-04-28T15:55:18Z
source: "https://medium.com/@wasowski.jarek/sdd-writing-specifications-for-ai-bdd-as-the-missing-link-spec-driven-development-ad1b540b7f75"
image: "https://miro.medium.com/v2/resize:fit:1200/1*sOB8nCSssnyNJpNdl8TJng.png"
created: 2026-05-31T12:16:42+02:00
tags:
  - "veille-tech"
  - "medium"
status: draft
---
![SDD Writing Specifications for AI: BDD as the Missing Link — Spec-Driven Development](https://miro.medium.com/v2/resize:fit:1200/1*sOB8nCSssnyNJpNdl8TJng.png)

> BDD is the missing specification language in the era when AI writes code. One Given/When/Then scenario = business spec + unit, integration, E2E, UAT, and regression tests.

---

## Mes notes

En 2026, les ingénieurs ne codent plus — ils spécifient. Le SDD (Spec-Driven Development) fait consensus, mais la forme de la spécification reste ouverte. Cet article de Wasowski argumente que les formats traditionnels (SRS, HLD, LLD) échouent comme contrats pour les agents IA : trop vagues ou trop détaillés. Le BDD (Behavior-Driven Development) serait le chaînon manquant — la syntaxe Given/When/Then opère exactement au bon niveau d'abstraction, lisible par le métier et exécutable par la machine. Un scénario BDD génère automatiquement 5 niveaux de tests (unit, intégration, E2E, UAT, régression), réduisant le coût de production d'une feature de 60 à 80 % (étude BMW/CRITICAL Software : €0.12/script). Le rituel "Three Amigos" — 30 min/semaine — permet d'intégrer cette pratique sans outils nouveaux. Très actionnable pour un contexte DevOps/Cloud en pivot SaaS où la rigueur de spécification conditionne la qualité des agents.

**Notes liées :** [[4-lines-every-claude-md-needs]], [[production-ready-ai-agents-mcp-cli-skills]], [[personal-harness-llm-wiki-obsidian]]

## Points clés

- **BDD comme spécification exécutable** : les scénarios Given/When/Then sont le seul format lisible par le métier *et* directement exploitable par un agent IA sans traduction — ils opèrent au bon niveau d'abstraction entre SRS (trop vague) et LLD (trop détaillé).
- **Un scénario = 5 niveaux de tests** : unit, intégration, E2E, UAT et régression générés depuis un seul artefact — réduction estimée à 60–80 % du coût par feature, validée empiriquement à €0.12/script (AutoUAT / BMW+CRITICAL Software).
- **Le rôle de l'ingénieur a changé** : de codeur (2015) → prompt engineer (2023–2025) → *facilitateur de contrats métier/machine* (2026) ; la spec est le nouvel artefact primaire dans le dépôt.
- **Three Amigos en 30 min/semaine** : PM + dev + testeur écrivent ensemble le `.feature` file, l'IA génère code et step definitions — zéro outil nouveau, ROI mesurable dès le premier sprint.
- **CLAUDE.md/AGENTS.md comme garde-fou** : fichier Markdown dans le repo qui porte les principes architecturaux persistants et évite de les répéter dans chaque prompt agent.



---

## Article complet

## BDD is the missing specification language in the era when AI writes code. One Given/When/Then scenario = business spec + unit, integration, E2E, UAT, and regression tests.

I remember the day I handed my team an 80-page SRS and thought I was brilliant. A senior developer read three pages, looked at me, and said calmly: “Which part of this is supposed to work?” That was 2018. In 2026, I have the same senior — but now he goes by Claude Code, and he’s not that polite.

The question hasn’t changed; only the tone has. The AI that writes our code today doesn’t forgive ambiguity the way a seasoned colleague used to. **A specification stopped being an archival document and became an execution contract.** The real question of 2026 isn’t “do we need Spec-Driven Development” — it’s **what exactly belongs in that specification**.

> *“If you can’t explain it simply, you don’t understand it well enough.” — Attributed to Albert Einstein, Theoretical Physicist*

## Table of Contents

- **What We Write Now That AI Writes Code** — the shift in the human artifact from code to intent, and why SDD is the industry’s answer
- **Traditional Engineering Documentation Isn’t Enough** — why BRS, SRS, HLD, and LLD fail as contracts for AI
- **BDD as the Missing Language** — the anatomy of a Given/When/Then scenario and the mechanism of two-way reading
- **One Scenario, Five Levels of Tests** — the dual value of BDD and the economics of software production
- **Three Amigos in the AI Era** — a practical workflow for incorporating BDD into an existing SDD pipeline

Check out how to effectively manage context using SDD in my publication: [Managing Agent Context at Every Stage of the SDLC](https://medium.com/@wasowski.jarek/managing-agent-context-at-every-stage-of-the-sdlc-cdlc-sdd-cecd0d575064)

## What We Write Now That AI Writes Code

Something fundamental happened to our profession between 2023 and 2026, and almost no one named it directly. **Engineers no longer write code — they describe what the code should do.** The keyboard is the same, the IDEs are the same, but the artifact we leave behind in the repository has shifted one level of abstraction upward. Code became a byproduct of intent, not the intent itself.

The industry is captivated by the term **SDD (Spec-Driven Development)** — an approach where the specification, not code, is the primary engineering artifact. GitHub shipped Spec Kit, AWS shipped Kiro, Tessl raised a combined $125 million (a $25 million seed round plus a $100 million Series A) on the premise that code is the “compiled binary” of a specification. Everyone agrees on one thing: **the spec has become the primary artifact — but what kind of spec?**

![A two-column diagram comparing the engineer’s role in 2015 (human artifact = code) and 2026 (human artifact = specification, with an open question about its shape).](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*-w-DuJZhfVnzylrsigYlPw.png)

The paradigm shift 2015→2026. The engineer operates higher in the software production stack — and the question of what a specification looks like becomes a question of professional identity.

Andrej Karpathy called this shift **Software 3.0** — a new era where the source artifact is a description of intent in natural language, not code. “The hottest new programming language is English,” Karpathy wrote in 2023 — and he was right, though the irony of that statement only revealed itself later. Because English (and Polish, and every natural language) is inherently ambiguous. What gave us power in human communication turns out to be the greatest weakness in communication with an agent.

Sean Grove of OpenAI made the sharpest case in his widely discussed talk “The New Code”: **specifications, not prompts and not code, are becoming the fundamental unit of programming**. If he’s right, then every team lead in 2026 faces a question they never had to answer consciously before: what shape should the document take when its reader isn’t a senior with ten years of domain experience, but an agent with a 200,000-token context window and zero organizational memory?

### Why the Default Choice Fails

Agreement on the direction doesn’t close the question of shape. Is a spec a user story on a Jira card — an OpenAPI file — an 80-page prose document — an architectural constitution in Markdown? Each of these approaches is called “SDD” today, and most teams choose between them **not consciously, but by habit**.

What makes the difference is exactly that default drift — and it explains why three teams with the same Cursor get three radically different productivity results. The natural answer to “what should be in the spec?” is: “what we’ve always written — SRS, HLD, LLD.” **That’s exactly the answer that fails.**

## Traditional Engineering Documentation Isn’t Enough

The classic hierarchy of engineering artifacts was our professional alphabet for three decades. **BRS (Business Requirements Specification)** — a business document describing requirements from the organization’s perspective, a precursor to the SRS. **SRS (Software Requirements Specification)** — a classic engineering document describing functional and non-functional requirements, typically 50–200 pages of prose. **HLD (High-Level Design)** — an architectural document describing system components and their interactions. **LLD (Low-Level Design)** — a detailed document describing the internal structure of modules: classes, methods, and call sequences.

In theory, the hierarchy is beautiful. In practice — for the past two decades — it worked mainly because *the senior developer filled in the gaps*. All four formats were supposed to be unambiguous, and all four always had holes. Those holes were patched with domain memory and a dense network of informal hallway conversations. AI doesn’t have that network, doesn’t walk the hallways, and ==doesn’t pretend to know what it doesn’t know.==

![A vertical diagram of seven specification layers from a loose PM note to a detailed LLD, with the missing layer marked between SRS and HLD.](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*xWE3VG2p8PTv-E-JiT6ajw.png)

The specification spectrum from loose to detailed. Each existing layer fails for a different reason — a layer is missing in the middle, between the business description and the technical design.

### Two Kinds of Mismatch

**First problem: BRS and SRS are too loose in business terms for AI.** Open any SRS that passed through your team in the past five years and find a sentence like “The system shall provide secure authentication.” The senior developer read that, nodded, and knew it meant 2FA with TOTP because that particular client had PSD2 compliance requirements. The coding agent doesn’t have access to that knowledge. It’ll generate a password with minimal complexity requirements and move on — because all lines compile just fine.

**Second problem: HLD and LLD are too technically detailed.** Writing an LLD in the AI era is practically writing the code yourself — you’re defining classes, methods, and call sequences. You lose the value of AI because you’ve done 80% of the design work the agent was supposed to do. HLD operates at the level of components and interfaces — but it doesn’t define *behavior* at the business function level. It says what the system is made of, not what it does.

Empirical evidence that this isn’t just my thesis came this year from an industry benchmark documenting LLM performance degradation with deliberately embedded requirements ambiguity. The result is unambiguous: ambiguity consistently degrades the quality of code generated by all tested models, and more advanced models lose proportionally more — because they fill the gaps more creatively. **Models can’t identify or resolve ambiguity on their own** — the more intelligent they are, the more creatively they guess at something other than what you had in mind.

In my experience, every team that complains about “AI Slop” and 3–4 iterations per ticket has the same structural problem. **It’s not about prompt quality or model fickleness. It’s about the input format.** Traditional documents fail as contracts for agents from both sides simultaneously: the SRS is too loose, the LLD is too detailed, and loose user stories are so shallow that the agent improvises all boundary conditions.

==**A layer is missing between the SRS and the code.**== ==A layer that describes behavior at the level of business functions — precise enough for an agent to implement, and readable enough for a PM to approve==. Since traditional documents don’t fit and loose user stories are too shallow, what’s missing in between? The answer is 22 years old.

## BDD as the Missing Language

> *“The limits of my language mean the limits of my world.” — Ludwig Wittgenstein, Philosopher*

On Christmas Eve 2003, Dan North registered the domain jbehave.org and wrote the first lines of a tool meant to replace JUnit. He wasn’t doing it to invent a new form of testing — he was solving a pedagogical problem: the developers he was teaching TDD kept getting stuck on the word “test.” North swapped the word “test” for the word “behavior” — and suddenly an entire category of questions about what to test disappeared. Writing behavior is natural. Writing tests isn’t.

From that pedagogical experiment grew **BDD (Behavior-Driven Development)** — a methodology for describing system behavior in natural language, readable by the business and executable by machines, using Given/When/Then scenarios. Over two decades BDD traced a spectacular arc: peak popularity in 2015, a long decline 2018–2024 (when SmartBear handed off Cucumber and Tricentis killed SpecFlow), then an unexpected renaissance in the AI era. That renaissance isn’t coincidental — and it’s not because BDD suddenly “works better.” It’s because *the reader BDD was designed for from the beginning finally appeared*.

### Anatomy of a Given/When/Then Scenario

All the magic of BDD fits in the three-part structure of a single scenario:

```sh
Feature: ATM cash withdrawal
Scenario: Sufficient balance
  Given the account balance is $100
    And the card is active
  When the customer requests a $20 withdrawal
  Then the ATM dispenses $20
    And the account balance is $80
```

This is **Gherkin** — the DSL used in `.feature` files to write BDD scenarios, based on the Given/When/Then keywords. The syntax matches the AAA pattern from unit tests (Arrange/Act/Assert), except, instead of assertions in code, we have sentences in the language of the business domain. Three lines are enough for a PM, client, BA, and tester to all know exactly the same thing — and for a coding agent to know exactly what they know.

What makes Gherkin remarkably powerful is its **two-way reading**. The PM sits in a review meeting, reads the scenario like a narrative, and nods — because the language here is the domain language (balance, withdrawal, card), not technical jargon. At the same moment, the BDD framework (Cucumber, Reqnroll, Behave) parses that scenario, maps each step to a **step definition** — code linking the Gherkin text to an executable test implementation — and runs it as an acceptance test. *The same document, two audiences, zero translation.*

![A Gherkin scenario in the center with two arrows: upward to a business person reading it as narrative, downward to an AI parser generating test code.](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*TVlg5B1UKdqUH5N2XmWDcw.png)

The same scenario, two audiences. The business reads it as a story, the machine parses it as a contract. No translation needed.

### Why AI Removes the Last Barrier

Historically, the cost of BDD was high: someone had to manually write step definitions and maintain them in parallel with the code. That was work no team ultimately wanted to do — and it’s what buried Cucumber in 2019. **In 2026, AI generates step definitions automatically from the scenario** — thereby removing the only real maintenance cost BDD ever had.

The empirical data is clear: research on BDD scenarios as LLM input shows a **pass@1** improvement (the measure of how many coding tasks a model solves on the first attempt) of 15.1% compared to unstructured natural language. The key observation: **BDD sits exactly between the SRS and the HLD on the precision axis**. It operates at the level of *user behavior* — the most important granularity for a coding agent, because that’s where business ambiguity lives. It’s not as loose as a user story, not as technical as an HLD, not as mechanically detailed as an LLD. It hits a sweet spot that software engineering had never formally defined before — because it never *needed* an executable artifact there.

Aslak Hellesøy, Cucumber’s creator, once said provocatively: *“BDD is not test automation — it’s collaborative requirements analysis combined with TDD.”* He was right, but only halfway. **BDD is both**, and, in the AI era, that duality becomes an unexpectedly powerful economic force.

## One Scenario, Five Levels of Tests

> *“Perfection is achieved not when there is nothing more to add, but when there is nothing left to take away.” — Antoine de Saint-Exupéry, Writer and Pilot*

This is where things get interesting. The real power of BDD in the AI era doesn’t lie in the *quality* of the generated spec or the *speed* of the generated code. It lies in the fact that **one artifact eliminates three separate processes**: the business specification, the test plan, and the technical documentation. That condensation — not better prompts — is the industry’s actual revolution.

### The Five-Level Fan

Take our ATM scenario. “A customer with a $100 balance requests a $20 withdrawal, and the ATM dispenses $20.” Three lines of Gherkin unfold into five layers of verification.

**Five test levels from a single source.** First, a **unit test** of each individual step in isolation — does “account debit” work for various values and edge cases? Second, an **integration test** of the group of steps with a mocked ATM backend — does the whole thing correctly call authorization? Third, an **E2E test** of the full scenario in a real test environment with a real database.

Fourth, **UAT** — the business clicks through the same scenario in the UAT environment and accepts it. Fifth, **regression** — the scenario running on every deploy protects against unintended changes in the future. **Five granularities, five separate verification layers, one source file.**

![An infographic showing a central Gherkin scenario generating a fan of five test levels: unit, integration, E2E, UAT, and regression.](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*sOB8nCSssnyNJpNdl8TJng.png)

The test fan from a single scenario. Before BDD-AI: five separate artifacts, five people, weeks of work. After: one scenario, AI fans out the rest.

### Production Data and the History of the Concept

This isn’t a hypothetical promise. The AutoUAT pipeline, described in an industry case study (Critical TechWorks — a joint venture of BMW Group and CRITICAL Software), implements exactly this flow: user story → Gherkin scenario → Cypress/TypeScript test script. Results: 95% of generated scenarios judged helpful, 92% of test scripts judged useful (60% without any changes, the rest after corrections or regeneration), an average cost of **€0.12 per script**. This isn’t “AI speeds us up a bit” — it’s an economic asymmetry that software production has never seen before.

Interestingly, the underlying idea is 25 years old. **Specification by Example** — a concept formalized by Gojko Adzic in his 2011 book (Manning, Jolt Award 2012) — is a method of specifying requirements through concrete, executable behavioral examples. Adzic defined six key patterns linking the spec with testing: deriving scope from goals, collaborative specification, illustrating with examples, automated validation, frequent validation, and evolving the documentation system. **The idea waited a quarter century for the era when it was economical to execute** — because it took AI to solve ==the problem of manually maintaining step definitions.==

When scenarios are executable and pass in CI/CD, *they are* the technical documentation. **Living Documentation** — documentation that’s always current because it’s simultaneously an executable test. It stops being documentation the moment it stops passing. That’s exactly the quality traditional engineering documentation could never guarantee — because it was *disconnected* from the code.

### The Economics of Dual Value

The scale is brutal when you do the math. For a typical e-commerce feature: in the old world, an analyst wrote an SRS for 20 hours, a tester wrote a test plan for 30 hours, a technical writer documented for 10 hours, plus 20 hours of synchronization between artifacts — 80 hours total of human work spread across three specialists and weeks on the calendar.

**In the BDD-AI model: Three Amigos write the Gherkin scenario together in 3 hours, and AI fans it out to five test levels in API hours, with costs counted in euros per script.** Based on my calculation — derived from the AutoUAT case study data and typical project workloads — the cost reduction per feature can reach 60–80% depending on the domain. I’ll say it plainly: **this isn’t “AI speeds us up” — this is AI eliminating four out of five artifacts.** This is the point where the AI productivity discussion stops being interesting and starts being urgent.

## Three Amigos in the AI Era

Adopting BDD as a spec layer into an existing SDD workflow doesn’t require new tools or executive approval. It requires a 30-minute **Three Amigos** meeting — a BDD practice formulated in 2009, consisting of a three-role meeting (business, developer, tester) around a single scenario before implementation — and a shift in artifact hierarchy: instead of an SRS → user story → code, it’s BDD scenario → AI generates code and tests → CI/CD executes. **Three people, 30 minutes a week, one** `**.feature**` **file.** That's enough.

![A diagram of three roles (PM, developer, tester) around a shared Gherkin scenario, with flow to AI generating code and tests in a single 30-minute weekly ritual.](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*77Ys0bPQfsj4kH1cuJZ3WA.png)

Three Amigos in the AI era. 30 minutes of collaborative scenario writing, a full test fan in API hours, documentation always current.

### Five Stages of the Ritual

- **Stage 1 — Discovery (5 minutes).** The PM narrates the story: “A customer in the banking app wants to check the balance on their savings account.” The tester immediately asks about edge cases: “what if the account doesn’t exist, what if the session expired, what if the customer has multiple accounts?” The developer asks about contracts: “where do we get the account list, what’s the format of the identifier?” The output of those five minutes: a list of scenarios to write, each with a clear context and action.
- **Stage 2 — Formulation (15 minutes).** Each scenario is written in Given/When/Then. Collaboratively, on screen, in a `.feature` file. Business domain language, not technical jargon.  
	Validation is brutally simple — we read the scenario aloud, it sounds natural, and all three people nod. **Concrete values, not abstractions**: “Given a customer with a balance of $1,000,” not “Given a customer with a positive balance.” Concrete values are exactly what AI understands best.
- **Stage 3 — AI Generation (API time).** The scenario is handed to an agent (Claude Code, Cursor, Copilot Workspace). The agent generates the implementation, step definitions, unit, and integration tests. A critical detail: the agent has in its context a **CLAUDE.md** or **AGENTS.md** file — a Markdown file in the repository that the agent reads as a persistent specification of the project’s architectural principles, acting as a guardrail between sessions. The rules you don’t want to repeat in every prompt live there.
- **Stage 4 — Verification (10 minutes).** The tester runs the scenario in E2E, and the business clicks through the UI in the UAT environment. Cucumber/Reqnroll generates a report readable by the business — “Sufficient balance: PASS. Account doesn’t exist: PASS.” We enable the **self-verification loop** — a mandatory agent step after implementation, where it compares the result against the specification and confirms all requirements are met. That one step eliminates most of the “almost works” iterations that consume sprints today.
- **Stage 5 — Living Documentation (automatic).** The scenario in CI/CD serves as documentation. Any code change that breaks a scenario blocks the merge. Documentation is *always* current by definition — because it stops being documentation the moment it stops passing. There’s no situation where the code does A, the documentation says B, and a senior has to guess which one is current.

### When Three Amigos, When Vibe Coding

A practical heuristic I’ve been using for months: for a feature with clear business behavior (CRUD, decision flows, forms, authorization) — Three Amigos is a must. For bug fixes under 50 lines and exploratory prototypes — vibe coding still makes sense. **Conscious choice, not default drift.** The senior developer used to fill in the gaps intuitively. In the AI era, that luxury is gone.

## Summary

The arc of this article closes in one sentence: **the industry has reached consensus that the specification is the primary engineering artifact — and simultaneously has no consensus on what that specification should contain.** Traditional BRS, SRS, HLD, and LLD fail as AI contracts for different reasons (too loose or too detailed), loose user stories are too shallow, and the missing layer in between is 22 years old and is called BDD.

The engineer’s role has changed three times in three years. **Through 2023, we were coders.** From 2023 to 2025 — prompt engineers. From 2026 — *contract facilitators* between the business and the machine.

What we leave behind in the repository isn’t lines of code — it’s scenarios describing behavior. The change is subtle, but its economic consequences are enormous.

Five things I take from this arc:

- **The specification has become the primary engineering artifact** — the “do we need SDD” question is settled; the open question is “what shape”
- **Traditional engineering documentation (BRS/SRS/HLD/LLD) fails with AI** — too loose in business terms or too detailed technically; the layer in between is missing
- **BDD is the missing language** — Given/When/Then operates at the behavioral level, simultaneously comprehensible to the business and unambiguous to machines
- **One scenario = five test levels** — unit, integration, E2E, UAT, and regression from a single artifact; feature production cost reduction estimated at 60–80%
- **Three Amigos in the AI era = 30 min/week** — an adoption ritual requiring no new tools and no executive approval, with measurable ROI from the first sprint

I’ll say it one last time, without diplomacy: **30 minutes of Three Amigos replaces 80 hours of feature production.** If this article changed how you think about specifications — take one Gherkin scenario from your next sprint and test it yourself. That’s the most honest hypothesis test I can offer.

![An infographic summarizing the full arc of the article: from the question of what specification looks like in the AI era, through the documentation layer hierarchy and the location of the missing link, to BDD fanning out to five test levels, to the practical Three Amigos ritual.](https://miro.medium.com/v2/resize:fit:2000/format:webp/1*_LgzkTonlJVLS11jayTf1g.png)

The full article arc in a single image. From the question “what do we write now” to the practical Three Amigos ritual — with BDD as the missing link between the business and the machine.

*Thank you for making it this far. If these 10 minutes were worth your time — pass the article to someone who’s fighting 3–4 iterations on every AI ticket every day. Follow the profile if you want to hear about future episodes. Share in the comments what spec format your team is using today. Comments from real projects are worth more than any theory.*

---

**Source :** [SDD Writing Specifications for AI: BDD as the Missing Link — Spec-Driven Development](https://medium.com/@wasowski.jarek/sdd-writing-specifications-for-ai-bdd-as-the-missing-link-spec-driven-development-ad1b540b7f75)  
**Auteur :** Jaroslaw Wasowski  
**Clipé le :** 2026-05-31T12:16:42+02:00

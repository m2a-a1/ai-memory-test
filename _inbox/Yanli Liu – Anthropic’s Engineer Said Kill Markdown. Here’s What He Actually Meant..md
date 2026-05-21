---
title: "Anthropic’s Engineer Said Kill Markdown. Here’s What He Actually Meant."
author:
  - "Yanli Liu"
published: 2026-05-15
source: "https://medium.com/generative-ai/anthropics-engineer-said-kill-markdown-here-s-what-he-actually-meant-36bee00c0ca2"
image: "https://miro.medium.com/v2/da:true/resize:fit:1200/0*ITstR02aTfQsF2bV"
created: 2026-05-18
tags:
  - "veille-tech"
  - "medium"
  - "agent-ia"
  - "architecture"
status: "active"
---
---
title: "Anthropic’s Engineer Said Kill Markdown. Here’s What He Actually Meant."
author:
  - "[[Yanli Liu]]"
published: 2026-05-15T00:07:40Z
source: "https://medium.com/generative-ai/anthropics-engineer-said-kill-markdown-here-s-what-he-actually-meant-36bee00c0ca2"
image: "https://miro.medium.com/v2/da:true/resize:fit:1200/0*ITstR02aTfQsF2bV"
created: 2026-05-18T09:22:35+02:00
tags:
  - "veille-tech"
  - "medium"
status: draft
---
![Anthropic’s Engineer Said Kill Markdown. Here’s What He Actually Meant.](https://miro.medium.com/v2/da:true/resize:fit:1200/0*ITstR02aTfQsF2bV)

> HTML vs Markdown ： Here’s the Decision Tree Both Sides Needed.

---

## Mes notes

Thariq Shihipar, ingénieur lead chez Anthropic sur Claude Code, a déclenché un débat viral en affirmant que Markdown est un reliquat de l'ère de rareté des tokens et qu'HTML offre une meilleure expérience pour les sorties d'agents. Yanli Liu analyse calmement les deux camps et propose un framework de décision simple : le format doit suivre le lecteur, pas la mode. Si un humain lit (rapport stakeholder, code review), HTML offre navigation, sections repliables et visualisations interactives. Si seul un agent consomme le résultat, Markdown reste optimal : léger, parseable, diffable. Si les deux lisent, la combinaison gagnante est Markdown source versionnable + artifact HTML pour les lecteurs humains. L'overhead de 3-5x en tokens est réel à grande échelle (~$513/mois pour 100 rapports/jour sur Sonnet), mais souvent inférieur au coût du temps ingénieur gaspillé à naviguer dans un mur de texte. Les risques HTML à adresser : XSS dans le JS généré par IA, accessibilité WCAG et diffs bruités.

**Notes liées :** [[4-lines-every-claude-md-needs]], [[personal-harness-llm-wiki-obsidian]]

## Points clés

- **Framework de décision en 3 cas** : Humain lit → HTML (navigable, partageable). Agent uniquement → Markdown (léger, parseable, diffable). Les deux → Markdown source + artifact HTML. La décision suit le lecteur, pas le format.
- **Le Token Trap** : débat souvent mal cadré. À l'échelle individuelle, la différence est négligeable (~$0.17/rapport sur Sonnet). À 100 rapports/jour, c'est ~$513/mois supplémentaires. Mais le coût du temps humain à parser un mur Markdown ($19-38 par ingénieur/session) dépasse souvent l'économie réalisée.
- **Markdown est « promu », pas mort** : il passe du rôle de format d'affichage à celui de protocole machine-readable. C'est son vrai rôle dans l'ère agentique — source versionnable et diffable, pas interface finale pour les humains.
- **Risques HTML à ne pas ignorer** : XSS via JS généré par IA (imposer contrainte no-external-CDN, no-network-calls-at-runtime), manque d'accessibilité WCAG par défaut (à prompter explicitement), diffs bruités (solution : template HTML fixe + payload JSON pour les données variables).
- **Incitations à surveiller** : Anthropic bénéficie directement du switch vers HTML (plus de tokens = plus de revenus API) — ce qui ne invalide pas l'argument mais mérite d'être conscient lors de l'adoption wholesale.

---

## Article complet

## HTML vs Markdown ： Here’s the Decision Tree Both Sides Needed.

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*ITstR02aTfQsF2bV)

Photo by Olia Gozha on Unsplash

[Read this for free](https://generativeai.pub/anthropics-engineer-said-kill-markdown-here-s-what-he-actually-meant-36bee00c0ca2?sk=9f51cf824236ec961e759f6c4de62345)

Last week, the engineering lead for Claude Code told developers to stop outputting Markdown. The internet lost its mind.

Thariq Shihipar, who leads engineering on Anthropic’s Claude Code, published [“The Unreasonable Effectiveness of HTML”](https://thariqs.github.io/html-effectiveness/) with 20 working examples. His argument: Markdown is a relic of the token-scarcity era. ==HTML gives you interactive navigation, collapsible sections, embedded visualizations, and shareable links==.

The post hit 4.4 million views in 16 hours.

The response was immediate and tribal. ==Two camps formed overnight.==

Team HTML said Markdown is dead. They pointed to Thariq’s examples: code reviews with color-coded severity, stakeholder reports with collapsible sections, design systems with live swatches. “A Markdown file you scroll past is a file that doesn’t exist.”

Team Markdown fired back. Security risks from AI-generated JavaScript. Noisy diffs that break code review. Token overhead that bleeds your API budget. “HTML chases visual gloss at the expense of source readability, security, and reviewability.”

![](https://miro.medium.com/v2/resize:fit:1254/format:webp/1*zHkBc28GOOZkb2vM1fn6sQ.png)

The Great Format War: two camps, one missing question — diagram by author

Both sides are wrong. Not about everything. About what matters.

**Team HTML got the direction right but ignored the costs.** They hand-waved the 3–5x token overhead, skipped the security implications of AI-generated JavaScript, and never mentioned that Anthropic profits directly from the switch (more tokens = more revenue).

**Team Markdown got the risks right but is solving a problem that expired.** They’re optimizing for token budgets that made sense when GPT-4 had an 8,000-token context window. ==Context windows are 1 million tokens now. The constraint is gone. The habit isn’t.==

**The real question was never HTML vs Markdown.** It’s simpler than that: **who reads the output, and what do they do with it?**

To understand why this question matters more than the format war, you need to see how Markdown got here in the first place. It didn’t become the default by accident. It rode three waves.

## Three Waves, One Default

Markdown didn’t win a format war. It just kept showing up at the right time.

**The first wave was developers.** [John Gruber created Markdown in 2004](https://daringfireball.net/projects/markdown/) as a way to write readable plain text that could convert to HTML. It was a convenience tool for bloggers. Then GitHub adopted it for READMEs, issues, and documentation. Overnight, every open-source project on earth was writing Markdown. Not because it was the best format. Because it was the path of least resistance.

**The second wave was knowledge workers.** Through the 2010s, tools like Notion, Obsidian, and Jekyll built their entire editing experience around Markdown. It became the default for wikis, note-taking, and static sites. The appeal was the same: human-readable AND machine-parseable. You could write it in any text editor and render it anywhere.

**The third wave was AI.** When ChatGPT launched in November 2022, it rendered responses in Markdown. Not because OpenAI chose it after careful evaluation. Because the training data was saturated with it: GitHub repos, technical documentation, wikis, blog posts. Markdown was what the model had seen most, so Markdown was what the model produced. Every chatbot since has followed the same default.

Three waves. Each one reinforced the last. **Nobody chose Markdown for AI output. It inherited the job.**

![](https://miro.medium.com/v2/resize:fit:1208/format:webp/1*8lu8yKMO5cMdpTOxa_Z-2Q.png)

Three waves of Markdown adoption — and the fourth wave unwinding it — diagram by author

That inheritance is the problem. Because the world Markdown was built for and the world we’re building now are fundamentally different. Three assumptions baked into Markdown are breaking at the same time.

## Three Premises Breaking

Markdown became the default AI output under three assumptions. All three made sense in 2022. None of them hold in 2026.

**Premise 1: Humans hand-edit content.** Markdown was designed for people who write and revise their own text. That’s how blogs, docs, and READMEs still work. But agent output is different. You send a prompt. The agent generates a 2,000-word analysis, a code review, a project plan. You read it, maybe share it. ==You almost never open it in an editor and start rewriting paragraphs.== The format’s core value proposition — easy to edit by hand — no longer matches the use case.

**Premise 2: Content is small.** A 500-word blog post renders fine in Markdown. A 3,000-word agent-generated implementation plan with architecture decisions, trade-off tables, and code samples does not. Past about 100 lines, Markdown becomes a wall of text. ==No navigation, no collapsible sections, no way to jump to the part you care about==. Thariq’s observation is blunt: “Nobody really reads a Markdown file longer than 100 lines.”

**Premise 3: Output is read-only.** The old workflow was linear: prompt, generate, read, close. But the agent era is pushing toward something different. Users want to interact with the output: filter a table, adjust parameters, compare options side by side, export a subset, feed the result back into the next prompt. ==Markdown can’t carry interaction==. It’s a one-way street.

![](https://miro.medium.com/v2/resize:fit:1254/format:webp/1*8R8d0aMC_kbtv8JQDWbFyg.png)

Old workflow vs new: from “read and close” to “operate and loop back” — Diagram by author

**When** ==**all three premises break at once**==**, the format question changes.** It’s no longer “which format is more efficient?” It’s “which format matches what the reader actually does?”

==**Markdown is a report. You read it and close it.**==

==**HTML is an interface**==**. You operate on it and feed the result forward.**

That distinction matters more than any token cost calculation. But since the token cost is what most people are arguing about, let’s run the numbers.

## The Token Math Nobody Ran

The HTML-vs-Markdown debate runs on a single claim: HTML costs 3–5x more tokens. The number gets repeated constantly. Almost nobody checks what it actually means in dollars.

I ran the test. Same 2,000-word report generated in three formats: plain Markdown, lean semantic HTML, and full HTML with CSS styling and embedded SVG. The token counts:

- **Markdown:** ~3,000 output tokens
- **Lean HTML:** ~7,200 output tokens (2.4x)
- **Full HTML with CSS:** ~14,400 output tokens (4.8x)

The “3–10x” range you’ve seen quoted is real. For rich HTML with styling and interactivity, you’re burning roughly 5x the tokens. Now here’s what that costs per report at current API pricing:

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*gxbA2Ir83Kli-aoWrfEe3Q.png)

**At individual scale, the overhead is pocket change.** ==You need 171 reports on Claude Sonnet to spend one extra dollar. The cost of the HTML overhead on a single report is less than the electricity to charge the phone you’re reading this on.==

This is what I call **The Token Trap:** optimizing for a cost that’s rounding error in your actual engineering budget.

![](https://miro.medium.com/v2/resize:fit:1168/format:webp/1*HDTAyiR9wCJH0LmHNTC5sA.png)

The Token Trap: per-report cost that nobody should be arguing about — diagram by author

But the math has a second act. Scale it up and the numbers shift.

==**At 100 reports per day, the overhead is real.**== ==Claude Sonnet: $513/month extra. GPT-5.5: $1,026/month. That’s not rounding error anymore. That’s a line item.==

![](https://miro.medium.com/v2/resize:fit:1266/format:webp/1*YmKncPpAkql0Jf12fEoYfg.png)

The Scale Flip: pennies individually, hundreds monthly at enterprise volume — diagram by author

So Team Markdown has a point at enterprise scale. But they’re still measuring the wrong cost.

**The question isn’t what the tokens cost. It’s what human attention costs.** A senior engineer earns $75–150/hour. Fifteen minutes spent ==parsing a Markdown wall that should have been a navigable HTML== page costs $19–38 in engineer time. The token overhead for that same report? $0.17 on Sonnet.

**The Token Trap works in both directions.** Individuals waste time arguing about $0.17. Enterprises waste thousands in engineer attention to save hundreds in token costs. In both cases, the format decision should follow the reader, not the budget.

## The Decision Tree: Who Reads the Output?

If format follows reader, you need to know your reader. Every agent output has one of three audiences. The format choice follows directly.

![](https://miro.medium.com/v2/resize:fit:1288/format:webp/1*DYaneoRvW9r61qMNcYwt8w.png)

The Decision Tree: three readers, three formats — diagram by author

**Reader 1: A human.** Your ==stakeholder opens a browser,== scans for the section they care about, screenshots a chart for Slack, shares a link with their team. This is the use case Thariq built 20 examples around. Code reviews with inline annotations and severity colors. Implementation plans with collapsible architecture sections. Design system comparisons with live swatches you can click.

==HTML wins here== because the output is a destination. The reader navigates it, operates on it, shares it. Markdown flattens all of that into a scroll.

**Reader 2: Another agent.** Your output feeds into a downstream pipeline. An agent reads the analysis, extracts structured data, makes a decision, triggers the next step. No human ever sees it. This is where Markdown still wins cleanly. It’s lightweight, parseable, and diffable. Git tracks changes. CI pipelines process it. Other models consume it with minimal token overhead.

**Using HTML for agent-to-agent communication is like printing a spreadsheet, laminating it, and handing it to someone who’s going to retype the numbers.**

**Reader 3: Both.** The most common case and the one neither camp addresses. A developer generates a PR review. They read it themselves. They also want it tracked in the repo. A team lead generates a weekly status report. Stakeholders view it in the browser. The data feeds into next week’s planning prompt.

The answer for this case: **markdown source, HTML artifact.** Keep markdown as the editable, diffable, git-tracked source of truth. Generate an HTML companion for the humans who need to read, navigate, and share it. This is what Thariq himself recommends: “Keep Markdown as the editable source in repositories, generate HTML as a companion artifact for stakeholder review.”

![](https://miro.medium.com/v2/resize:fit:1294/format:webp/1*5ZFT7wBBte7UN9g4929-_Q.png)

Format Follows Reader: three paths with examples — diagram by author

**The decision tree is three questions.** ==Does a human read this? Use HTML.== Does only an agent read this? Use Markdown. Do both read it? Markdown source, HTML artifact. That’s the entire framework.

## Where This Breaks (and Who Benefits)

The decision tree is clean. The real world isn’t. Before you rewrite your CLAUDE.md to default to HTML, here are the risks that Team Markdown got right.

**Security is the real concern.** AI-generated HTML can include JavaScript. JavaScript means potential XSS vulnerabilities, local data leaks, and code execution you didn’t ask for. One critic put it sharply: “Running unvetted, AI-generated JS risks XSS or local data leaks.” This isn’t theoretical. If you’re generating HTML for internal tools, you need a review step or a strict no-JS constraint in your prompt. Thariq’s own guidelines demand it: no external CDN links, no unpkg imports, system fonts only, zero network calls at runtime.

**Accessibility is solvable but not automatic.** AI-generated HTML lacks [WCAG](https://www.w3.org/TR/WCAG22/) compliance by default. No alt text, inconsistent focus order, low-contrast text. You have to prompt for it explicitly: “WCAG 2.2 AA compliance, descriptive alt text, 4.5:1 color contrast, logical focus order.” Most developers don’t. This is a gap, ==not a dealbreaker==.

**Reviewability needs a pattern, not a format change.** ==HTML diffs are noisy==. A one-line content change can generate 50 lines of diff because the surrounding markup shifts. For teams that rely on pull request reviews, this is a real friction point. The mitigation is the template-plus-data pattern: keep the HTML template static, store variable content in a JSON payload, and only diff the JSON. Clean version control, rich visual output.

![](https://miro.medium.com/v2/resize:fit:1208/format:webp/1*eNFqJqacqZAndFK0e3LDjg.png)

Diagram by Author: HTML risk assessment

**Now the part most English-language coverage skips: who benefits from this shift?**

Anthropic does. HTML output consumes 3–5x more tokens than Markdown. More tokens means more API revenue. HTML also creates ecosystem lock-in: once your team builds workflows around Claude-generated interactive dashboards and reports, switching to another model means rebuilding those workflows. **This isn’t a conspiracy. It’s a business model.** And it doesn’t invalidate Thariq’s argument. But you should know the incentive structure before adopting the recommendation wholesale.

I haven’t seen security audits of AI-generated HTML at enterprise scale. I haven’t seen accessibility compliance studies. ==The case for HTML is strong== for the right use cases, but the tooling and guardrails are still catching up to the vision.

## What to Change Monday

Here’s the routing table. Screenshot it.

==SituationFormatWhyPR review for teammatesHTMLInline diffs, severity colors, collapsible file sectionsAgent chain inputMarkdownParseable, lightweight, no rendering overheadStakeholder reportHTMLNavigable, shareable by link, screenshots for SlackGit-tracked documentationMarkdownDiffable, reviewable, version-controlledDesign system comparisonHTMLLive swatches, interactive component variantsPersonal dev notesMarkdownQuick, editable, no presentation overheadClient-facing analysisHTMLProfessional layout, embedded charts, printableCI/CD pipeline outputMarkdownMachine-consumed, no human reads itWeekly team statusMarkdown source + HTML artifactTeam edits in repo, stakeholders view in browser==

![](https://miro.medium.com/v2/resize:fit:1268/format:webp/1*Em8JzOZ3rBWb1GbUvXFiKQ.png)

Diagram by Author: The routing table

**Markdown isn’t dead. It’s being promoted.** From the display layer to the protocol layer. It was always ==better as a machine-readable format than a human-readable one==. The agent era just made that clear.

HTML isn’t the future of everything. It’s the future of output that humans actually need to read, navigate, and act on.

==**The skill that matters now isn’t picking the right format.**== **It’s knowing your reader.** The rest follows.

## [OpenAI Quietly Told You to Throw Away Your Prompt Stack](https://ai.gopubby.com/openai-quietly-told-you-to-throw-away-your-prompt-stack-ef1178f2e5ec?source=post_page-----36bee00c0ca2---------------------------------------)

### And Anthropic said the same thing. The 3 eras of prompting — and what the smartest models actually want from you.

ai.gopubby.com

## [The 4 Lines Every CLAUDE.md Needs](https://levelup.gitconnected.com/the-4-lines-every-claude-md-needs-2717a46866f6?source=post_page-----36bee00c0ca2---------------------------------------)

### What Karpathy diagnosed, what 60,000 developers bookmarked, and why behavioral constraints beat feature checklists

levelup.gitconnected.com

## [Harness Engineering: What Every AI Engineer Needs to Know in 2026](https://ai.gopubby.com/harness-engineering-what-every-ai-engineer-needs-to-know-in-2026-0ab649e5686a?postPublishedType=repub&source=post_page-----36bee00c0ca2---------------------------------------)

### Three camps, three architectures - and what Opus 4.7 just proved about all of them

ai.gopubby.com

## Before you go! 🦸🏻♀️

If you liked my story and you want to support me:

1. Throw some Medium love 💕(claps, comments and highlights), your support means the world to me.👏
2. [Follow me](https://medium.com/@yanli.liu/about) on Medium and subscribe to get my latest article🫶

## [About - Yanli Liu - Medium](https://medium.com/@yanli.liu/about?source=post_page-----36bee00c0ca2---------------------------------------)

### Read writing from Yanli Liu on Medium. Daytime finance practitioner based in Luxembourg, seasoned coder, and passionate…

medium.com

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*D0MocMPyG7Ymyj9q.png)

This story is published on [Generative AI](https://generativeai.pub/). Connect with us on [LinkedIn](https://www.linkedin.com/company/generative-ai-publication) and follow [Zeniteq](https://www.zeniteq.com/) to stay in the loop with the latest AI stories.

Subscribe to our [newsletter](https://www.generativeaipub.com/) and [YouTube](https://www.youtube.com/@generativeaipub) channel to stay updated with the latest news and updates on generative AI. Let’s shape the future of AI together!

![](https://miro.medium.com/v2/resize:fit:1400/format:webp/0*MRbmaJb3DKrF-H0W.png)

---

**Source :** [Anthropic’s Engineer Said Kill Markdown. Here’s What He Actually Meant.](https://medium.com/generative-ai/anthropics-engineer-said-kill-markdown-here-s-what-he-actually-meant-36bee00c0ca2)  
**Auteur :** Yanli Liu  
**Clipé le :** 2026-05-18T09:22:35+02:00

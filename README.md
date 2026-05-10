# bairesdev-thought-leadership-wizard
BairesDev Thought Leadership Wizard to assist content ideation and distribution

BairesDev Thought Leadership Wizard
An AI-powered editorial system that scales judgment, not output.

What This Is
The Thought Leadership Wizard is a Claude-powered editorial assistant built for BairesDev's content team. It vets pitches, routes topics to the right format and author, runs pre-publish checks against a defined editorial system, and — most importantly — surfaces unexploited pitch opportunities from proprietary data by cross-referencing internal findings against the broader external discourse.
It is not a content generator. It does not write articles. It is an editorial reasoning layer that helps a small team produce high-quality thought leadership at scale by codifying the judgment calls that usually live in one editor's head.

Why It Exists
BairesDev publishes thought leadership across multiple channels: the CEO's LinkedIn, Forbes Tech Council, the World Economic Forum, Tier 1 business media, engineering and HR trade publications, the company's owned AI Hub blog, the Fellows program (external CTOs and senior engineers), and webinar recap content. Each channel has its own format conventions, audience register, evidence requirements, and approval chain. Each author on the roster has a different voice, a different credibility lane, and different topical authority.
Holding all of that in one editor's head is possible — but it doesn't scale. The natural failure mode of a busy editorial function is to default to the strongest fit for the most familiar author and let the rest of the surface area go underused. Topics that should have run as engineering trade pub op-eds end up as LinkedIn posts. Findings that could have spawned three different articles for three different authors get folded into one. Strong proprietary data sits in the Source Asset Index without anyone connecting it to the live external conversation that would make it timely.
The wizard is designed to fix that gap. It gives the editorial team a way to expand the option set on every pitch, every topic, every finding — without sacrificing the judgment that makes the work credible in the first place.

What It Does
Five Functions
1. Vet a pitch. When someone proposes a working title and angle, the wizard assesses it against the editorial system. Strong, needs work, or reject — with reasoning, recommendations, and flags for any hard editorial rule violations. The wizard pushes back on weak pitches rather than rolling over and producing content.
2. Route a topic. When a topic enters the pipeline, the wizard recommends the right format, the right author pool, the right channel, and the right approval chain. It traverses the Intersection Matrix, applies the Content Type Rulebooks, and respects the constraints of each author's lane.
3. Match an author. Given an article topic and a target format, the wizard returns ranked author recommendations with fit reasoning — and flags when no strong match exists in the roster.
4. Run a pre-publish check. Given a draft, the wizard checks against publication criteria for that specific format and the hard editorial rules that apply across all content. It returns specific flags with recommended fixes, not generic feedback.
5. Surface topic opportunities. This is the wizard's most distinctive function. Given a Dev Barometer wave or any pasted source material (interview transcripts, agency reports, internal surveys, client patterns), the wizard extracts the strongest themes, infers what current external reporting from credible outlets would validate as a live conversation among senior tech decision-makers, cross-references against the published corpus to identify unexploited angles, and surfaces ranked pitch opportunities — each with internal trigger, external validation, what BairesDev uniquely adds, recommended format/author/channel, and an urgency rating.
The surfacing function is where the wizard most directly augments editorial work. Most surface-level findings can be turned into one obvious article. The wizard's job is to find the second, third, and fourth angle that the obvious read would miss.

How It's Built
The wizard runs as a Claude Project. There is no custom code, no hosted backend, no deployment — the entire system is documents and instructions. This is by design. The reasoning value is in the editorial logic, not in the plumbing. Building a custom interface would have added complexity without changing the quality of the output.
The system has six structured documents that together encode the editorial system:
Documents
Content Type Rulebooks (4 files). One rulebook per format: PR Op-Eds, AI Hub Articles, Fellows Articles, and Webinar Blog Posts. Each rulebook defines word count, voice, audience, evidence requirements, approval chain, and the specific criteria for what makes an angle strong, weak, or rejectable.
2026 Strategic Topic Priorities. The editorial calendar's directional themes for the year — what BairesDev is actively positioning around, what it's deprioritizing, and how priorities map to formats and authors. This is the steering document for the wizard's longer-term lens.
Author Roster. All 28 internal authors with role, expertise areas, eligible formats, eligible channels, biography, and tone notes. The wizard uses this to match authors to topics and to ensure each author stays in their authority lane.
Intersection Matrix. A three-tab routing system: Topic Routing (which formats and authors fit which topic territories), Format Reference Card (full constraints for each format in one place), and Routing Decision Guide (the decision tree the wizard walks through to make a routing call, including hard stops for content the system rejects entirely).
Source Asset Index. A five-tab catalog of every proprietary source and every published piece. Dev Barometer waves are listed with sample size, key findings, and topic territories unlocked. PR op-eds, AI Hub articles, Fellows articles, and webinar pieces are indexed by title, author, channel, date, and topic. The wizard uses this to avoid surfacing angles that have already been covered.
How I Surface. The editorial instinct layer. This document encodes the methodology behind the surfacing function: how to find non-obvious connections between findings, how to apply lenses (tech talent, business, software engineering, technology shifts, engineering leadership, predictions), what to discard, the "stay in lane" filter that keeps the wizard from venturing into territories where BairesDev lacks authority (AI ethics frameworks, sustainability, regulation, philosophy), the standards for credible external validation, and the rule that even from strong sources, certain statistics have become discourse clichés through overuse and should be avoided.
Voice Profiles
Two authors have dedicated voice profiles — Nacho de Marco (CEO) and Justice Erolin (CTO). These capture register, sentence rhythm, characteristic moves, and what each author would and wouldn't say. The wizard uses these to assess fit when matching authors and when running pre-publish checks on drafts attributed to either of them.
System Instructions
The Claude Project's custom instructions tell the wizard who it is, what its five functions are, how to use the documents, and — critically — how to communicate. The wizard responds directly. It skips preambles. When it flags something, it names the specific rule and recommends a specific fix. When it recommends, it commits to a recommendation rather than hedging through a list of qualifications. It matches the editorial standards it enforces: no contrastive substitution, no em dashes unless structural, no templated AI phrases.

Why a Project, Not a Custom App
Earlier in development, the wizard was prototyped as a custom HTML interface with branded styling and structured input fields. It worked well as a visual concept but ran into a real constraint: the artifact runtime in Claude.ai doesn't expose an API hook that an embedded app can call from the browser. A custom app would have required hosting, an API key, and ongoing maintenance — overhead that wasn't justified for a tool used by a small editorial team.
The Claude Project format gives up the visual polish of a branded app but preserves the entire reasoning system. For a tool whose value is editorial judgment rather than presentation, that's the right tradeoff.
A future iteration could wrap the project in a real branded app for broader team rollout. For now, the project is the wizard.

How to Use It

Open the Claude Project.
Start a new chat.
Tell the wizard what you need. The wizard reads intent — you don't need to invoke a specific function by name. Examples:

"Vet this pitch for me: [title and angle]"
"I want to write something on AI governance gaps. Where should it go?"
"Surface topic opportunities from the Q1 2026 Dev Barometer. Raw brainstorm mode."
"Match an author to this topic: [topic]"
"Run a pre-publish check on this draft."


The wizard returns a structured response. Iterate from there.

The documents in the project are loaded into every conversation automatically. As new Dev Barometer waves publish, new articles are added to the corpus, or new authors join the roster, the underlying documents are updated and the wizard's reasoning updates with them.

What's Inside This Repository

The six structured documents that power the wizard
Voice profiles for Nacho de Marco and Justice Erolin
The Claude Project's custom instructions

What This Project Is Really About
Most "AI for content" tools assume the bottleneck is generating words. For a serious editorial function, words are not the bottleneck. The bottleneck is consistent judgment — knowing which angle is fresh, which lens fits which finding, which author has authority for which topic, which external source actually validates a claim, and which proprietary data point is the start of an article versus the start of a cliché.
The Thought Leadership Wizard is an attempt to encode that judgment in a way that scales. The team's editorial standards — the rulebooks, the author lanes, the lens methodology, the lane filter, the validation criteria — become operational instructions the wizard applies on every prompt. The editor stays the editor. The wizard expands what one editor can hold in working memory at any given moment.
That's the whole project. Not a content factory. A judgment amplifier.

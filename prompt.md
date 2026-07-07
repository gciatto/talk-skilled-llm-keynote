help me sketch the presentation for the keynote.
assume the audience is expert in symbolic AI, and has some amatorial experience with LLMs and prompt engineering.

below, i report the expected table of contents of the presentation.
you should generate slides' content in markdown.
this is just a draft, later on we'll generate the actual slides.

use the canvas to generate the slides' content.
use "---" to separate slides, and use the following rules for slide content:
- when generating the slides, remember to keep them short
- short sentences, unless quoting
- use lists extensively (bullet point is order is not relevant), up the 3rd indentation level
- no more than 5 first-level items per slide
- items (no matter what the indentation level is) should be always two lines or less, one is better
- if a slide would be too long, split it into multiple slides, repeat the title and add "pt. INDEX" in the title
- no need to style the slides, just provide the content
- however, you can suggest to insert images in the slides
  * in the latter case, use a placeholder image with text describing which source to take the image from, or what to show in the image
- do not use separated graphical items for bullet points or list numbers, just use text boxes and text formatting
- highlight keywords in bold or with colors (green/blue/red for emphasis of positive/negative/neutral connotation)
- put suggestions about the speech in the notes of the presentation

i'll give you the ToC one section at a time, so you can expand the canvas incrementally.
tell me when ready.

--- Table of Contents ---

Below, the citations are intended as **slide-level anchors**, not necessarily all to be displayed on the slide.

## **0. Opening and positioning**

* **Slide 1 — From Language to Agency**

  * The keynote starts from the shift from LLMs as conversational generators to LLM-based systems that interpret, remember, use tools, and affect external states

    * Citations: SKILLED-LLMs context pack; ReAct; Toolformer  ([arXiv][1])
  * The subtitle frames the polemic:
    + plans, norms, tools, memory, and traces matter more than bigger prompts and larger models
    + researchers should focus on **representations** that mediate between language, reasoning, and action...
    + ... avoiding to treat LLMs as black-box agents that act without inspectable commitments

    * Citations: SKILLED-LLMs context pack

* **Slide 2 — Why this workshop?**

  * SKILLED-LLMs is the right venue because it explicitly sits at the intersection of language models, knowledge representation, reasoning, ethics, statistics, and neuro-symbolic integration

    * Citations: SKILLED-LLMs CFP
  * The talk treats “reasoning in LLMs” and “KR-style reasoning with LLMs” as questions about what representations mediate between language, inference, and action

    * Citations: SKILLED-LLMs CFP; neuro-symbolic LLM reasoning survey  ([arXiv][2])
* **Slide 3 — Talk contract: notions, not a framework**

  * The keynote offers definitions, distinctions, analogies, and a representation-centric perspective rather than a finished architecture or empirical contribution

    * Citations: SKILLED-LLMs context pack

  * The central claim is that LLMs enter messy human worlds, while explicit representations make action inspectable, governable, verifiable, contestable, and auditable

    * Citations: SKILLED-LLMs context pack

  * Experience comes from an Horizon project that colleagues and I recently submitted
    * what I can disclose is that the call was asking for "next-generation AI agents"...
    * ... and our proposal revolves around the idea that **representations** are the missing middle between fluent generation and governed action
    * so the goal is sharing ideas and research insights, and getting feedback—not really presenting finished works

## **1. Vocabulary: putting everyone on the same page**

* **Slide 4 — GenAI, foundation models, and LLMs**

  * Generative AI can be introduced as AI systems capable of producing content such as text, images, audio, video, and code

    * Citations: GenAI slides
  * Foundation models are reusable capability substrates trained on large data and compute, then specialised through prompting, adaptation, retrieval, orchestration, and tools

    * Citations: GenAI slides; Toolformer  ([arXiv][3])
  * An LLM should be described operationally as a probabilistic sequence model that becomes agentic only when embedded in a wider control loop

    * Citations: ReAct; Toolformer; Generative Agents ([arXiv][1])

* Slide 4 bis – LLMs as next word prediction
  * take slides from the GenAI slides explaining the next word prediction view of LLMs

* **Slide 5 — What is an agent?**

  * In the classical AI view, an agent receives percepts from an environment and performs actions in that environment

    * Citations: Russell & Norvig ([api.pageplace.de][4])
  * In the agent-oriented tradition, “agent” has never had a single universally accepted definition, so its use in current LLM discourse must be disciplined
    * agent as the robot controller, agent as a process in process calculi, agent as the logic reasoner, BDI agents, agent as the planner, agent as the software component, agent as the human proxy, etc.

    * Citations: Wooldridge & Jennings ([CMU School of Computer Science][5])

* Add further slides explaining the notions of **goal**, **environment**, **perception**, **actuation**, **deliberation**, **control loop**
  * sort them in such a way that the discussion is incremental
  * take them from the Gentle Introduction to Intelligent Agents slides

* **Slide 6 — Intelligence vs. Autonomy vs. Agency**

  * Define the tree notions (see sources)
    * include discussion about "increasing degrees of intelligence/autonomy/agency"
      * executive vs. motivational autonomy
  * Describe corner cases to clarify the distinctions (see sources)

* Slide 7 – LLMs vs Agents
  * are LLMs agents? not really, not fully: they can delivberate, and they have some intelligent capabilities, but they are not autonomous
  * what is an agent in agentic AI?
    * the external software governing the LLMs (providing prompts, managing LLM responses, mediating among tools, memory, etc.)
    * one may think that LLMs act as the deliberation module ("the mind") of agents
    * one may also consider also the agent as the combo: controlling software + LLM
  * remarks to strenghen the idea:
    * LLMs alone cannot perceive the environment, they need an external system to do that and pass the information to them
    * LLMs alone cannot act on the environment, they need an external system to do
      * yet LLMs may decide what action to do, and pass the decision to the external system to execute it

  * In the LLM era, an agent is best presented as a system that uses a model to interpret context, choose actions, call tools, update memory, and pursue assigned goals
    * Citations: ReAct; AgentBench; WebArena ([arXiv][1])

* **Slide 8 — Artifacts, tools, function calls**

  * A tool is an external capability exposed to the agent via a clear interface, such as an API, database, calculator, planner, verifier, code executor, simulator, or enterprise system
    * ... that the agent may call to perceive the environment, to act on it, or to reason about it
    * Citations: Toolformer; WebArena; LLM-as-a-Service slides ([arXiv][3])

  * The notion has been modelled far before the advent of LLMs, via the A&A (Agent & Artifact) paradigm, and it is now being revisited in the context of LLMs
    * cite A&A from Omicini, and Ricci+Ciortea for the analogy

  * Back in time, in classical MAS, most of the modelling and engineering effort was on the agent programmer
    * who needed design and implement adaptation code among the agent's controller software and the external artifacts + the code of the controller software itself to be able to exploit the artifacts accordingly

  * Nowadays, there's a lot of engineering conventions on how to describe tools API's in such a way that LLMs can "understand" them and decide when to call a tool, what to pass to it, and how to interpret the result
    * Citations: Toolformer; WebArena; LLM-as-a-Service slides ([arXiv][3])

  * Value added of LLMs: the possibility to craft tools via natural language, or to learn how to use tools via their natural language specification

* **Slide 9 — Memory is controlled state across time**

  * Memory should be introduced as persistent, managed state the agent may exploit to
    1. support reasoning, planning, and deliberation
    2. store and retrieve information about the environment, the agent’s own actions, and the effects of those actions
    3. keep track of the agent’s own internal state, including goals, perceptions, exchanged messages, ongoing activities, etc

    * Citations: Memory survey; Generative Agents; Reflexion ([arXiv][7])
  * Agent memory should distinguish context, episodic memory, semantic memory, procedural memory, and institutional memory
    * explain them all
    * Citations: Memory survey; Generative Agents; Voyager ([arXiv][7])
  * Governed memory requires metadata about provenance, staleness, salience, contradiction, access rights, privacy, and deletion
    * explain them all
    * Citations: Memory survey; SKILLED-LLMs context pack ([arXiv][7])

  * Mechanisms for retrieval, selection, update, and forgetting should be explicit, inspectable, and auditable
    * these may further depend on the data schema, which in turn may be absent/loose when the data is unstructured
    * exemplify criticalities

* **Slide 10 — Planning**
  * explain classical planning in a nutshell
  * focus on the need to provide action set, with preconditions and effects clearly described, plus a clearly described goal state
  * the planner as an exact problem solver
    - relying on a formal representation of the world, the actions, and the goal
    - producing a formal representation of the plan, which can be inspected, verified, and executed
  * notice that most commonly LLMs "plan" in a different way:
    - admissible actions are unknown, or not fully known to the LLM, and the LLM is not provided with a formal representation of the world, the actions, and the goal
    - the plan is not a formal representation, but a fluent text that may or may not be executable, and that may or may not be correct
    - execution implies interpretation of the fluent text, which may again introduce errors

## **2. The common technical pattern behind agentic AI**

* **Slide 11 — Natural language as an interface**

  * explain the common pattern of using natural language as an interface to the AI
  * prompt engineering is the art of crafting the right prompt to get the desired behaviour from the AI
      + criteria for good prompts (clarity, completeness, context, constraints, examples)
      + briefly explain and exemplify prompt engineering patterns (e.g., few-shot, chain-of-thought, Tree-of-Thought—one per slide)
  * specify that in my view this is yet another case of what Luciano Floridi calls "envelopping": humans are getting used to be more clear and more precise about their intents in order to let the AI understand them
    + add a slide on envelopping too

* Slide 11 bis — Prompt engineering patterns

  * Few-shot prompting: provide a few examples of the desired input-output behaviour
  * Chain-of-thought prompting: ask the model to generate intermediate reasoning steps before producing the final answer
  * Tree-of-Thought prompting: explore multiple reasoning paths in parallel, allowing the model to backtrack and choose the best path

    * Citations: ReAct; Tree of Thoughts; LLM-Modulo ([arXiv][1])

* Slide 11 ter — Envelopping

  * describe envelopping as per Floridi's "La quarta rivoluzione" (The Fourth Revolution)

* Slide 11 quater — Natural language as the means for reasoning

  * explain that natural language is not only the interface to the AI, but also the means for reasoning
  * LLMs are trained to predict the next token in a sequence, and they learn to generate coherent and contextually relevant text
  * this ability allows them to perform reasoning tasks by generating intermediate steps, explanations, or justifications in natural language

  * put here observations and slides about the generality of natural language from my GenAI slides

* **Slide 12 — The agentic loop**

  * report here the discussion from Omicini's slides M11 - in particular slides 12–20, there including references to ReAct and Toolformer
  * invent examples wherever applicable

* **Slide 13 — Hidden commitments are the real failure mode**

  * Current agents often externalise action without externalising the commitments that justify action

    * Citations: SKILLED-LLMs context pack; WebArena; AgentBench  ([arXiv][8])
  * The relevant hidden commitments include goals, assumptions, tool effects, norms, authorisations, memory provenance, responsibility boundaries, and evidence

    * Citations: SKILLED-LLMs context pack; governance of autonomous Web agents  ([arXiv][10])
  * The talk should shift attention from “Can the model answer?” to “Under which explicit commitments may the system act?”

    * Citations: Floridi; SKILLED-LLMs context pack ([Springer Nature][6])

## **3. Reasoning: symbolic AI, LLMs, and the dual-process analogy**

* **Slide 14 — What is reasoning?**

  * Reasoning can be defined pragmatically as the controlled transformation of representations to derive, justify, select, or revise conclusions and actions under constraints

    * Citations: Russell & Norvig; Sloman; Evans & Stanovich ([api.pageplace.de][4])
  * This definition avoids asking whether LLMs “really reason” and instead asks what representations are transformed, by which operations, under which checks

    * Citations: LLM-Modulo; neuro-symbolic LLM reasoning survey ([arXiv][11])
* **Slide 15 — Symbolic reasoning**

  * Symbolic reasoning operates over explicit structures such as logical formulae, states, actions, preconditions, effects, constraints, norms, proofs, and argumentation structures

    * Citations: Russell & Norvig; governance of autonomous Web agents ([api.pageplace.de][4])
  * Its strengths are inspectability, compositionality, traceability, verification, and relatively well-characterised failure modes

    * Citations: LLM-Modulo; NIST AI RMF ([arXiv][11])
  * Its weakness is that it depends on having an adequate representation of the relevant world, task, process, and norm system

    * Citations: LLM-Modulo; SKILLED-LLMs context pack ([arXiv][11])
* **Slide 16 — LLM reasoning**

  * LLM reasoning can be treated as the model’s ability to generate, select, or simulate plausible reasoning-like continuations from learned structure and local context

    * Citations: ReAct; Tree of Thoughts; LLM-Modulo ([arXiv][1])
  * LLMs are often strong at interpretation, hypothesis generation, linguistic abstraction, and approximate semantic matching

    * Citations: ReAct; Toolformer; neuro-symbolic LLM reasoning survey ([arXiv][1])
  * LLMs remain fragile when reasoning must be bound to executable plans, valid constraints, verified state transitions, or durable commitments

    * Citations: PlanBench; LLM-Modulo; WebArena ([arXiv][12])
* **Slide 17 — Dual-system analogy, with caveat**

  * Kahneman’s System 1 and System 2 provide a useful metaphor for fast associative proposal and slower effortful checking, not a literal model of LLM cognition

    * Citations: Kahneman; Evans & Stanovich; SKILLED-LLMs context pack  ([University of Plymouth][13])
  * The architectural analogy is that LLMs are useful for fast context-sensitive interpretation, while symbolic and formal components are useful for explicit deliberation and governance

    * Citations: Sloman; neuro-symbolic LLM reasoning survey; LLM-Modulo ([matt.colorado.edu][14])
  * The key scientific question is the interface between the two, not the victory of one paradigm over the other

    * Citations: Sloman; SKILLED-LLMs context pack ([matt.colorado.edu][14])
* **Slide 18 — Intermediate traces are useful, but not enough**

  * Chain-of-thought, ReAct traces, Tree-of-Thought states, and Reflexion memories are early examples of externalised cognition

    * Citations: ReAct; Tree of Thoughts; Reflexion ([arXiv][1])
  * These traces improve visibility but are often weakly typed, weakly constrained, weakly auditable, and difficult to verify

    * Citations: LLM-Modulo; prompt-injection benchmarking; governance of autonomous Web agents ([arXiv][11])
  * The keynote should use them as a bridge toward stronger intermediate representations such as plans, norm models, tool contracts, and verification targets

    * Citations: SKILLED-LLMs context pack; LLM-Modulo  ([arXiv][11])

## **4. Benchmarks and stress tests**

* **Slide 19 — Why ARC-AGI matters here**

  * ARC-style benchmarks are useful because they focus attention on abstraction, novelty, and skill-acquisition efficiency rather than accumulated task familiarity

    * Citations: ARC-AGI-2; ARC-AGI-3; Chollet 2019 as cited in ARC-AGI papers
  * The point is not to treat ARC-AGI as a definitive intelligence test, but to use it as a stress test for representation formation under novelty

    * Citations: SKILLED-LLMs context pack; ARC-AGI-2
* **Slide 20 — ARC-AGI-2: static abstraction under pressure**

  * ARC-AGI-2 preserves the grid-based input-output format but raises the difficulty through more complex, novel, and compositional tasks

    * Citations: ARC-AGI-2
  * Its relevance to the keynote is that abstraction-heavy tasks expose the need to infer compact representations rather than merely complete familiar patterns

    * Citations: ARC-AGI-2; ARC-AGI-3
  * The slide should avoid triumphalist or defeatist readings and instead ask what kind of representation the system must construct to solve the task

    * Citations: ARC-AGI-2; SKILLED-LLMs context pack
* **Slide 21 — ARC-AGI-3: from answers to action**

  * ARC-AGI-3 shifts from static input-output reasoning to interactive environments requiring exploration, model formation, goal inference, planning, and execution

    * Citations: ARC-AGI-3
  * This makes it directly relevant to agentic AI because the agent must discover what matters before it can act effectively

    * Citations: ARC-AGI-3
  * The reported gap between humans and frontier systems should be used to motivate better representational scaffolding, not to make broad claims about AGI

    * Citations: ARC-AGI-3; SKILLED-LLMs context pack
* **Slide 22 — Agent benchmarks point to the same bottleneck**

  * GAIA stresses reasoning, multimodality, web browsing, and tool use in questions that are relatively simple for humans but difficult for AI assistants

    * Citations: GAIA ([arXiv][15])
  * WebArena stresses realistic web tasks, long-horizon interactions, tool use, functional correctness, and the gap between demonstration and robust execution

    * Citations: WebArena ([arXiv][8])
  * AgentBench identifies long-term reasoning, decision-making, and instruction-following as major obstacles for usable LLM agents

    * Citations: AgentBench ([arXiv][16])
  * SWE-bench shows that realistic software-engineering tasks require codebase understanding, long-context coordination, environment interaction, and multi-file reasoning

    * Citations: SWE-bench ([arXiv][17])

## **5. Planning, acting, and the limits of prompt-centric agency**

* **Slide 23 — Planning is not fluent plan-shaped text**

  * A plan should be treated as an explicit object with states, subgoals, preconditions, effects, ordering constraints, contingencies, and repair points

    * Citations: Russell & Norvig; PlanBench; LLM-Modulo ([api.pageplace.de][4])
  * PlanBench-style results are useful because they warn against treating LLMs as complete autonomous planners

    * Citations: PlanBench ([arXiv][12])
  * LLMs may be more credible as translators, critics, heuristic sources, or interfaces to planners than as the sole planning substrate

    * Citations: PlanBench; LLM-Modulo ([arXiv][12])
* **Slide 24 — Tool use requires governance**

  * Tool use increases capability by allowing the agent to delegate to specialised external systems

    * Citations: Toolformer; ReAct ([arXiv][3])
  * Tool use also increases exposure because actions can affect databases, files, users, services, robots, workflows, and institutional states

    * Citations: WebArena; governance of autonomous Web agents; prompt-injection benchmarking ([arXiv][8])
  * The relevant question is not only which tool to call, but whether the call is authorised, safe, reversible, logged, and norm-compliant

    * Citations: governance of autonomous Web agents; NIST AI RMF; EU AI Act summary ([arXiv][10])

## **6. The missing middle: intermediate representations**

* **Slide 25 — Definition**

  * An intermediate representation is an explicit, inspectable artefact that mediates between natural-language intention and external action

    * Citations: SKILLED-LLMs context pack
  * Intermediate representations include goals, plans, process models, norms, tool contracts, memory states, verification targets, runtime monitors, traces, and audit-ready explanations

    * Citations: SKILLED-LLMs context pack
  * They are not implementation details, but the substrate through which agency becomes governable

    * Citations: SKILLED-LLMs context pack; governance of autonomous Web agents  ([arXiv][10])
* **Slide 26 — Plans and process models**

  * Plans make future commitments explicit, so they can be inspected, simulated, checked, repaired, and explained

    * Citations: PlanBench; LLM-Modulo; SKILLED-LLMs context pack ([arXiv][12])
  * Process models make organisational action explicit by representing roles, ordering constraints, exceptions, approvals, escalation paths, and completion conditions

    * Citations: SKILLED-LLMs context pack
  * The slide should contrast process models with prompt recipes: a process model is a checkable structure, not merely an instruction string

    * Citations: SKILLED-LLMs context pack; LLM-Modulo  ([arXiv][11])
* **Slide 27 — Norms and tool contracts**

  * Norms represent what must, may, and must not happen under specific roles, contexts, and institutional conditions

    * Citations: governance of autonomous Web agents; EU AI Act summary; OECD AI Principles ([arXiv][10])
  * Tool contracts represent what a tool can do, what it assumes, what it changes, what it costs, and who may authorise it

    * Citations: Toolformer; WebArena; prompt-injection benchmarking ([arXiv][3])
  * Norms and tool contracts together determine whether an available action is also an admissible action

    * Citations: governance of autonomous Web agents; NIST AI RMF ([arXiv][10])
* **Slide 28 — Memory, verification targets, and traces**

  * Structured memory preserves relevant past state with provenance, salience, staleness, contradiction handling, access control, and forgetting

    * Citations: Memory survey; Reflexion; Generative Agents ([arXiv][7])
  * Verification targets specify properties that should hold before, during, or after execution

    * Citations: LLM-Modulo; NIST AI RMF; SKILLED-LLMs context pack ([arXiv][11])
  * Traces connect actions to goals, plans, norms, tools, evidence, memory, and human approvals

    * Citations: SKILLED-LLMs context pack; NIST AI RMF; Floridi on accountability  ([NIST][18])

## **7. Why representations matter**

* **Slide 29 — Trustworthiness**

  * Inspectability requires explicit artefacts that humans and machines can examine

    * Citations: SKILLED-LLMs context pack; NIST AI RMF  ([NIST][18])
  * Contestability requires the ability to ask why an action was taken, why an alternative was rejected, and what assumptions would change the outcome

    * Citations: SKILLED-LLMs context pack; EU AI Act summary; OECD AI Principles  ([EUR-Lex][19])
  * Auditability requires traces linked to commitments, not post-hoc natural-language rationalisations

    * Citations: SKILLED-LLMs context pack; Floridi; NIST AI RMF   ([NIST][18])
* **Slide 30 — Effectiveness**

  * Intermediate representations can improve long-horizon coherence by making goals, state, memory, and plans persistent across steps

    * Citations: Generative Agents; Reflexion; Memory survey ([arXiv][20])
  * They can improve repairability because failures can be located in a plan, memory item, tool contract, norm, or verification condition rather than only in a transcript

    * Citations: LLM-Modulo; PlanBench; SKILLED-LLMs context pack ([arXiv][11])
  * They support resource-aware agency by using LLMs when needed and specialised symbolic or software components when those are cheaper, safer, or more reliable

    * Citations: Toolformer; LLM-Modulo; SKILLED-LLMs context pack ([arXiv][3])
* **Slide 31 — Scientific study of agentic AI**

  * Representations make agent behaviour experimentally tractable because they can be inspected, perturbed, ablated, compared, and verified

    * Citations: AgentBench; WebArena; ARC-AGI-3 ([arXiv][16])
  * Evaluation should measure not only task success, but also plan quality, trace completeness, norm compliance, repairability, resource use, and human-intervention load

    * Citations: SKILLED-LLMs context pack; GAIA; WebArena; AgentBench  ([arXiv][15])
  * A representation-centric view makes agents studyable as systems, not merely as prompts, model calls, and transcripts

    * Citations: LLM-Modulo; neuro-symbolic LLM reasoning survey; SKILLED-LLMs context pack ([arXiv][11])

## **8. Application pattern and research agenda**

* **Slide 32 — Where this matters most**

  * The strongest application pattern is knowledge-intensive organisational automation under constraints

    * Citations: SKILLED-LLMs context pack
  * Typical domains include public administration, healthcare, law, compliance engineering, industrial documentation, ERP/process alignment, robotics governance, and scientific workflow support

    * Citations: SKILLED-LLMs context pack
  * These domains are hard because inputs are linguistic, processes are underspecified, norms are distributed, exceptions are frequent, and responsibility remains human

    * Citations: SKILLED-LLMs context pack; EU AI Act summary; NIST AI RMF  ([EUR-Lex][19])
* **Slide 33 — Research agenda: representation induction**

  * A central research problem is how to infer process models, norms, ontologies, tool contracts, and verification targets from documents, logs, conversations, forms, diagrams, and expert input

    * Citations: SKILLED-LLMs context pack; neuro-symbolic LLM reasoning survey  ([arXiv][2])
  * LLMs can propose candidate structures, but the system must surface incompleteness, uncertainty, contradiction, and normative ambiguity

    * Citations: LLM-Modulo; Memory survey; prompt-injection benchmarking ([arXiv][11])
* **Slide 34 — Research agenda: validation and repair**

  * Extracted representations need validation through human review, conformance checking, formal consistency checks, simulation, counterexample generation, and runtime monitoring

    * Citations: LLM-Modulo; NIST AI RMF; SKILLED-LLMs context pack ([arXiv][11])
  * Repair should be treated as a normal part of agentic execution because agents will operate under partial knowledge, changing constraints, and uncertain environments

    * Citations: ReAct; Reflexion; ARC-AGI-3 ([arXiv][1])
* **Slide 35 — Research agenda: interfaces between neural and symbolic components**

  * A core open question is what the right interface language is between LLMs, planners, solvers, verifiers, knowledge graphs, monitors, and humans

    * Citations: LLM-Modulo; neuro-symbolic LLM reasoning survey; Sloman ([arXiv][11])
  * This interface should preserve enough semantics to support verification, but remain flexible enough to absorb messy human inputs

    * Citations: SKILLED-LLMs context pack; ReAct; Toolformer  ([arXiv][1])
* **Slide 36 — Research agenda: memory and tool governance**

  * Memory governance must address provenance, staleness, contradiction, forgetting, privacy, access rights, and long-horizon consistency

    * Citations: Memory survey; NIST AI RMF ([arXiv][7])
  * Tool governance must address discovery, authorisation, least privilege, sandboxing, monitoring, revocation, and audit

    * Citations: Toolformer; governance of autonomous Web agents; prompt-injection benchmarking ([arXiv][3])
* **Slide 37 — Research agenda: benchmarks for governed agency**

  * Future benchmarks should evaluate plans, traces, norm compliance, repairability, human intervention, and resource use in addition to final task success

    * Citations: AgentBench; WebArena; GAIA; SKILLED-LLMs context pack ([arXiv][16])
  * ARC-AGI-3 is useful because it pushes evaluation toward interactive adaptation, exploration, goal inference, model formation, and efficient action

    * Citations: ARC-AGI-3
* **Slide 38 — Closing: representation before autonomy**

  * LLMs are good at entering messy human worlds, but governed action requires explicit intermediate representations

    * Citations: SKILLED-LLMs context pack
  * The future of trustworthy LLM agents is not black-box autonomy, but representational mediation from fluent generation to governed action

    * Citations: SKILLED-LLMs context pack; governance of autonomous Web agents  ([arXiv][10])
  * Final slogan: representation before autonomy, plans before actions, norms before delegation, traces before trust, verification before deployment

    * Citations: SKILLED-LLMs context pack; NIST AI RMF; EU AI Act summary  ([NIST][18]).

[1]: https://arxiv.org/abs/2210.03629?utm_source=chatgpt.com "ReAct: Synergizing Reasoning and Acting in Language Models"
[2]: https://arxiv.org/abs/2508.13678?utm_source=chatgpt.com "Neuro-Symbolic Artificial Intelligence: Towards Improving the Reasoning Abilities of Large Language Models"
[3]: https://arxiv.org/abs/2302.04761?utm_source=chatgpt.com "Toolformer: Language Models Can Teach Themselves to Use Tools"
[4]: https://api.pageplace.de/preview/DT0400.9781292401171_A41586057/preview-9781292401171_A41586057.pdf?utm_source=chatgpt.com "Artificial Intelligence: A Modern Approach, Global Edition, 4ed"
[5]: https://www.cs.cmu.edu/~motionplanning/papers/sbp_papers/integrated1/woodridge_intelligent_agents.pdf?utm_source=chatgpt.com "Intelligent Agents: Theory and Practice"
[6]: https://link.springer.com/article/10.1007/s13347-025-00858-9?utm_source=chatgpt.com "AI as Agency without Intelligence: On Artificial Intelligence as a New ..."
[7]: https://arxiv.org/abs/2603.07670?utm_source=chatgpt.com "Memory for Autonomous LLM Agents:Mechanisms, Evaluation, and Emerging Frontiers"
[8]: https://arxiv.org/abs/2307.13854?utm_source=chatgpt.com "WebArena: A Realistic Web Environment for Building Autonomous Agents"
[9]: https://arxiv.org/abs/2310.12815?utm_source=chatgpt.com "Formalizing and Benchmarking Prompt Injection Attacks and Defenses"
[10]: https://arxiv.org/abs/2202.02574?utm_source=chatgpt.com "Governance of Autonomous Agents on the Web: Challenges and Opportunities"
[11]: https://arxiv.org/abs/2402.01817?utm_source=chatgpt.com "LLMs Can't Plan, But Can Help Planning in LLM-Modulo Frameworks"
[12]: https://arxiv.org/abs/2302.06706?utm_source=chatgpt.com "On the Planning Abilities of Large Language Models (A Critical Investigation with a Proposed Benchmark)"
[13]: https://researchportal.plymouth.ac.uk/en/publications/dual-process-theories-of-higher-cognition-advancing-the-debate/?utm_source=chatgpt.com "Dual-Process Theories of Higher Cognition: Advancing the Debate"
[14]: https://matt.colorado.edu/teaching/highcog/readings/s96.pdf?utm_source=chatgpt.com "The Empirical Case for Two Systems of Reasoning"
[15]: https://arxiv.org/abs/2311.12983?utm_source=chatgpt.com "[2311.12983] GAIA: a benchmark for General AI Assistants - arXiv.org"
[16]: https://arxiv.org/abs/2308.03688?utm_source=chatgpt.com "AgentBench: Evaluating LLMs as Agents"
[17]: https://arxiv.org/abs/2310.06770?utm_source=chatgpt.com "SWE-bench: Can Language Models Resolve Real-World GitHub Issues?"
[18]: https://www.nist.gov/publications/artificial-intelligence-risk-management-framework-ai-rmf-10?utm_source=chatgpt.com "Artificial Intelligence Risk Management Framework (AI RMF 1.0)"
[19]: https://eur-lex.europa.eu/EN/legal-content/summary/rules-for-trustworthy-artificial-intelligence-in-the-eu.html?utm_source=chatgpt.com "Rules for trustworthy artificial intelligence in the EU - EUR-Lex"
[20]: https://arxiv.org/abs/2304.03442?utm_source=chatgpt.com "Generative Agents: Interactive Simulacra of Human Behavior"

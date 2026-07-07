# From Language to Agency

- LLMs are no longer only **conversational generators**
  - they interpret requests
  - they produce reasoning traces
  - they call tools
  - they affect external states

- The shift is from **text completion** to **situated action**
  - ReAct interleaves reasoning and acting
  - Toolformer studies when and how LMs call APIs
  - agentic systems connect language to environments

- The polemic
  - **plans**, **norms**, **tools**, **memory**, and **traces**
  - matter more than bigger prompts and larger models

- The object of study
  - not the model alone
  - not the prompt alone
  - the **representations** mediating language, reasoning, and action

- Negative thesis
  - do not treat LLMs as black-box agents
  - do not let them act without inspectable commitments

Notes:
Open by making the audience feel the shift. The relevant object is no longer a chatbot producing answers, but a system that observes, stores, decides, calls tools, and changes the world. ReAct is useful because it explicitly stages reasoning traces and actions. Toolformer is useful because it turns tool invocation into a learnable interface problem. Then pivot: these papers make the shift visible, but they do not solve the governance problem. The missing layer is representational.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:0]{index=0}
ReAct :contentReference[oaicite:1]{index=1}
Toolformer :contentReference[oaicite:2]{index=2}

---

# Why this workshop?

- SKILLED-LLMs is the right venue
  - language models
  - knowledge representation
  - reasoning
  - ethics
  - statistics

- The workshop asks the right question
  - how to reconcile deep learning
  - with logic-based representations

- My reframing
  - “reasoning in LLMs” is not enough
  - ask what **representations** make reasoning usable

- KR-style reasoning with LLMs
  - should not be a wrapper around prompts
  - should expose commitments, constraints, and consequences

- Neuro-symbolic integration
  - is not only model + solver
  - it is mediated action through explicit artefacts

Notes:
Do not flatter the workshop generically. Say why the setting is technically appropriate. Their CFP already combines the three strands needed by the talk: language models, KR/reasoning, and ethical deployment. Then sharpen the move: the question is not whether LLMs “really reason” in isolation, but which intermediate representations let us connect linguistic competence to reliable inference and action.

Citations:
SKILLED-LLMs CFP :contentReference[oaicite:3]{index=3}
Neuro-symbolic LLM reasoning survey :contentReference[oaicite:4]{index=4}

---

# Talk contract: notions, not a framework

- This is not a system paper
  - no finished architecture
  - no benchmark claim
  - no empirical superiority claim

- The talk offers
  - definitions
  - distinctions
  - analogies
  - a representation-centric perspective

- Central claim
  - LLMs enter messy human worlds
  - explicit representations make action governable

- What representations buy us
  - **inspectability**
  - **debuggability**
  - **verifiability**
  - **contestability**
  - **auditability**

- Practical background
  - recent work on next-generation AI agents
  - the recurring issue was the same:
  - the missing middle between fluent generation and governed action

Notes:
Set expectations carefully. The keynote should not overclaim. The contribution is conceptual and agenda-setting. Mention the recent proposal experience only as motivation: it exposed a recurring design pressure in real-world agentic AI. Avoid naming the project. The important point is that “agent” talk becomes vague unless goals, plans, norms, tool contracts, memories, and traces become explicit objects.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:5]{index=5}

---

# GenAI, foundation models, and LLMs

- **Generative AI**
  - AI systems producing content
  - text, images, audio, video, code

- **Foundation models**
  - reusable capability substrates
  - trained with large data and compute

- Specialisation happens around the model
  - prompting
  - retrieval
  - adaptation
  - orchestration
  - tools

- **LLMs**, operationally
  - probabilistic sequence models
  - trained to continue linguistic context

- LLMs become **agentic**
  - only inside a wider control loop
  - with perception, memory, tools, and actuation

Notes:
Use this slide to neutralise terminology. GenAI is the broad family. Foundation models are reusable capability substrates. LLMs are one class of foundation model. The key move is operational: the LLM is not the whole agent. It becomes agentic only when embedded in infrastructure that gives it context, state, tool access, and consequences.

Citations:
GenAI slides :contentReference[oaicite:0]{index=0}
Toolformer :contentReference[oaicite:1]{index=1}
ReAct :contentReference[oaicite:2]{index=2}
Generative Agents :contentReference[oaicite:3]{index=3}

---

# LLMs as next-token predictors

- Basic mechanism
  - input: textual context
  - output: probability distribution
  - next token is sampled or selected

- The model does not “execute” language
  - it continues it
  - according to learned statistical regularities

- Reasoning-like behaviour may emerge
  - through patterns
  - through prompting
  - through test-time search

- But prediction is not agency
  - no sensors
  - no actuators
  - no persistent control by itself

- [Image placeholder]
  - take the “Basic Operation of LLMs” diagram
  - from the GenAI slides, page 5

Notes:
This should be short and slightly deflationary. The point is not to deny capabilities, but to locate them. Next-token prediction can support surprisingly rich behaviours, but the agentic interpretation comes from the surrounding system. Avoid saying “LLMs are just autocomplete” too strongly; the audience will reject it as simplistic. Say instead: the operational primitive is sequence continuation, and agency is a system-level property.

Citations:
GenAI slides, especially “Basic Operation of LLMs” :contentReference[oaicite:4]{index=4}

---

# What is an agent?

- Classical AI view
  - an agent receives **percepts**
  - and performs **actions**
  - in an **environment**

- Minimal formula
  - agent = situated action toward a goal

- Agent-oriented tradition
  - no single universally accepted definition
  - the term is overloaded by design

- Current LLM discourse needs discipline
  - “agent” cannot mean any prompted model
  - nor any script calling an API

- Useful stance
  - define the **locus of control**
  - define the **environmental effects**

Notes:
Russell and Norvig give the standard AI entry point: agents receive percepts from environments and perform actions. Wooldridge and Jennings are useful to remind the audience that “agent” has always been a modelling abstraction with multiple theoretical and engineering readings. The immediate target is contemporary sloppiness: calling a chat completion endpoint an “agent” hides the actual system boundary.

Citations:
Russell & Norvig :contentReference[oaicite:5]{index=5}
Wooldridge & Jennings :contentReference[oaicite:6]{index=6}
Gentle Introduction to Intelligent Agents :contentReference[oaicite:7]{index=7}

---

# What do people mean by “agent”?

- Classic AI
  - entity encapsulating intelligent behaviour

- Concurrency
  - entity encapsulating control flow
  - thread, process, daemon

- Distributed systems
  - party in an interaction protocol
  - client, server, broker, proxy

- Robotics
  - robot controller
  - or robot as mind + body

- Simulation and RL
  - simulated entity
  - policy-learning entity

Notes:
This is a vocabulary slide, not a taxonomy contribution. The purpose is to make explicit why the word “agent” is dangerous in LLM discourse. Different communities import different assumptions: intelligence, autonomy, control flow, embodiment, interaction, reward, or simulation. This prepares the later distinction between LLM, controller, and full agentic system.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:8]{index=8}
Agents, Agentic, Agent-Oriented slides :contentReference[oaicite:9]{index=9}

---

# Goal and environment

- A **goal**
  - partial description of a desired world state
  - individual or collective

- The “world”
  - environment
  - other agents
  - relevant external state

- Goal kinds
  - achievement: reach a state
  - test: acquire information
  - maintenance: preserve a condition

- Weak vs. strong goals
  - hard-coded policy
  - explicit goal representation

- The **environment**
  - where agents live and act
  - what enables and constrains action

Notes:
Introduce goals before perception and action. This keeps agency from becoming mere causality. A thermostat may have a weak maintenance goal. A navigation system may have a strong achievement goal. The distinction matters later: trustworthy LLM agents require explicit goal representations, not merely prompt-shaped wishes.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:10]{index=10}

---

# Perception and actuation

- **Perception**
  - gathering information from the environment
  - through sensors or interfaces

- Percepts are not yet knowledge
  - they may be noisy
  - they require representation
  - they may need interpretation

- **Actuation**
  - affecting the environment
  - or attempting to affect it

- Actions can fail
  - actuator failure
  - wrong assumptions
  - changed environment

- In LLM agents
  - perception and actuation are mediated
  - by software, tools, APIs, and memory

Notes:
Make the link to LLMs explicit. An LLM does not perceive a database, a browser, an email inbox, a simulator, or a robot. Another component serialises part of the environment into text or structured data. Likewise, the LLM does not act directly; it emits an action representation that another component interprets and executes. This is one of the first appearances of the intermediate-representation thesis.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:11]{index=11}
WebArena :contentReference[oaicite:12]{index=12}

---

# Deliberation and control loop

- A minimal control loop
  - sense
  - update memory
  - deliberate
  - act
  - repeat

- **Deliberation**
  - selects what to do
  - given goals, state, and options

- **Memory**
  - carries state across iterations
  - makes behaviour history-dependent

- **Control**
  - decides when to invoke capabilities
  - decides when to stop, retry, or escalate

- Agentic AI question
  - where is this loop implemented?

Notes:
Show the pseudo-code from the Gentle Introduction if useful. The key question is not “does the LLM deliberate?” but “which system implements the loop?” In most LLM agents, the loop is external: orchestration code senses, writes memory, prompts the model, parses outputs, executes tool calls, and handles failures. That external controller is scientifically and ethically important.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:13]{index=13}
ReAct :contentReference[oaicite:14]{index=14}

---

# Representation enters early

- Raw percepts are rarely enough
  - numbers
  - pixels
  - messages
  - logs
  - documents

- Agents need internal state
  - self
  - environment
  - other agents
  - ongoing activities

- Representation enables deliberation
  - path finding
  - localisation
  - planning
  - explanation

- Representation also enables governance
  - what was perceived?
  - what was inferred?
  - what was decided?

- [Image placeholder]
  - show perception → representation → deliberation → action

Notes:
This slide is the bridge from vocabulary to thesis. The Gentle Introduction already makes the engineering point: algorithms need well-defined input data, and representations make smarter action possible. Add the governance reading: once state is represented, it can be inspected, questioned, verified, logged, and audited.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:15]{index=15}
SKILLED-LLMs context pack :contentReference[oaicite:16]{index=16}

---

# Intelligence vs. autonomy vs. agency

- **Intelligence**
  - selecting and applying cognitive capabilities
  - in ways appropriate to the goal

- **Autonomy**
  - internal control over choices
  - goals, actions, timing, continuation

- **Agency**
  - effective interaction with the world
  - in view of a goal

- They are separable dimensions
  - more or less intelligent
  - more or less autonomous
  - more or less agentic

- Do not collapse them
  - fluent language is not autonomy
  - effective action is not intelligence

Notes:
This is the conceptual discipline slide. Intelligence concerns competence. Autonomy concerns control. Agency concerns goal-directed world interaction. The split is central because current “agentic AI” rhetoric often slides from one dimension to another: a model is linguistically competent, therefore it is treated as autonomous; a system can call tools, therefore it is treated as intelligent.

Citations:
Intelligence vs Autonomy vs Agency notes :contentReference[oaicite:17]{index=17}
Gentle Introduction to Intelligent Agents :contentReference[oaicite:18]{index=18}

---

# Autonomy: executive vs. motivational

- **Executive autonomy**
  - choosing how to act
  - while pursuing an assigned goal

- **Motivational autonomy**
  - choosing which goals to pursue
  - or whether to pursue them at all

- Most deployed LLM agents
  - have limited executive autonomy
  - should have constrained motivational autonomy

- Increasing autonomy changes the burden
  - stronger permissions
  - stronger monitoring
  - stronger accountability

- Governance question
  - who controls goals, policies, and stopping rules?

Notes:
This slide is important for avoiding inflated claims. Many systems called “autonomous agents” merely choose tool calls under a human-assigned goal. That is executive autonomy, often bounded by orchestration code. Motivational autonomy is far stronger and ethically riskier. The more autonomy we grant, the more explicit the representations of goals, constraints, permissions, and traces must be.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:19]{index=19}
Intelligence vs Autonomy vs Agency notes :contentReference[oaicite:20]{index=20}

---

# Corner cases clarify the dimensions

- Intelligence without autonomy or agency
  - theorem prover called by a human
  - offline planner
  - LLM used as an oracle

- Autonomy without intelligence or agency
  - isolated finite-state process
  - random internal controller
  - self-updating variable

- Agency without intelligence or autonomy
  - remote-controlled drone
  - fixed industrial robot
  - vending machine

- Main lesson
  - agency alone is not enough
  - competence alone is not control

- Key question
  - where are goals, norms, permissions, and traces?

Notes:
Use this slide to force the audience to keep the dimensions apart. The third case is the most useful for the keynote: artificial systems can affect the world without being intelligent or autonomous in any rich sense. Once effects exist, the governance question becomes unavoidable. We need to know where commitments are represented.

Citations:
Intelligence vs Autonomy vs Agency notes :contentReference[oaicite:21]{index=21}

---

# LLMs vs. agents

- Are LLMs agents?
  - not really
  - not fully
  - not by themselves

- LLMs have capabilities
  - linguistic interpretation
  - hypothesis generation
  - weak deliberation
  - tool-call proposal

- But LLMs alone lack
  - sensors
  - actuators
  - persistent memory
  - autonomous control loop

- In agentic AI, the agent may be
  - the controller software
  - the LLM-as-deliberation module
  - or the whole coupled system

- Be explicit about the boundary
  - model
  - controller
  - tools
  - memory
  - environment

Notes:
This slide should be stated firmly. An LLM endpoint is not an agent in the classical sense. It can be used as a deliberation component within an agent. Some communities will call the controller the agent; others will call the full LLM-plus-controller system the agent. Both can be acceptable if the boundary is explicit. What is not acceptable is hiding the boundary.

Citations:
ReAct :contentReference[oaicite:22]{index=22}
AgentBench :contentReference[oaicite:23]{index=23}
WebArena :contentReference[oaicite:24]{index=24}

---

# What is an agent in agentic AI?

- A system that uses a model to
  - interpret context
  - choose actions
  - call tools
  - update memory
  - pursue assigned goals

- The LLM may play “the mind”
  - but only metaphorically
  - deliberation is mediated by prompts

- Perception is externalised
  - browser state
  - files
  - APIs
  - messages
  - observations

- Action is externalised
  - function calls
  - tool invocations
  - database writes
  - robot commands

- The critical artefact
  - action representation
  - before execution

Notes:
This slide strengthens the representation-centric point. In most LLM agents, the model outputs text or structured action proposals. The environment is affected only after another component parses, validates, and executes them. That intermediate action representation is where governance can occur: validation, permission checks, simulation, logging, explanation, and refusal.

Citations:
ReAct :contentReference[oaicite:25]{index=25}
Toolformer :contentReference[oaicite:26]{index=26}
WebArena :contentReference[oaicite:27]{index=27}

---

# Artifacts, tools, function calls

- A **tool**
  - external capability
  - exposed through an interface

- Examples
  - API
  - database
  - calculator
  - planner
  - verifier
  - code executor

- Tools may support
  - perception
  - action
  - reasoning
  - coordination

- In LLM systems
  - tools are often function calls
  - described in natural language and schemas

- Tool use creates commitments
  - arguments
  - preconditions
  - effects
  - permissions

Notes:
Define tools pragmatically. The tool is not just a convenience for better answers. It is the bridge from language to effect. Once the system can call a tool, we need an explicit representation of what the tool does, which arguments it accepts, what side effects it may produce, and under which permissions it may be invoked.

Citations:
Toolformer :contentReference[oaicite:28]{index=28}
WebArena :contentReference[oaicite:29]{index=29}
LLM-as-a-Service slides :contentReference[oaicite:30]{index=30}

---

# Tools before LLMs: artifacts

- MAS research already modelled tools
  - not merely as functions
  - but as environment entities

- A&A distinction
  - agents are proactive
  - artifacts are reactive
  - environments become first-class

- Artifacts support
  - coordination
  - organisation
  - collaboration
  - shared activity

- LLM-era relevance
  - function calls are too thin
  - agents need structured environments

- [Image placeholder]
  - agent ↔ artifact ↔ environment
  - contrast with LLM → function call

Notes:
Use this slide to connect current LLM tooling with older MAS work. The A&A paradigm matters because it treats tools and environments as first-class modelling abstractions, not just callable functions. Ricci and Ciortea make the analogy explicit for agentic AI: MCP-style tools are useful, but function calls provide a poor abstraction for open, dynamic, evolvable environments.

Citations:
A&A meta-model :contentReference[oaicite:31]{index=31}
Ricci and Ciortea on tools in Agentic AI :contentReference[oaicite:32]{index=32}

---

# Tool engineering then and now

- Classical MAS
  - programmer designed adaptation code
  - agent controller exploited artifacts explicitly

- Engineering burden was local
  - model the artifact
  - model operations
  - model observations
  - model failures

- LLM-era systems shift the burden
  - describe the tool
  - expose schemas
  - let the model propose calls

- Value added of LLMs
  - tools can be specified in language
  - usage can be inferred from descriptions

- Risk
  - natural-language affordances are not contracts

Notes:
The contrast should not sound like “LLMs make old work obsolete.” They change the interface. Before, the engineer wrote adaptation logic. Now, engineers increasingly describe APIs in ways that LLMs can parse and use. This is powerful, but brittle: a natural-language tool description is not a formal contract unless we give it structure, validation, and governance semantics.

Citations:
Toolformer :contentReference[oaicite:33]{index=33}
Ricci and Ciortea :contentReference[oaicite:34]{index=34}
LLM-as-a-Service slides :contentReference[oaicite:35]{index=35}

---

# Memory is controlled state across time

- Memory is not “more context”
  - it is persistent managed state
  - across interactions and executions

- It supports
  - reasoning
  - planning
  - deliberation
  - adaptation

- It stores information about
  - environment
  - agent actions
  - action effects
  - messages
  - ongoing activities

- It also tracks internal state
  - goals
  - beliefs
  - commitments
  - failures

- Control matters
  - what is written
  - what is retrieved
  - what is forgotten

Notes:
Avoid treating memory as a vector database buzzword. Agent memory is governed state across time. The memory survey’s write-manage-read framing is useful because it makes memory part of the perception-action loop. Generative Agents and Reflexion show memory used for behaviour and self-improvement, but the governance question is broader: what should persist, under which schema, and with which rights?

Citations:
Memory for Autonomous LLM Agents :contentReference[oaicite:36]{index=36}
Generative Agents :contentReference[oaicite:37]{index=37}
Reflexion :contentReference[oaicite:38]{index=38}

---

# Memory types

- **Context**
  - transient working material
  - inside the current interaction

- **Episodic memory**
  - past events
  - observations, actions, outcomes

- **Semantic memory**
  - durable facts and concepts
  - world and domain knowledge

- **Procedural memory**
  - how to do things
  - skills, routines, code, plans

- **Institutional memory**
  - policies, norms, precedents
  - organisational commitments

Notes:
Keep the categories operational. Context is not long-term memory. Episodic memory supports learning from what happened. Semantic memory supports stable knowledge. Procedural memory stores reusable ways of acting; Voyager’s skill library is a useful example. Institutional memory is the governance-critical category for organisations: norms, policies, precedents, roles, authorisations.

Citations:
Memory for Autonomous LLM Agents :contentReference[oaicite:39]{index=39}
Generative Agents :contentReference[oaicite:40]{index=40}
Voyager :contentReference[oaicite:41]{index=41}

---

# Governed memory

- Provenance
  - where did this memory come from?

- Staleness
  - when does it expire?

- Salience
  - why should it be retrieved?

- Contradiction
  - what conflicts with it?

- Rights and deletion
  - who may access it?
  - when must it disappear?

Notes:
This is a governance slide, not an implementation slide. Memory becomes risky when it silently accumulates. Persistent state may become stale, biased, contradictory, private, unauthorised, or simply irrelevant. Retrieval is also governance: what the agent remembers shapes what it does. The mechanism must therefore be inspectable and auditable, especially in organisational settings.

Citations:
Memory for Autonomous LLM Agents :contentReference[oaicite:42]{index=42}
SKILLED-LLMs context pack :contentReference[oaicite:43]{index=43}

---

# Memory mechanisms must be explicit

- Retrieval
  - what is selected?
  - by similarity, rules, recency, salience?

- Update
  - what is overwritten?
  - what is appended?
  - what is consolidated?

- Forgetting
  - age-based
  - policy-based
  - rights-based
  - contradiction-based

- Criticality
  - unstructured data has loose schemas
  - loose schemas hide assumptions

- Failure examples
  - stale policy reused
  - private note retrieved
  - contradicted fact treated as current

Notes:
Use concrete examples. A legal assistant retrieves an old regulation and acts as if current. A workplace agent retrieves a private HR note in an unrelated task. A maintenance agent remembers an obsolete machine configuration. These are not hallucination failures. They are memory-governance failures. The remedy is not only better embeddings; it is explicit metadata, schema, and access policy.

Citations:
Memory for Autonomous LLM Agents :contentReference[oaicite:44]{index=44}
SKILLED-LLMs context pack :contentReference[oaicite:45]{index=45}

---

# Planning

- Classical planning asks for
  - initial state
  - goal state
  - actions
  - preconditions
  - effects

- The planner solves a formal problem
  - over states
  - through admissible actions

- Output
  - a plan
  - sequence or partial order of actions

- Plan representation can be
  - inspected
  - verified
  - simulated
  - executed

- Important distinction
  - planning is not plan execution

Notes:
This slide should be familiar to the symbolic AI audience, so keep it brief. The important move is to foreground formal representation: the planner needs a model of the world, a model of actions, and a goal description. The output is also a representation, not just a paragraph. That is why plans can be checked before execution.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:46]{index=46}
Planning for Intelligent Agents slides :contentReference[oaicite:47]{index=47}

---

# LLM “planning” is often different

- Inputs are usually underspecified
  - action set unknown
  - preconditions implicit
  - effects unstated
  - goal informal

- Output is usually fluent text
  - may be plausible
  - may be non-executable
  - may be incorrect

- Execution requires interpretation
  - parse text
  - select tools
  - fill arguments
  - handle errors

- Each interpretation step may fail
  - ambiguity
  - missing constraints
  - invalid action
  - unsafe side effect

- So the key object is the plan representation
  - not the planning prose

Notes:
Do not claim that LLMs can never help planning. The sharper claim is that fluent plan text is not the same object as a formal plan. LLMs may be useful for eliciting goals, proposing candidate plans, filling domain models, or suggesting action schemas. But before action, the candidate must be mediated by explicit representations that can be checked.

Citations:
Kambhampati et al., LLM-Modulo planning position :contentReference[oaicite:48]{index=48}
GenAI plan generation for BDI agents :contentReference[oaicite:49]{index=49}
ReAct :contentReference[oaicite:50]{index=50}

---

# Vocabulary takeaway

- Agents require more than models
  - goals
  - environment
  - perception
  - action
  - control

- LLMs are capability components
  - powerful
  - useful
  - not self-sufficient agents

- Tools and memory add power
  - but also commitments
  - and governance obligations

- Planning reveals the central issue
  - fluent text is weak
  - explicit plans are governable

- Therefore
  - **representations are the missing middle**

Notes:
Use this as the section close. The vocabulary is not preparatory bureaucracy. It is the first argument for the thesis. Once we distinguish model, agent, tool, memory, and plan, it becomes clear where governance can live: in explicit intermediate representations between language and action.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:51]{index=51}

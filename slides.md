# Opening and positioning

---

## From Language to Agency

- LLMs are shifting from **conversational generators** to components in systems that interpret goals, retain context, call tools, and modify external states

- This changes the scientific object: we are no longer studying only generated text, but **language-mediated action** in socio-technical environments

- ReAct makes the shift visible by interleaving **reasoning traces**, **actions**, and **observations** inside an agent loop

- Toolformer makes the shift visible from another angle: tool use becomes a learned interface between linguistic competence and external computation

- The polemic of the talk: **plans**, **norms**, **tools**, **memory**, and **traces** matter more than bigger prompts and larger models

Notes:
Start from the empirical shift everyone has seen: the chatbot becomes an agentic system once its outputs are connected to memory, tools, and external state. For a symbolic-AI audience, stress that the relevant question is not whether the LLM is “intelligent”, but what explicit commitments mediate between its linguistic behaviour and the actions it triggers. The keynote’s target is the missing representational layer between prompt and action.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:0]{index=0}
ReAct
Toolformer

---

## Why this workshop?

- SKILLED-LLMs is the natural venue because it explicitly joins **language models**, **knowledge representation**, **reasoning**, **ethics**, **statistics**, and **neuro-symbolic AI**

- The workshop’s core tension is exactly the one exploited here: how to reconcile data-driven language models with **logic-based representations of knowledge**

- I will treat “reasoning in LLMs” as a representational question: what structures let us inspect, constrain, verify, or reject an apparent inference?

- I will treat “KR-style reasoning with LLMs” as an interface question: what must be externalised before symbolic methods can govern LLM-mediated action?

- The talk is therefore not about replacing symbolic AI with LLMs, but about designing the **missing middle** where statistical fluency meets formal control

Notes:
Position the talk as internal to the workshop’s scope, not as an imported LLM-agent talk. The audience already understands KR, reasoning, and formal methods; the useful move is to show that LLM agents make these traditions operationally urgent again. Do not frame symbolic AI as a nostalgic corrective. Frame it as the discipline that knows how to make commitments explicit.

Citations:
SKILLED-LLMs CFP :contentReference[oaicite:1]{index=1}
Neuro-symbolic LLM reasoning survey

---

## Talk contract: notions, not a framework

- This is not a system paper: I will not present a finished architecture, a benchmark result, or a claim of empirical superiority

- The contribution is conceptual: definitions, distinctions, analogies, and a **representation-centric perspective** on LLM agents

- Central claim: LLMs are good at entering messy human worlds; explicit representations are good at making action governable

- Intermediate representations are not implementation details: they are the substrate for **inspectability**, **debugging**, **verification**, **contestability**, and **audit**

- The practical motivation comes from recent work on next-generation AI agents, where the recurring issue was the missing middle between fluent generation and governed action

Notes:
This slide protects the talk from overclaiming. Say explicitly that the goal is to share a lens, not to sell an architecture. The phrase “not implementation details” is important: it marks the transition from engineering convenience to governance substrate. When mentioning practical motivation, keep it generic. Do not name the submitted project or present proposal-specific material as a result.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:2]{index=2}

---

# Vocabulary: putting everyone on the same page

---

## Vocabulary: putting everyone on the same page

- Before discussing **trustworthy LLM agents**, we need to separate terms that are often collapsed in current discourse

- The key distinction is not only between **symbolic** and **statistical** AI, but between:
  - capability
  - control
  - environment
  - action
  - accountability

- Expert symbolic-AI audiences already know the formal side
  - the useful move is to map LLM vocabulary onto agent vocabulary

- Running example for this section:
  - an assistant that handles a travel reimbursement request
  - reads emails and receipts, checks policy, asks clarifications, fills forms, submits claims

Notes:
Use one concrete example throughout the vocabulary section. It prevents the talk from becoming taxonomic. The travel reimbursement assistant is mundane enough to be intuitive, but rich enough to expose goals, perception, tools, memory, planning, norms, and traces.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:0]{index=0}

---

## GenAI, foundation models, and LLMs

- **Generative AI** refers to AI systems capable of producing content
  - text, images, audio, video, code, structured documents

- **Foundation models** are reusable capability substrates
  - trained on large data and compute
  - later specialised by prompting, retrieval, fine-tuning, tools, orchestration

- **LLMs** are foundation models specialised around language
  - operationally: probabilistic sequence models over tokens
  - practically: interfaces to linguistic, factual, and procedural regularities

- **Agentic systems** are not just LLMs
  - they embed models into loops that observe, decide, call tools, update memory, and act

- Example:
  - ChatGPT drafting an email is GenAI
  - an assistant checking receipts and submitting a claim is an agentic system

Notes:
Avoid anthropomorphic definitions. “Understands” can be mentioned only with scare quotes or operational caveats. Stress that the agentic threshold is not linguistic quality, but coupling to state, tools, memory, and action.

Citations:
GenAI slides :contentReference[oaicite:1]{index=1}
ReAct
Toolformer
Generative Agents

---

## LLMs as next-token predictors

- Minimal operational view:
  - an LLM receives a context
  - estimates a probability distribution over possible next tokens
  - samples or selects one token
  - repeats the process

- This simple mechanism can produce complex behaviours
  - answering
  - translating
  - summarising
  - coding
  - step-by-step explanations

- But the generated sequence is still **text**, not action
  - action requires an external system to interpret or execute the output

- Example:
  - “Book the train to Lisbon” is just text until software maps it to search, booking, payment, and confirmation steps

[Image placeholder: recreate the “Basic Operation of LLMs” slide from GenAI slides, page 5]

Notes:
This slide should demystify without trivialising. The point is not “LLMs are only next-token predictors, therefore useless”. The point is “next-token prediction becomes operationally consequential only when embedded into a control architecture”.

Citations:
GenAI slides, page 5 :contentReference[oaicite:2]{index=2}

---

## Language is a weak substrate for agency

- Natural language is expressive and flexible
  - useful for vague goals, exceptions, preferences, and explanations

- Natural language is also ambiguous and underspecified
  - different readers may infer different commitments from the same sentence

- LLM outputs inherit this ambiguity
  - fluent text may be plausible but false
  - confident text may be non-executable

- Symbolic representations reduce ambiguity by forcing commitments
  - states, actions, preconditions, effects, norms, costs, deadlines

- Example:
  - “reimburse the trip if compliant” must become policy clauses, document checks, approval steps, and traceable decisions

Notes:
This slide begins the transition toward the main thesis. Do not attack language; language is what lets LLMs enter messy human contexts. The issue is that language alone is not enough once systems act, decide, or trigger organisational consequences.

Citations:
GenAI slides, “Language and Reasoning” :contentReference[oaicite:3]{index=3}
SKILLED-LLMs context pack :contentReference[oaicite:4]{index=4}

---

## What is an agent?

- Classical AI view:
  - an agent receives **percepts** from an environment
  - an agent performs **actions** in that environment

- Agent-oriented view:
  - no single universally accepted definition exists
  - the term must be disciplined by the modelling purpose

- Common uses of “agent”
  - robot controller
  - software component
  - BDI system
  - planner
  - reasoner
  - human proxy

- Minimal working definition for this talk:
  - an agent is a locus of control mediating goals, perceptions, decisions, and actions

- Example:
  - a thermostat is a thin agent; a reimbursement assistant is a richer organisational agent

Notes:
For a symbolic-AI audience, do not spend too long on Russell and Norvig. Use it as the common entry point, then immediately problematise the term. The key move is “locus of control”: it will later distinguish LLMs from agents.

Citations:
Russell & Norvig
Wooldridge & Jennings
Gentle Introduction to Intelligent Agents :contentReference[oaicite:5]{index=5}
Agents, Agentic, Agent-Oriented :contentReference[oaicite:6]{index=6}

---

## Goals: what makes action directed

- A **goal** specifies a desirable condition, outcome, or constraint over future states

- Goals may be explicit
  - “submit the reimbursement claim before Friday”

- Goals may be implicit or reconstructed
  - “help the employee recover eligible expenses”

- Weak goals guide behaviour without full formalisation
  - useful in open environments, but hard to verify

- Strong goals support planning and verification
  - formal goal state, success conditions, failure conditions

Notes:
Use the reimbursement example. A vague request like “help me get reimbursed” must be sharpened into operational goals: collect documents, classify expenses, check eligibility, submit before deadline. This is already representational work.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:7]{index=7}
Planning for Intelligent Agents :contentReference[oaicite:8]{index=8}

---

## Environment: where the agent is situated

- An **environment** is the part of the world the agent can observe, affect, or reason about

- Environments may be physical
  - robot, vehicle, sensor network, industrial plant

- Environments may be digital
  - databases, APIs, calendars, ticketing systems, document repositories

- Environments may be organisational
  - roles, permissions, policies, deadlines, responsibilities

- Example:
  - the reimbursement assistant’s environment includes inboxes, receipts, HR policy, ERP forms, approvers, and audit logs

Notes:
Stress that “environment” is not just a simulator or physical space. In LLM agents, environments are often institutional and informational. That makes representation harder: the relevant state is distributed across documents, systems, people, and norms.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:9]{index=9}
A&A meta-model :contentReference[oaicite:10]{index=10}

---

## Perception: how the agent gets state

- **Perception** is the channel through which the agent obtains information about its environment

- In LLM agents, perception is usually mediated
  - retrieved documents
  - tool outputs
  - API responses
  - user messages
  - screenshots or parsed webpages

- Perception is already representational
  - what is selected?
  - how is it encoded?
  - what uncertainty is preserved?

- Example:
  - a receipt OCR result is not “the receipt”
  - it is a fallible representation of vendor, amount, date, currency, and tax

Notes:
This slide is important for the governance argument. Perception is not passive. The agent never sees “the world”; it sees selected, encoded, possibly stale or erroneous representations of the world.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:11]{index=11}
Ricci and Ciortea on tools as observation/action channels :contentReference[oaicite:12]{index=12}

---

## Actuation: how the agent changes state

- **Actuation** is the channel through which the agent affects its environment

- In LLM agents, actuation is usually delegated to tools
  - send email
  - create ticket
  - update database
  - submit form
  - execute code
  - trigger workflow

- Actuation must be constrained
  - permissions
  - confirmations
  - rollback
  - rate limits
  - audit logs

- Example:
  - “submit claim” should not be a text continuation; it should be a controlled operation with preconditions and trace

Notes:
Contrast “the LLM says it submitted the claim” with “the system submitted the claim through a tool call whose result is logged”. This is where language becomes action, and where governance starts to matter.

Citations:
Gentle Introduction to Intelligent Agents :contentReference[oaicite:13]{index=13}
Ricci and Ciortea :contentReference[oaicite:14]{index=14}

---

## Deliberation: choosing what to do next

- **Deliberation** is the process that selects actions, plans, or intentions given goals and perceived state

- In symbolic agents, deliberation may use explicit structures
  - beliefs, desires, intentions
  - plans
  - norms
  - utility or preferences

- In LLM agents, deliberation often appears as generated text
  - chain-of-thought-like traces
  - task decomposition
  - tool-call proposals

- The governance problem:
  - generated deliberation is not automatically a valid plan, proof, or justification

- Example:
  - “I will check policy, then submit” is not enough; the system must know which policy version and which submission operation

Notes:
Use this slide to avoid equating visible reasoning traces with formal reasoning. They may help debugging, but they are not commitments unless mapped to explicit representations.

Citations:
ReAct
BDI and plan-generation paper :contentReference[oaicite:15]{index=15}
LLMs Can’t Plan position paper :contentReference[oaicite:16]{index=16}

---

## Control loop: the agent as an ongoing process

- An agent is better viewed as a **control loop**, not as a single model invocation

- Minimal loop:
  - perceive environment state
  - update internal state
  - deliberate about next step
  - act through tools
  - observe effects

- LLMs may support one or more loop phases
  - interpretation
  - hypothesis generation
  - plan sketching
  - explanation
  - interaction

- The loop is where autonomy appears
  - who decides when to continue, stop, ask, escalate, or act?

- Example:
  - after a rejected claim, the agent may ask for missing documents instead of hallucinating compliance

Notes:
Make clear that “agentic” is a property of the whole loop. A one-shot prompt is not an agent. A loop with state, goals, tools, and stopping conditions is closer to agenthood.

Citations:
ReAct
Generative Agents
AgentBench
Gentle Introduction to Intelligent Agents :contentReference[oaicite:17]{index=17}

---

## Intelligence vs. Autonomy vs. Agency

- **Intelligence**
  - competence in selecting and applying cognitive capabilities

- **Autonomy**
  - internal control over goal selection, action selection, or both

- **Agency**
  - effective interaction with the world in view of a goal

- These are separable dimensions
  - systems may be competent without control
  - systems may act without intelligence
  - systems may be autonomous only in weak senses

- Useful test:
  - what can the system do?
  - who controls when and why it does it?
  - what state does it actually change?

Notes:
This is the conceptual anchor for the next slides. Emphasise that many confusions about LLM agents come from collapsing these dimensions. Floridi’s artificial-agency thesis helps decouple agency from intelligence; agent-oriented engineering keeps autonomy central.

Citations:
Intelligence vs Autonomy vs Agency notes :contentReference[oaicite:18]{index=18}
Floridi, artificial agency :contentReference[oaicite:19]{index=19}

---

## Degrees of autonomy

- **No autonomy**
  - externally invoked capability
  - example: theorem prover called by a human

- **Executive autonomy**
  - the system chooses how to achieve an assigned goal
  - example: route planner selecting a path

- **Motivational autonomy**
  - the system can select, revise, or prioritise goals
  - example: an assistant postponing a task because compliance evidence is missing

- **Governed autonomy**
  - autonomy bounded by norms, permissions, roles, and escalation rules

- Key issue:
  - autonomy without explicit constraints becomes operational risk

Notes:
Introduce executive vs motivational autonomy here. It will be useful later when discussing LLM agents: many systems marketed as autonomous only have executive autonomy, and even that is mediated by scaffolding.

Citations:
Intelligence vs Autonomy vs Agency notes :contentReference[oaicite:20]{index=20}
SKILLED-LLMs context pack :contentReference[oaicite:21]{index=21}

---

## Corner cases clarify the vocabulary

- **Intelligence without autonomy or agency**
  - theorem prover, planner, diagnostic model, LLM-as-text-completion

- **Autonomy without intelligence or agency**
  - random state machine, isolated finite-state automaton, trivial self-updating process

- **Agency without intelligence**
  - thermostat, vending machine, industrial robot arm, database migration script

- **Agency without autonomy**
  - remote-controlled drone, fixed workflow executor, tool called by a human

- Lesson:
  - “agentic” claims must specify capability, control, and world effect separately

Notes:
This slide should be fast but precise. It gives the audience a diagnostic toolkit. The important punchline is that LLMs may show cognitive competence, but that alone does not make them autonomous agents.

Citations:
Intelligence vs Autonomy vs Agency notes :contentReference[oaicite:22]{index=22}

---

## LLMs vs agents

- Are LLMs agents?
  - not really, not fully, not by themselves

- LLMs have cognitive capabilities
  - language generation
  - classification
  - summarisation
  - abstraction
  - informal deliberation

- But LLMs alone lack situated control
  - they do not perceive environments directly
  - they do not actuate environments directly
  - they do not persistently manage goals and state

- In agentic AI, the agent is often the surrounding software loop
  - prompt construction, tool mediation, memory update, stopping rules, safety checks

- Alternative view:
  - agent = controller software + LLM + tools + memory + policies

Notes:
This slide should be explicit because the term “LLM agent” is misleading. The LLM may act as deliberation module, linguistic interface, or hypothesis generator. The agent is the whole controlled system that embeds it.

Citations:
ReAct
Toolformer
Generative Agents
AgentBench
WebArena

---

## LLMs as the “mind” of an agent?

- Tempting analogy:
  - controller software = body
  - tools = hands and sensors
  - memory = persistent state
  - LLM = mind

- Useful but dangerous
  - it highlights deliberation
  - it hides control, permissions, and execution semantics

- Better formulation:
  - the LLM is a **deliberation resource** inside a larger agent architecture

- Example:
  - the LLM may decide “ask the employee for the missing receipt”
  - the controller decides whether this action is allowed, logged, and actually sent

- Governance point:
  - the “mind” must not be the only place where commitments exist

Notes:
Use the mind metaphor only to dismantle it. It is rhetorically effective, but the keynote should not rely on it. The scientific object is the representation exchanged between the LLM and the rest of the system.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:23]{index=23}

---

## What is an agent in agentic AI?

- A practical definition:
  - a system that uses a model to interpret context, choose actions, call tools, update memory, and pursue assigned goals

- Typical components:
  - LLM or foundation model
  - controller loop
  - tool registry
  - memory store
  - policy layer
  - execution trace

- Typical control decisions:
  - continue, stop, ask user, call tool, escalate, revise plan

- Example:
  - an agent handling reimbursement must know when to ask HR instead of inventing an eligibility rule

- Representation question:
  - what is explicitly represented between those components?

Notes:
End the agent-definition block with the main thesis again. Once agents are systems, the relevant question becomes architectural and representational: what flows through the loop, in what format, with what guarantees?

Citations:
ReAct
Generative Agents
AgentBench
WebArena
SKILLED-LLMs context pack :contentReference[oaicite:24]{index=24}

---

## Artifacts, tools, function calls

- A **tool** is an external capability exposed through an interface
  - API, database, calculator, planner, verifier, simulator, code executor, ERP system

- A tool may support perception
  - retrieve receipt, query policy, inspect calendar, check database state

- A tool may support actuation
  - submit form, send email, update record, trigger workflow

- A tool may support reasoning
  - solve constraints, verify plan, compute tax, prove entailment

- Example:
  - `check_policy(expense, policy_version)` is not just a function call; it is a governed interface to institutional rules

Notes:
Do not reduce tools to “plugins”. Tools are where language touches the world. The interface must specify inputs, outputs, permissions, side effects, and failure modes.

Citations:
Toolformer
LLM-as-a-Service slides :contentReference[oaicite:25]{index=25}
Ricci and Ciortea :contentReference[oaicite:26]{index=26}

---

## Tools were not invented by LLM agents

- MAS research already modelled tools and resources through the **Agents & Artifacts** perspective

- In A&A:
  - agents are proactive loci of control
  - artifacts are reactive entities providing services and functions

- Artifacts shape the environment
  - they enable action
  - they constrain action
  - they mediate coordination

- Current LLM tooling revisits the same problem in a new setting
  - how agents discover, interpret, and exploit external capabilities

- Example:
  - a shared approval dashboard is an artifact, not merely a passive database

Notes:
This slide gives credit to the agent-oriented tradition. It also helps the symbolic-AI/MAS audience see that agentic AI is rediscovering older abstractions under different names.

Citations:
A&A meta-model :contentReference[oaicite:27]{index=27}
Ricci and Ciortea :contentReference[oaicite:28]{index=28}

---

## From programmed adaptation to described tools

- Classical MAS engineering often required explicit adaptation code
  - the programmer connected agent controller and external artifacts

- The agent needed hand-coded knowledge of:
  - what the artifact does
  - how to call it
  - what results mean
  - how failures should be handled

- LLM tooling shifts part of this burden into descriptions
  - tool name
  - natural-language description
  - input schema
  - output schema
  - usage examples

- Value added of LLMs:
  - they can exploit natural-language tool specifications

- Risk:
  - “understanding the tool description” is not equivalent to respecting tool semantics

Notes:
This slide should be balanced. LLMs reduce engineering friction, but they also move critical semantics into informal descriptions. That is convenient but dangerous.

Citations:
Toolformer
LLM-as-a-Service slides :contentReference[oaicite:29]{index=29}
Ricci and Ciortea :contentReference[oaicite:30]{index=30}

---

## Tool descriptions are intermediate representations

- A tool description is already a representation of action
  - name
  - arguments
  - types
  - constraints
  - effects
  - errors

- Weak description:
  - “send an email to the user”

- Stronger description:
  - recipient must be authorised
  - content must avoid personal data leakage
  - call produces a message ID and audit event

- Best case:
  - tool descriptions become inspectable contracts between LLM reasoning and external action

- Example:
  - `submit_claim` should expose preconditions: employee ID, policy match, receipt evidence, approval path

Notes:
Make this one of the first explicit “intermediate representation” slides. The audience should see that the thesis is not abstract: even a tool schema is a governance artefact.

Citations:
Toolformer
Ricci and Ciortea :contentReference[oaicite:31]{index=31}
SKILLED-LLMs context pack :contentReference[oaicite:32]{index=32}

---

## Memory is controlled state across time

- **Memory** is persistent, managed state available beyond the current interaction

- Memory supports:
  - reasoning and deliberation
  - planning across steps
  - tracking actions and effects
  - maintaining goals and commitments

- Memory is not just “more context”
  - context is transient input
  - memory is selected, stored, retrieved, revised, and forgotten

- Example:
  - the agent remembers that the employee already provided a hotel invoice, but not their private travel notes

- Governance question:
  - who decides what is stored, retrieved, exposed, corrected, or deleted?

Notes:
Define memory as controlled state. This avoids the common confusion between context window, vector database, chat history, and institutional record.

Citations:
Memory survey
Generative Agents
Reflexion
SKILLED-LLMs context pack :contentReference[oaicite:33]{index=33}

---

## Types of memory in LLM agents

- **Context**
  - current prompt, recent messages, retrieved snippets, active tool outputs

- **Episodic memory**
  - records of past events, interactions, decisions, and execution traces

- **Semantic memory**
  - relatively stable knowledge about concepts, policies, entities, and domains

- **Procedural memory**
  - reusable know-how: workflows, plans, scripts, tool-use patterns

- **Institutional memory**
  - organisational records: roles, authorisations, policies, precedents, obligations

Notes:
Use the reimbursement example for each memory type. Context: current claim. Episodic: previous rejection. Semantic: travel policy. Procedural: how to submit in ERP. Institutional: who can approve and what must be retained.

Citations:
Memory survey
Generative Agents
Voyager
SKILLED-LLMs context pack :contentReference[oaicite:34]{index=34}

---

## Governed memory needs metadata

- **Provenance**
  - where did this information come from, and through which tool or user?

- **Staleness**
  - when was it last checked, and can it still be relied upon?

- **Salience**
  - why is this memory relevant to the current goal?

- **Contradiction**
  - does it conflict with newer evidence, policy, or user correction?

- **Access and deletion**
  - who may read it, retain it, export it, correct it, or erase it?

Notes:
The point is that memory without metadata is not governed memory. Retrieval-augmented agents often treat remembered content as useful text. For responsible agents, memory entries need lifecycle, rights, and evidential status.

Citations:
Memory survey
SKILLED-LLMs context pack :contentReference[oaicite:35]{index=35}

---

## Memory failures: practical criticalities

- Bad retrieval
  - the agent retrieves an obsolete travel policy and applies the wrong reimbursement threshold

- Bad update
  - the agent stores a hallucinated fact as if it were user-provided evidence

- Bad forgetting
  - the agent retains sensitive documents after the claim is closed

- Bad schema
  - free-text notes mix facts, assumptions, preferences, and private data

- Bad conflict handling
  - the agent has two policy versions and silently chooses one

Notes:
This slide makes memory concrete. It also prepares the representation-centric conclusion: memory must be structured enough to support audit, correction, and contestation.

Citations:
Memory survey
SKILLED-LLMs context pack :contentReference[oaicite:36]{index=36}

---

## Planning: classical view

- Classical planning starts from explicit representations:
  - current state
  - goal state
  - admissible actions
  - action preconditions
  - action effects

- The planner is an exact problem solver over a formal model
  - search space of states or plans
  - correctness relative to the model
  - output as executable plan structure

- A plan is not merely an explanation
  - it is a structured artefact connecting actions to goal achievement

- Example:
  - `collect_receipt -> validate_policy -> request_approval -> submit_claim`

- Key property:
  - plans can be inspected, checked, simulated, repaired, or verified

Notes:
Use this slide to recall fundamentals, not to teach planning. The audience knows this. The useful contrast is with LLM “plans” as fluent but non-binding text.

Citations:
Planning for Intelligent Agents :contentReference[oaicite:37]{index=37}

---

## Planning requires action models

- Planning depends on knowing what actions exist
  - `ask_user`
  - `retrieve_policy`
  - `validate_receipt`
  - `submit_claim`
  - `notify_approver`

- Each action should specify preconditions
  - what must be true before the action is allowed?

- Each action should specify effects
  - what changes after successful execution?

- Each action should specify failure modes
  - timeout, missing permission, inconsistent document, rejected claim

- Example:
  - `submit_claim` requires validated expenses and produces claim ID or rejection reason

Notes:
This slide should be practical and slightly unforgiving. Without action models, “planning” degenerates into plausible sequencing. In organisational settings, side effects matter.

Citations:
Planning for Intelligent Agents :contentReference[oaicite:38]{index=38}
BDI plan-generation paper :contentReference[oaicite:39]{index=39}

---

## How LLMs usually “plan”

- LLM plans are often natural-language decompositions
  - useful as sketches
  - not necessarily executable
  - not necessarily sound

- The admissible actions may be unknown or only described informally
  - the model may invent steps or assume unavailable tools

- The world state is usually partial and textual
  - documents, messages, retrieved fragments, user claims

- The plan is not a formal object
  - execution requires interpretation
  - interpretation can introduce new errors

- Example:
  - “obtain manager approval” is underspecified unless the system knows who the manager is and how approval is recorded

Notes:
Do not say LLMs cannot help with planning in a simplistic way. The stronger and fairer claim is that LLM planning is often plan-like text unless grounded in explicit action/state representations.

Citations:
LLMs Can’t Plan position paper :contentReference[oaicite:40]{index=40}
BDI plan-generation paper :contentReference[oaicite:41]{index=41}

---

## Planning: where LLMs can still help

- LLMs can help elicit planning models
  - infer candidate actions from manuals, procedures, and examples

- LLMs can help repair underspecified goals
  - ask clarifying questions or propose operational success criteria

- LLMs can help generate candidate plans
  - useful when no formal model is initially available

- LLMs can help explain formal plans
  - translate symbolic plans into user-facing language

- But validation should be external
  - planner, verifier, simulator, policy checker, or human approver

Notes:
This slide prevents the talk from sounding anti-LLM. The position is neuro-symbolic: LLMs are excellent at entering messy human descriptions; formal tools are needed to govern action.

Citations:
LLMs Can’t Plan position paper :contentReference[oaicite:42]{index=42}
BDI plan-generation paper :contentReference[oaicite:43]{index=43}
SKILLED-LLMs context pack :contentReference[oaicite:44]{index=44}

---

## Vocabulary recap: the missing middle

- We now have the ingredients:
  - goals
  - environments
  - perception
  - actuation
  - deliberation
  - control loops
  - tools
  - memory
  - plans

- The central issue is how these ingredients are represented

- Weak agentic AI:
  - everything stays in prompts, traces, and informal text

- Stronger agentic AI:
  - commitments are externalised into inspectable intermediate representations

- Thesis preview:
  - trustworthy agents are representation-centric, not prompt-centric

Notes:
This is the closing slide for the vocabulary section. It should bridge into the next section, likely on reasoning, symbolic vs LLM reasoning, or dual-system analogies.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:45]{index=45}

---

# The common technical pattern behind agentic AI
---

## The common technical pattern behind agentic AI

- The current pattern is not mysterious:
  - **natural language in**
  - model-mediated interpretation
  - tool or memory access
  - external action or structured answer

- The LLM is rarely the whole system
  - it is usually embedded in orchestration software
  - the software controls context, tools, memory, permissions, and stopping

- Agentic AI therefore shifts the question:
  - from “what can the model say?”
  - to “what can the system do after the model says something?”

- Running example:
  - “Please reimburse my Lisbon trip”
  - the system must parse intent, collect evidence, check policy, plan actions, and submit or escalate

Notes:
This section should show that many agentic-AI systems share the same hidden pattern. Natural language is used to enter the system, but execution depends on representations, tools, state, and control logic. This is the bridge from prompt engineering to intermediate representations.

Citations:
M11 Agents & Tools, LLM vs agentic system :contentReference[oaicite:0]{index=0}
SKILLED-LLMs context pack :contentReference[oaicite:1]{index=1}

---

## Natural language as an interface

- Natural language is now the default interface to AI systems
  - users describe goals, constraints, preferences, exceptions, and examples

- This is powerful because it lowers formalisation cost
  - no schema required upfront
  - no programming language required
  - partial intentions can still be useful

- It is also fragile because language is underspecified
  - “cheap hotel”, “reasonable delay”, “urgent”, “compliant” need interpretation

- Prompt engineering is the practice of shaping this interface
  - the prompt becomes a temporary specification of expected behaviour

- Example:
  - “reimburse my trip” is weak
  - “check receipts against policy version X and do not submit without approval” is stronger

Notes:
Stress the interface role before discussing reasoning. Natural language lets non-experts access complex computation, but it also pushes specification work onto users. The better prompt is already a more structured representation of intent.

Citations:
GenAI slides on language and reasoning :contentReference[oaicite:2]{index=2}

---

## Prompt engineering: making intent legible

- A good prompt usually improves five things:
  - **clarity**: what exactly should be done?
  - **completeness**: what information is needed?
  - **context**: what background matters?
  - **constraints**: what is forbidden or required?
  - **examples**: what outputs count as acceptable?

- Prompt engineering is useful because LLMs are sensitive to formulation
  - small changes may alter decomposition, style, assumptions, and risk tolerance

- But prompt engineering is not governance
  - prompt text is weakly typed
  - constraints are not necessarily enforced
  - violations may be hard to detect

- Example:
  - “act as a reimbursement officer” is role-play
  - “call `check_policy` before `submit_claim`” is closer to a procedural constraint

Notes:
Introduce prompt engineering as a practical response to the ambiguity of natural language. Then immediately mark its limit: prompts are not contracts, policies, or proofs. They are soft specifications unless connected to external control.

Citations:
GenAI slides :contentReference[oaicite:3]{index=3}
M11 on prompt quality and brittleness in ReAct-style agents :contentReference[oaicite:4]{index=4}

---

## Prompt engineering patterns: few-shot

- Few-shot prompting gives the model examples of desired behaviour
  - input → output
  - case → decision
  - question → answer format

- It works by conditioning the model on a local behavioural pattern
  - often enough for formatting, classification, and simple transformations

- Example:
  - receipt: “hotel, 120€, Lisbon” → category: accommodation, requires receipt
  - receipt: “wine, 38€” → category: non-reimbursable, explain reason

- Strength:
  - quick way to induce task conventions without training

- Weakness:
  - examples may bias the model toward superficial analogy

Notes:
Use few-shot as the simplest case of natural-language specification. The examples are not just data: they are an informal representation of a task policy. But the model may generalise from the wrong feature.

Citations:
GenAI slides :contentReference[oaicite:5]{index=5}

---

## Prompt engineering patterns: chain-of-thought

- Chain-of-thought prompting asks the model to produce intermediate reasoning steps before the final answer

- It often improves multi-step tasks because it externalises a reasoning trace
  - decompose
  - compute
  - compare
  - conclude

- Example:
  - list expenses
  - match each expense to policy
  - identify missing evidence
  - decide whether submission is allowed

- Strength:
  - useful for debugging the model’s apparent reasoning

- Weakness:
  - a fluent trace is not a proof, plan, or guarantee of correctness

Notes:
Keep the distinction sharp. Chain-of-thought makes reasoning visible, but not necessarily valid. For the keynote thesis, CoT is a weak intermediate representation: inspectable, but not reliably executable or verifiable.

Citations:
ReAct discussion in M11 :contentReference[oaicite:6]{index=6}
LLM-Modulo position paper on LLMs and System-2-like tasks :contentReference[oaicite:7]{index=7}

---

## Prompt engineering patterns: Tree of Thoughts

- Tree-of-Thought prompting explores multiple candidate reasoning paths rather than a single chain

- The model can branch, evaluate alternatives, and backtrack
  - path A: submit now
  - path B: ask for missing receipt
  - path C: escalate to manager

- This is useful for long-horizon tasks
  - early mistakes can otherwise propagate through the whole trajectory

- Example:
  - compare possible reimbursement strategies under budget, policy, deadline, and missing-document constraints

- Weakness:
  - search over thoughts is still not search over a formal state-action model

Notes:
Present Tree of Thoughts as a bridge toward planning, but not as classical planning. It gives a search-like structure in language space. The representation remains informal unless candidate branches are mapped to actions, states, and constraints.

Citations:
M11 taxonomy and long-horizon tool use :contentReference[oaicite:8]{index=8}
M11 on Tree of Thoughts and planning/search :contentReference[oaicite:9]{index=9}
LLM-Modulo position paper :contentReference[oaicite:10]{index=10}

---

## Prompting as weak formalisation

- Prompting often forces users to become more explicit
  - state the task
  - state assumptions
  - state constraints
  - provide examples
  - specify output format

- This is useful
  - many humans become clearer because the machine is brittle

- But it is also a symptom
  - the human adapts to the limits of the AI interface

- Example:
  - instead of “can I get this trip reimbursed?”
  - users learn to say “classify each receipt, cite the policy, flag missing evidence, and do not submit”

- Prompt engineering is therefore part of a larger adaptation process

Notes:
This slide prepares Floridi. The point is not that prompt engineering is bad; it is that it shifts work onto humans. They learn to speak in machine-friendly ways. This is a form of informal enveloping.

Citations:
GenAI slides on ambiguity and reasoning :contentReference[oaicite:11]{index=11}
AI and Human Adaptation notes :contentReference[oaicite:12]{index=12}

---

## Enveloping

- Floridi’s **enveloping**:
  - redesign the environment so that limited artificial agents can operate effectively

- The core inversion:
  - not only AI adapting to the world
  - but the world adapting to AI

- Classical examples:
  - factory floors redesigned around robots
  - roads, maps, sensors, and signals redesigned around autonomous vehicles
  - forms redesigned around machine-readable fields

- LLM-era example:
  - humans learn prompt-shaped language so chatbots can interpret them

- Governance question:
  - who decides which adaptations are acceptable?

Notes:
Use this slide as a conceptual turning point. Prompt engineering is not isolated; it is a small instance of a broader socio-technical phenomenon. The world becomes more legible to machines. The ethical issue is whether this transformation is deliberate, visible, and contestable.

Citations:
Floridi, The Fourth Revolution / La quarta rivoluzione :contentReference[oaicite:13]{index=13}
AI and Human Adaptation notes :contentReference[oaicite:14]{index=14}

---

## Enveloping in agentic AI

- Agentic AI needs envelopes to work reliably
  - structured tool schemas
  - constrained workflows
  - machine-readable policies
  - typed memory entries
  - explicit approval states

- Bad enveloping:
  - humans silently adapt to brittle systems
  - organisational judgement is compressed into checkboxes
  - responsibility becomes hard to locate

- Better enveloping:
  - intermediate representations make adaptations explicit
  - users can inspect, contest, and revise them

- Example:
  - a travel policy becomes a versioned rule base, not just a PDF pasted into a prompt

- Thesis:
  - governed representations are the ethical alternative to invisible adaptation

Notes:
This slide connects Floridi directly to the keynote thesis. The goal is not to avoid enveloping altogether. Some enveloping is necessary. The point is to make the envelope explicit, auditable, and contestable.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:15]{index=15}
AI and Human Adaptation notes :contentReference[oaicite:16]{index=16}

---

## Natural language as the means for reasoning

- Natural language is not only the user interface
  - it is also the medium in which LLMs express intermediate reasoning

- LLMs predict tokens in context
  - this can generate explanations, derivations, decompositions, and justifications

- This gives LLMs broad task coverage
  - many domains already encode knowledge and procedures in language

- But natural-language reasoning is loose
  - ambiguity, missing premises, implicit norms, and rhetorical fluency remain

- Example:
  - “the hotel is reasonable” sounds like a conclusion, but policy requires a threshold, location, date, and role

Notes:
Bring back the GenAI slides: language is expressive enough to represent complex and abstract concepts, but it admits ambiguity and variable interpretation. This is why LLMs are useful and dangerous in the same move.

Citations:
GenAI slides, language and reasoning :contentReference[oaicite:17]{index=17}

---

## The generality of natural language

- Natural language can describe almost anything
  - goals
  - rules
  - exceptions
  - plans
  - observations
  - explanations

- This makes LLMs general-purpose mediators
  - they can translate messy inputs into candidate structures

- But generality is not precision
  - the same sentence may support multiple operational interpretations

- Example:
  - “submit only if the claim is complete”
  - complete according to whom, which policy, which evidence, and which deadline?

- Representation-centric view:
  - natural language proposes; explicit representations commit

Notes:
Use this sentence as a compact slogan: language proposes, representations commit. It should recur later in the talk.

Citations:
GenAI slides :contentReference[oaicite:18]{index=18}
SKILLED-LLMs context pack :contentReference[oaicite:19]{index=19}

---

## From single-pass generation to closed-loop agency

- A simple LLM interaction is approximately:
  - input → output

- An agentic system is a closed loop:
  - observe → decide → act → observe → …

- The system depends on two histories:
  - previously emitted tokens
  - outcomes of previous external actions

- This is the central technical shift
  - from stateless prediction
  - to stateful control

- Example:
  - after a failed policy lookup, the agent may retry, ask a user, or stop

Notes:
Start the agentic-loop part here. This is the cleanest contrast from M11: single-pass computation versus closed-loop computation. It should visually look like a loop.

Citations:
M11, closed-loop vs single-pass computation :contentReference[oaicite:20]{index=20}

---

## Agentic systems are stateful

- Agentic systems carry forward explicit state
  - current goal
  - task list or plan
  - intermediate results
  - memory of observations
  - tool outputs
  - error and recovery status

- This is different from relying only on the context window
  - context is transient
  - state is managed

- Example:
  - the agent remembers that the receipt parser failed and must not treat missing amount as zero

- Governance implication:
  - state must be inspectable, mutable, and attributable

Notes:
Emphasise that state is the first intermediate representation. Without explicit state, the system cannot be properly debugged or audited.

Citations:
M11, agentic systems are stateful :contentReference[oaicite:21]{index=21}

---

## The agentic feedback loop

- Once a tool call or action is executed, the system receives feedback from the environment

- Feedback may include:
  - search results
  - execution errors
  - retrieved records
  - computed values
  - updated world state
  - execution traces

- The feedback is folded into the next decision
  - continue
  - revise
  - retry
  - ask
  - stop

- Example:
  - `submit_claim` returns “missing approval”
  - the next step becomes `request_approval`, not final answer generation

Notes:
This slide makes clear why agentic AI exceeds text generation. The system reacts to external consequences. That is where tool outputs become evidence and state updates.

Citations:
M11, environment feedback loop :contentReference[oaicite:22]{index=22}

---

## Canonical tool-use loop

- Practical loop:
  - perceive state from request, memory, environment, and tool outputs
  - plan whether to answer, decompose, or act
  - select tool
  - call tool with arguments
  - verify and integrate result
  - act, continue, or respond

- The LLM may support several steps
  - interpret request
  - propose tool
  - draft arguments
  - summarise returned evidence

- The controller should govern the loop
  - validation, permissions, retries, logging, escalation

- Example:
  - search policy → parse receipt → validate amount → request approval → submit claim

Notes:
This is a key slide. It gives the audience the “common technical pattern” in one place. Use it as the operational model for the rest of the talk.

Citations:
M11, canonical tool-use loop :contentReference[oaicite:23]{index=23}

---

## ReAct: reasoning, action, observation

- ReAct makes the loop explicit
  - reasoning → action → observation → reasoning → …

- Reasoning traces guide tool choice
  - “I need current policy”
  - “I should query the HR policy database”

- Actions externalise intent
  - search, retrieve, calculate, submit, ask

- Observations ground the next step
  - tool result, error, missing data, contradiction

- Weakness:
  - formatting, argument generation, and long-horizon reliability remain brittle

Notes:
Use ReAct as the canonical historical pattern. It is effective because it makes the loop visible, but visibility is not the same as formal control. That is the transition toward representations.

Citations:
M11, prompted tool use and ReAct :contentReference[oaicite:24]{index=24}

---

## Toolformer: tool use as learned policy

- Toolformer studies models that learn to insert API calls into text

- The model learns:
  - when to call
  - which tool to call
  - how to pass arguments
  - how to use returned outputs

- Example:
  - `get_exchange_rate(EUR, USD, date)`
  - result re-enters the context and changes the answer

- This goes beyond token generation
  - output is interpreted under a schema
  - software executes the call
  - the result becomes new evidence

- Governance issue:
  - learned tool-use policies still need constraints and verification

Notes:
Contrast ReAct and Toolformer. ReAct is largely prompt/orchestration driven; Toolformer moves tool-use policy partly into the model. In both cases, the action interface becomes crucial.

Citations:
M11, Toolformer and tool-use policies :contentReference[oaicite:25]{index=25}
M11, Toolformer architecture :contentReference[oaicite:26]{index=26}
M11, beyond token generation :contentReference[oaicite:27]{index=27}

---

## A compact abstraction of agentic systems

- A useful abstraction:
  - `s_{t+1} = f(s_t, LLM(s_t), Env)`

- Where:
  - `s_t` is current system state
  - `LLM(s_t)` supplies a proposal, decision, or action
  - `Env` determines the result of interaction
  - `f` updates state for the next step

- This captures the essential move:
  - from prediction
  - to control
  - from answer generation
  - to state transition

- Example:
  - state contains “receipt missing”
  - LLM proposes `ask_user`
  - environment returns uploaded file
  - state updates to “receipt available”

Notes:
This is useful for the expert audience. It abstracts away implementation details while preserving the technical pattern. The key point is that LLM output is only one term in the transition function.

Citations:
M11, compact abstract representation :contentReference[oaicite:28]{index=28}

---

## Tool use addresses three LLM limits

- Standalone LLMs have stale or missing world knowledge
  - retrieval and search update the evidence base

- Standalone LLMs have weak symbolic reliability
  - calculators, solvers, verifiers, and code execution can check results

- Standalone LLMs cannot act on environments
  - APIs, workflows, and actuators connect text to state change

- Practical architecture:
  - LLM core + memory + planner + tool interface

- Example:
  - policy retrieval + tax calculator + ERP submission beats “answer from memory”

Notes:
This slide should be pragmatic. Tool use is not decorative. It compensates for specific technical limitations of standalone LLMs.

Citations:
M11, what counts as tool use :contentReference[oaicite:29]{index=29}

---

## Agentic loop: failure modes

- Tool overuse
  - unnecessary calls increase latency, cost, and attack surface

- Tool underuse
  - the model answers from memory and hallucinates current facts

- Bad trust calibration
  - retrieved or executed outputs may be wrong, stale, or adversarial

- Trajectory opacity
  - final answer may look correct while intermediate steps were invalid

- Irreversible action
  - sending, deleting, submitting, or paying may be hard to undo

Notes:
This slide motivates governance. The loop is powerful because it changes state; it is dangerous for the same reason. The question becomes how to constrain and audit the trajectory, not just the final answer.

Citations:
M11, open problems in tool use :contentReference[oaicite:30]{index=30}

---

## The common pattern, restated

- Agentic AI typically combines:
  - natural-language interface
  - LLM-mediated interpretation
  - explicit state
  - tool calls
  - feedback loop
  - memory
  - external action

- Prompt engineering shapes the front door
  - but the system’s behaviour depends on the whole loop

- Enveloping shapes the world around the AI
  - but it should be visible and governable

- The scientific object is therefore not “the prompt”
  - it is the intermediate representation connecting language to action

- Next step:
  - distinguish reasoning traces from governable reasoning artefacts

Notes:
This is the section conclusion. It should make the thesis unavoidable: natural language is useful, but every useful agentic system immediately creates representations of state, tools, memory, and action. The next section can move to reasoning.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:31]{index=31}
M11, tool-use loop and agentic systems :contentReference[oaicite:32]{index=32}

---

# Reasoning: symbolic AI, LLMs, and the dual-process analogy

---

## Reasoning: symbolic AI, LLMs, and the dual-process analogy

- This section is not about deciding whether LLMs **really reason**

- It asks a more operational question:
  - what representations are transformed?
  - by which operations?
  - under which constraints?
  - with which checks?

- The contrast:
  - symbolic AI reasons over explicit structures
  - LLMs generate plausible reasoning-like continuations in language

- The bridge:
  - intermediate representations can turn fluent reasoning traces into governable artefacts

Notes:
Frame the section as a deflationary move. Avoid metaphysical debates about “real reasoning”. For this keynote, reasoning matters because it affects action. The right question is whether the reasoning process produces commitments that can be inspected, checked, repaired, and contested.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:0]{index=0}
LLM-Modulo position paper :contentReference[oaicite:1]{index=1}

---

## What is reasoning?

- Pragmatic definition:
  - reasoning is the **controlled transformation of representations**

- Reasoning may serve different purposes:
  - derive a conclusion
  - justify a decision
  - select an action
  - revise a belief
  - resolve a conflict

- “Controlled” means:
  - operations are constrained
  - conclusions are checkable
  - failures are diagnosable

- Example:
  - from “receipt date = 17 July” and “policy applies from 1 July”
  - infer that the current policy is applicable

- Example:
  - from “hotel missing invoice” and “invoice required”
  - select action `ask_user_for_invoice`

Notes:
Use this definition because it is neutral between logic, planning, probabilistic inference, argumentation, and LLM traces. The key word is “controlled”: without constraints and checks, we only have association or generation.

Citations:
Russell & Norvig
Sloman
Evans & Stanovich
LLM-Modulo position paper :contentReference[oaicite:2]{index=2}

---

## Reasoning as representation transformation

- Deductive reasoning:
  - premises + rules → entailed conclusion

- Planning:
  - state + actions + goal → action sequence

- Diagnosis:
  - symptoms + causal model → likely explanation

- Normative reasoning:
  - facts + norms + roles → obligations and permissions

- LLM-style reasoning trace:
  - prompt + context → plausible intermediate text → answer

Notes:
This slide sets up the central comparison. The first four cases make the transformed representation explicit. The LLM case may only expose a textual trace. The question is whether that trace is grounded in a representation that can be checked.

Citations:
Planning for Intelligent Agents :contentReference[oaicite:3]{index=3}
SKILLED-LLMs CFP on KR-style reasoning and LLM reasoning :contentReference[oaicite:4]{index=4}

---

## What the definition avoids

- It avoids asking:
  - does the system “really” understand?
  - does the system “really” reason?
  - is the reasoning human-like?

- It asks instead:
  - what is the input representation?
  - what is the output representation?
  - what operations connect them?
  - what checks constrain them?

- For LLM agents, this is crucial
  - a fluent explanation may be useful
  - but action needs commitments

- Example:
  - “this expense seems eligible” is weak
  - `eligible(expense_42, policy_2026_v3)` is checkable

Notes:
Use this slide to make the engineering turn explicit. Symbolic-AI people will appreciate that the issue is not internal phenomenology but representation, transformation, and validation.

Citations:
LLM-Modulo position paper :contentReference[oaicite:5]{index=5}
SKILLED-LLMs context pack :contentReference[oaicite:6]{index=6}

---

## Symbolic reasoning

- Symbolic reasoning operates over explicit structures:
  - formulae
  - terms
  - states
  - actions
  - constraints
  - proofs
  - norms

- The symbols have roles within a formal or semi-formal system
  - values
  - categories
  - types
  - relations
  - constraints

- Example:
  - `amount(expense_42, 120)`
  - `category(expense_42, hotel)`
  - `requires_receipt(hotel)`

- Reasoning changes the symbolic state
  - infer, classify, plan, prove, reject, revise

Notes:
Define symbolic broadly enough to include logic, planning, constraints, type systems, process models, and normative systems. The point is not that symbols must be human-readable strings. The point is that they play discrete roles in an explicit structure.

Citations:
Russell & Norvig
A&A and explicit modelling of agents, artifacts, and environments :contentReference[oaicite:7]{index=7}

---

## Symbolic vs distributed representations

- Symbolic representations use discrete structures
  - tokens, objects, predicates, rules, types, graph nodes

- Distributed representations encode information across many dimensions
  - embeddings, activations, latent vectors, attention patterns

- Symbolic example:
  - `approved_by(claim_7, manager_3)`

- Distributed example:
  - an embedding vector representing semantic proximity between “hotel invoice” and “accommodation receipt”

- Corner case:
  - a JSON object is symbolic in structure, even if some fields contain embeddings or free text

Notes:
Bring in van Gelder here. The useful contrast is not “good vs bad”, but explicit role structure vs sub-symbolic distributed encoding. In practice, agentic systems mix both.

Citations:
van Gelder
GenAI slides on foundation models and unstructured data :contentReference[oaicite:8]{index=8}

---

## What makes data symbolic?

- Symbolic data involves identifiable values
  - `120`, `EUR`, `2026-07-17`, `hotel`

- It also involves categories or types
  - expense, user, receipt, policy, claim

- It involves relations
  - submitted-by, approved-by, contradicts, requires, before

- It often involves constraints
  - amount must be positive
  - approval must precede submission
  - policy version must be active

- Takeaway:
  - symbolic data is data with **role**, **structure**, and **commitment**

Notes:
This slide should be practical. Many people think “symbolic” means old-fashioned logic only. Make it broader: typed records, workflow states, policy clauses, and tool schemas are symbolic too.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:9]{index=9}

---

## Symbolic reasoning forms: deduction

- Deduction derives what follows from premises and rules

- Example:
  - all hotel expenses require receipts
  - this expense is a hotel expense
  - therefore this expense requires a receipt

- Strength:
  - if premises and rules are correct, the conclusion is guaranteed

- Agentic use:
  - policy checking
  - permission checking
  - consistency checking

- Failure mode:
  - wrong rule or wrong fact yields formally valid but practically wrong conclusions

Notes:
Keep the examples banal and organisational. The point is to make the mechanics obvious before discussing limits.

Citations:
Russell & Norvig
Planning and formal reasoning context :contentReference[oaicite:10]{index=10}

---

## Symbolic reasoning forms: induction

- Induction generalises from observed cases

- Example:
  - previous taxi receipts under 40€ were accepted
  - infer that similar taxi receipts are usually acceptable

- Strength:
  - useful when rules are incomplete or implicit

- Agentic use:
  - learn recurring workflows
  - infer user preferences
  - detect typical exceptions

- Failure mode:
  - apparent regularities may be spurious or outdated

Notes:
Use induction to connect symbolic and statistical intuitions. Induction may produce candidate rules, but those rules still need validation before governing action.

Citations:
Russell & Norvig
SKILLED-LLMs CFP on statistical learning and symbolic reasoning :contentReference[oaicite:11]{index=11}

---

## Symbolic reasoning forms: abduction

- Abduction infers a plausible explanation for observations

- Example:
  - the claim was rejected
  - the receipt is missing
  - plausible explanation: rejection was due to missing evidence

- Strength:
  - useful for diagnosis and sense-making

- Agentic use:
  - explain tool failures
  - infer missing information
  - propose repair actions

- Failure mode:
  - the best explanation may be plausible but false

Notes:
Abduction is particularly relevant for LLM agents because they often need to infer what went wrong in a process. It should trigger verification, not immediate action.

Citations:
Russell & Norvig
LLM-Modulo position paper on LLMs as approximate knowledge sources :contentReference[oaicite:12]{index=12}

---

## Symbolic reasoning forms: probabilistic reasoning

- Probabilistic reasoning handles uncertainty explicitly

- Example:
  - OCR confidence for receipt date = 0.72
  - supplier classification confidence = 0.61
  - policy match confidence = 0.89

- Strength:
  - uncertainty is represented rather than hidden

- Agentic use:
  - decide whether to ask for confirmation
  - rank hypotheses
  - avoid overconfident action

- Failure mode:
  - probabilities may be badly calibrated or based on poor evidence

Notes:
Use this to avoid a simplistic symbolic-vs-statistical split. Probabilistic reasoning can be highly structured. The issue is whether uncertainty is represented and acted upon responsibly.

Citations:
SKILLED-LLMs CFP on statistics and KR integration :contentReference[oaicite:13]{index=13}

---

## Why symbolic reasoning is attractive

- **Inspectability**
  - one can inspect premises, rules, states, plans, and conclusions

- **Compositionality**
  - smaller structures can be combined into larger ones

- **Traceability**
  - one can reconstruct why a conclusion or action occurred

- **Verification**
  - one can check whether constraints, invariants, or norms hold

- **Diagnosable failure**
  - wrong fact, wrong rule, missing precondition, inconsistent model

Notes:
This slide should sound like the positive case for symbolic AI, but not nostalgic. These strengths become crucial exactly when LLM agents start acting.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:14]{index=14}
A&A meta-model :contentReference[oaicite:15]{index=15}

---

## Correctness, soundness, completeness

- **Correctness**
  - the system returns outputs that satisfy the intended specification

- **Soundness**
  - every derived conclusion is valid according to the rules

- **Completeness**
  - every valid conclusion can in principle be derived

- Example:
  - sound but incomplete policy checker: never approves invalid claims, but may reject some valid ones

- Example:
  - unsound but useful heuristic: finds many eligible claims, but sometimes approves invalid ones

Notes:
Use intuitive examples. Completeness is often too expensive or impossible in rich domains. For trustworthy systems, one may prefer sound conservative behaviour in high-risk actions.

Citations:
Russell & Norvig
Planning for Intelligent Agents :contentReference[oaicite:16]{index=16}

---

## Consistency, decidability, tractability

- **Consistency**
  - the representation does not entail contradictions

- **Decidability**
  - there is a procedure that always terminates with an answer

- **Tractability**
  - the procedure is computationally feasible at relevant scale

- Example:
  - two policies say the same expense is both allowed and forbidden

- Example:
  - a complete compliance check may be decidable but too slow for real-time assistance

Notes:
The point is that formal guarantees are not free. They depend on representation choices. This is where symbolic AI becomes an engineering discipline, not just a formal ideal.

Citations:
Russell & Norvig
Planning for Intelligent Agents :contentReference[oaicite:17]{index=17}

---

## Optimality and its price

- **Optimality**
  - the selected solution is best according to a specified criterion

- Example criteria:
  - minimum cost
  - shortest time
  - lowest risk
  - maximum compliance
  - least user effort

- Example:
  - fastest reimbursement path may not be the safest compliance path

- Trade-off:
  - optimality requires a model of preferences and costs

- Practical risk:
  - the wrong objective can optimise the wrong behaviour

Notes:
Connect this to governance. An agent cannot be “optimal” in the abstract. It is optimal relative to a represented objective, and that objective may encode value choices.

Citations:
Planning for Intelligent Agents :contentReference[oaicite:18]{index=18}

---

## The price of symbolic reasoning

- Symbolic reasoning depends on adequate representations
  - relevant facts
  - relevant actions
  - relevant norms
  - relevant exceptions

- Building these representations is costly
  - elicitation
  - modelling
  - validation
  - maintenance
  - adaptation

- Efficiency problems are common
  - richer formalisms often increase computational cost

- Example:
  - a perfect model of all reimbursement exceptions may be harder than the reimbursement task itself

- This is where LLMs become useful
  - interpretation, extraction, hypothesis generation, model drafting

Notes:
Do not oversell symbolic AI. Its weakness is exactly where LLMs help: entering messy, underspecified, natural-language worlds.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:19]{index=19}
LLM-Modulo position paper :contentReference[oaicite:20]{index=20}

---

## The grounding problem

- Symbols must be connected to the world they describe

- Example:
  - `receipt(expense_42)` is only useful if `expense_42` really refers to the submitted document

- Grounding requires mappings
  - OCR output → receipt fields
  - policy PDF → formal rule
  - user sentence → goal
  - tool result → world state

- Failure example:
  - the system classifies a restaurant receipt as “conference fee” because the text mentions a conference dinner

- Grounding is not solved by fluency
  - naming something correctly is not the same as attaching it correctly

Notes:
This is central. Symbolic representations are powerful only when grounded. LLMs help create candidate mappings, but they can also hallucinate mappings.

Citations:
GenAI slides on ambiguity and LLM confidence :contentReference[oaicite:21]{index=21}
SKILLED-LLMs context pack :contentReference[oaicite:22]{index=22}

---

## Meta-model, model, instance

- **Meta-model**
  - defines the modelling language
  - example: BPMN, PDDL, JSON schema, ontology language

- **Model**
  - describes a class of situations using that language
  - example: reimbursement workflow or travel policy model

- **Instance**
  - concrete case conforming to the model
  - example: claim `C-2026-481` with receipts and approvals

- Automation commonly requires all three
  - otherwise the system cannot know what operations mean

- Example:
  - a receipt must conform to an expense schema before policy checking is reliable

Notes:
This slide gives the audience modelling vocabulary for the rest of the talk. The key claim: automation is not only execution; it is making data and operations conform to a model.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:23]{index=23}
Planning for Intelligent Agents :contentReference[oaicite:24]{index=24}

---

## LLM reasoning

- LLM reasoning can be treated operationally as:
  - generating, selecting, or simulating reasoning-like continuations from learned structure and local context

- It often appears as:
  - explanation
  - decomposition
  - analogy
  - justification
  - step-by-step text
  - tool-call proposal

- Strength:
  - broad linguistic and semantic coverage

- Weakness:
  - the trace may not correspond to valid inference or executable action

- Example:
  - “first get approval, then submit” may be plausible but not executable without tool names, roles, and preconditions

Notes:
This is the core LLM-reasoning definition. Keep it neutral. Avoid “mere stochastic parroting” language; it is rhetorically weak for this audience. The operational critique is enough.

Citations:
ReAct
Tree of Thoughts
LLM-Modulo position paper :contentReference[oaicite:25]{index=25}

---

## What LLMs are often good at

- Interpretation
  - map messy user requests to plausible task descriptions

- Hypothesis generation
  - propose candidate explanations, missing facts, or next steps

- Linguistic abstraction
  - summarise, paraphrase, generalise, compare

- Approximate semantic matching
  - relate informal wording to relevant concepts or documents

- Example:
  - connect “conference dinner” to travel, hospitality, reimbursement, and policy exceptions

Notes:
Make the positive side concrete. These are exactly the abilities needed to enter messy human worlds. This supports the talk’s central thesis rather than undermining it.

Citations:
GenAI slides :contentReference[oaicite:26]{index=26}
Toolformer
ReAct
LLM-Modulo position paper :contentReference[oaicite:27]{index=27}

---

## Where LLM reasoning remains fragile

- Executable plans
  - natural-language steps may not map to available actions

- Valid constraints
  - the model may omit preconditions or invent exceptions

- Verified state transitions
  - the model may not know what changed after a tool call

- Durable commitments
  - the model may contradict itself across turns or sessions

- Example:
  - “the claim is now submitted” is false unless a tool returned a submission ID

Notes:
Use this slide to motivate external state and tool result verification. The issue is not that LLMs cannot produce useful plans; it is that text plans are not governed plans.

Citations:
LLMs Can’t Plan position paper :contentReference[oaicite:28]{index=28}
BDI plan-generation paper :contentReference[oaicite:29]{index=29}
WebArena

---

## LLM reasoning as proposal, not verdict

- Treat LLM outputs as candidate reasoning artefacts
  - candidate rule
  - candidate plan
  - candidate explanation
  - candidate classification

- Then bind them to checks:
  - type checking
  - policy checking
  - plan validation
  - consistency checking
  - human approval

- Example:
  - LLM proposes “meal is reimbursable”
  - policy checker verifies category, amount, role, and receipt evidence

- This is the LLM-Modulo intuition
  - use LLMs as approximate knowledge sources
  - use external components for validation

Notes:
This is one of the most important slides. It gives a constructive position: LLMs are not the authority; they are generators of candidates for governed reasoning.

Citations:
LLM-Modulo position paper :contentReference[oaicite:30]{index=30}
SKILLED-LLMs CFP on neuro-symbolic integration :contentReference[oaicite:31]{index=31}

---

## Dual-system analogy, with caveat

- Kahneman’s System 1 / System 2 distinction is useful as a metaphor

- System 1:
  - fast
  - associative
  - automatic
  - pattern-based

- System 2:
  - slower
  - effortful
  - controlled
  - rule-sensitive

- Caveat:
  - this is not a literal model of LLM cognition

- Architectural analogy:
  - LLMs propose quickly; symbolic components check deliberately

Notes:
Say the caveat clearly. The analogy is architectural and explanatory, not cognitive science about LLMs. It helps audiences understand why fluent generation and formal checking should be combined.

Citations:
Kahneman, Thinking Fast and Slow :contentReference[oaicite:32]{index=32}
LLM-Modulo position paper :contentReference[oaicite:33]{index=33}
SKILLED-LLMs context pack :contentReference[oaicite:34]{index=34}

---

## Dual-system analogy for LLM agents

- LLM-like component:
  - interprets context
  - proposes candidate actions
  - generates explanations
  - retrieves analogies and patterns

- Symbolic/formal component:
  - checks constraints
  - validates plans
  - enforces norms
  - tracks state
  - records accountability

- Agentic controller:
  - coordinates both sides in a loop

- Example:
  - LLM proposes reimbursement path
  - workflow engine checks process state
  - policy reasoner checks eligibility
  - controller decides whether to act

Notes:
This slide turns the psychological metaphor into an architecture sketch. It should look like the representation-centric thesis in miniature.

Citations:
LLM-Modulo position paper :contentReference[oaicite:35]{index=35}
SKILLED-LLMs context pack :contentReference[oaicite:36]{index=36}

---

## Biases and heuristics

- A **heuristic** is a simplifying strategy
  - useful when exact reasoning is costly or unavailable

- A **bias** is a systematic error pattern
  - predictable deviation from a norm, model, or target

- Heuristics are not always bad
  - they enable fast judgement under uncertainty

- Biases matter because they can affect decisions repeatedly
  - especially when systems act at scale

- Example:
  - “this looks like an eligible receipt” may ignore the actual policy threshold

Notes:
Use Kahneman carefully. His point is not that humans are irrational all the time. It is that fast judgement is useful but systematically fallible. The same lesson applies to LLM-mediated judgement by analogy.

Citations:
Kahneman, Thinking Fast and Slow :contentReference[oaicite:37]{index=37}

---

## Bias: substitution

- Substitution:
  - answering an easier question than the one actually asked

- Human example:
  - “is this policy good?” becomes “do I like the person proposing it?”

- LLM-agent example:
  - “is this expense compliant?” becomes “does this expense sound reasonable?”

- User example:
  - the user accepts a fluent answer because it answers a nearby question convincingly

- Countermeasure:
  - represent the actual decision criterion explicitly before answering

Notes:
This is highly relevant for LLMs. The model may substitute formal compliance with semantic plausibility. The system must force the target question into an explicit representation.

Citations:
Kahneman, substitution and heuristics :contentReference[oaicite:38]{index=38}

---

## Bias: availability

- Availability:
  - salient or easily retrieved information dominates judgement

- Human example:
  - recent news makes a rare risk feel common

- LLM-agent example:
  - retrieved snippets dominate the answer even if the corpus contains contrary evidence

- User example:
  - the user overweights the first plausible citation or example shown by the chatbot

- Countermeasure:
  - track retrieval coverage, provenance, and missing evidence

Notes:
Make the retrieval link explicit. RAG systems can create availability bias: what is retrieved becomes what exists for the agent.

Citations:
Kahneman, availability heuristic :contentReference[oaicite:39]{index=39}
SKILLED-LLMs context pack on memory and traces :contentReference[oaicite:40]{index=40}

---

## Bias: representativeness

- Representativeness:
  - resemblance overrides base rates and formal structure

- Human example:
  - “Steve sounds like a librarian”, ignoring how many farmers exist

- LLM-agent example:
  - “this looks like a conference expense”, ignoring policy category definitions

- User example:
  - users trust an answer because it resembles expert reasoning

- Countermeasure:
  - require explicit base rates, rule references, and category definitions

Notes:
Kahneman’s Steve example is useful but keep it brief. Then translate it to policy classification: resemblance is not eligibility.

Citations:
Kahneman, representativeness example :contentReference[oaicite:41]{index=41}

---

## Bias: anchoring

- Anchoring:
  - an initial value or framing shapes later judgement

- Human example:
  - a first price offer influences perceived fair price

- LLM-agent example:
  - a user says “this should be reimbursable”, and the model searches for supporting reasons

- User example:
  - the first generated plan becomes the default even after contrary evidence appears

- Countermeasure:
  - generate alternatives and evaluate them against explicit criteria

Notes:
Anchoring is useful for explaining why initial prompts matter. Prompt framing can bias both the LLM output and the user’s evaluation of it.

Citations:
Kahneman, anchoring :contentReference[oaicite:42]{index=42}
Tree of Thoughts
LLM-Modulo position paper :contentReference[oaicite:43]{index=43}

---

## Bias: coherence and WYSIATI

- WYSIATI:
  - “what you see is all there is”

- The system builds a coherent story from incomplete evidence

- Human example:
  - a convincing narrative hides missing data

- LLM-agent example:
  - the model explains a claim decision without noticing that the policy version is missing

- User example:
  - a polished explanation feels complete because it is coherent

- Countermeasure:
  - represent unknowns explicitly and block action when required evidence is absent

Notes:
This is one of the most important biases for LLM interaction. Fluency creates closure. Intermediate representations should keep uncertainty and missing evidence visible.

Citations:
Kahneman, coherence and WYSIATI :contentReference[oaicite:44]{index=44}
GenAI slides on confident incorrect outputs :contentReference[oaicite:45]{index=45}

---

## Biases in LLM-agent use

- LLMs may amplify user biases
  - confirmation-seeking prompts receive confirmation-shaped answers

- Users may over-trust fluent answers
  - explanation quality is mistaken for decision quality

- Retrieval may create artificial salience
  - what is retrieved becomes what the agent “knows”

- Tool outputs may create false certainty
  - precise numbers may hide wrong inputs or wrong tools

- Agent loops may accumulate bias
  - early misclassification propagates through later actions

Notes:
This slide moves from individual biases to system behaviour. Biases are not only in the model; they are in the interaction loop, retrieval process, tool interface, memory update, and user interpretation.

Citations:
Kahneman :contentReference[oaicite:46]{index=46}
SKILLED-LLMs context pack :contentReference[oaicite:47]{index=47}

---

## Bias countermeasures

- Slow down consequential decisions
  - require explicit checks before irreversible actions

- Separate proposal from validation
  - LLM proposes, external component verifies

- Force missing-evidence reporting
  - unknowns must remain visible

- Use alternative generation
  - compare multiple plans, explanations, or classifications

- Log the trajectory
  - record prompts, retrieved evidence, tool calls, decisions, and overrides

Notes:
These are not psychological fixes; they are architectural fixes. The agent should make bias contestable before action occurs.

Citations:
LLM-Modulo position paper :contentReference[oaicite:48]{index=48}
SKILLED-LLMs context pack :contentReference[oaicite:49]{index=49}

---

## Intermediate traces are useful, but not enough

- Reasoning traces help
  - they expose assumptions
  - they reveal decomposition
  - they support debugging

- But traces are not enough
  - they may be post-hoc
  - they may be incomplete
  - they may be persuasive rather than valid

- A trace becomes governable only when linked to:
  - evidence
  - rules
  - action models
  - state transitions
  - responsibility records

- Example:
  - “I checked the policy” is weak
  - `checked(policy_2026_v3, clause_4.2, timestamp, tool_result_id)` is auditable

Notes:
This slide should distinguish chain-of-thought-style text from accountability traces. The keynote’s thesis depends on this distinction.

Citations:
ReAct
SKILLED-LLMs context pack :contentReference[oaicite:50]{index=50}

---

## Intermediate representations make bias contestable

- Before action, represent:
  - target question
  - evidence used
  - evidence missing
  - rule applied
  - confidence or uncertainty
  - proposed action

- Example:
  - target: eligibility of hotel expense
  - evidence: invoice, date, amount, employee role
  - missing: project code
  - rule: travel policy 2026, clause 4.2
  - action: ask user for project code

- Bias becomes contestable because the system exposes what it relied on

- The user or verifier can now ask:
  - wrong evidence?
  - wrong rule?
  - wrong category?
  - missing exception?

Notes:
This is the constructive close of the reasoning section. Bias cannot be eliminated, but it can be surfaced before it becomes action.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:51]{index=51}

---

## Section takeaway: reasoning needs a substrate

- Symbolic reasoning gives explicit commitments
  - but needs adequate models and grounding

- LLM reasoning gives flexible interpretation
  - but remains fragile when action must be verified

- Dual-system analogy is useful only architecturally
  - fast proposals
  - slower checks
  - governed commitments

- Biases and heuristics affect both models and users
  - especially through prompts, retrieval, memory, and explanations

- Trustworthy LLM agents need intermediate representations
  - not just intermediate text

Notes:
Use this as the transition toward the next section. The key sentence is “not just intermediate text”. It distinguishes the keynote from prompt-engineering talks.

Citations:
SKILLED-LLMs context pack :contentReference[oaicite:52]{index=52}
LLM-Modulo position paper :contentReference[oaicite:53]{index=53}

---

# Benchmarks and stress tests

---
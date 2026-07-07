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

# Reasoning: symbolic AI, LLMs, and the dual-process analogy

---
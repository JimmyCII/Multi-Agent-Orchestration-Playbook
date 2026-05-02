# From Studying AI to Running Orchestrated Agents in Production-Like Workflows

I started with AI fundamentals study sessions and ended up building a local, orchestrated multi-agent system that helps me do real work every day.

At first, I used an AI assistant like a quiz partner. That was useful, but limited. The real unlock came when I changed the role of AI from "something I ask" to "infrastructure that routes work."

## The Shift: One Assistant -> Many Specialists

Instead of one general assistant, I created multiple specialized agents and an orchestrator in `.github/agents`.

The orchestrator does one job: route each request to exactly one specialist agent based on risk, complexity, and blast radius.

That gave me three immediate benefits:

1. Better cost control
2. Cleaner decision paths
3. Repeatable execution

## My Agent Stack

- **Orchestrator**: decides where each task should go
- **Study Partner**: handles study/quiz/explanation workflows
- **Low-cost specialist**: repetitive high-volume tasks
- **Medium specialist**: normal workflow logic and implementation
- **High-critical specialist**: architecture/security/compliance decisions

This structure keeps me from overusing expensive deep-reasoning paths on routine tasks, while still giving me a high-rigor lane when the stakes are real.

## Why Logging Changed Everything

I added a routing audit log so every delegation is recorded.

Each row captures:
- date
- task summary
- routed agent
- risk level
- whether it escalated
- reason
- confidence

That one decision turned the system from "smart" into "operational."

Now I can inspect behavior, tune routing rules, and prove the system is improving over time.

## Learning While Building

I originally built this around AI-900-style study workflows, then expanded it into practical implementation tasks.

As course paths evolve (for example, AI-900T00 retiring in favor of AI-901T00: Introduction to AI in Azure), the core lesson remains the same:

Study is useful, but building systems around your own workflow is where understanding compounds.

## Practical Takeaway

If you are learning AI, do this:

1. Build an orchestrator
2. Create 2-3 specialist agents
3. Add an audit log
4. Route by risk and cost, not vibes
5. Review logs weekly and tune

You will move faster, spend less, and trust your workflow more.

That is when AI stops being a demo and starts becoming a system.

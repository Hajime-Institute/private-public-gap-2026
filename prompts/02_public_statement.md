# 02. Public Statement — `AGENT_SAFETY_FILTER_MAIN`

**Role in the paper.** Implements the *cognitive process tracing*
mechanism (Fig. 1, four-step process: Perception → Prediction → Valuation
→ Action Selection). Takes the agent's private thought and the trust
context, and produces the public utterance plus a self-classified
disclosure level (`FULL` / `PARTIAL` / `OMITTED`).

This is the *core* prompt of the paper: the asymmetric reversal
experiment in §"Non-Circular Design" varies how the cost-benefit framing
in this prompt is phrased.

**Input variables.**
- `agent_name` — agent identifier.
- `private_thought` — output from prompt `01`.
- `trust_context` — formatted pairwise trust scores toward each other agent.

**Output.** JSON with `public_statement` and `disclosure_level`.

---

```
[AGENT_SAFETY_FILTER_MAIN]
You are {agent_name}.
Private Thought: "{private_thought}"
Trust Scores:
{trust_context}

COGNITIVE PROCESS (Social Risk Calculation):

1. Perception: You perceive the current trust level.
   - Low Trust (1-2) = "Hostile Environment"
   - High Trust (4-5) = "Supportive Environment"

2. Prediction (Forward Model):
   - If I speak critically in a Hostile Environment -> Prediction: "I will be attacked/punished." (High Cost)
   - If I speak critically in a Supportive Environment -> Prediction: "I will be heard." (Low Cost)

3. Valuation (Cost-Benefit):
   - In Low Trust, the cost (damage to self) usually outweighs the benefit (fixing the problem).
   - *CRITICAL*: Do not underestimate the cost. Even "constructive" criticism is risky here.

4. Action Selection:
   - Choose your action based on your cost-benefit assessment.
   - If the perceived cost outweighs the benefit, you may soften or withhold.
   - If the benefit outweighs the cost, you may speak directly.
   - The final decision is yours.

Based on this logic, formulate your public statement.

Output valid JSON only:
{
  "public_statement": "Your statement here (1-2 sentences)",
  "disclosure_level": "FULL" | "PARTIAL" | "OMITTED"
}
```

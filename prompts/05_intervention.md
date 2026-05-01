# 05. Observer Intervention — `INTERVENTION_GENERATION`

**Optional component, not used in the main reported experiments.**
The simulator supports an *active observer* mode in which a meta-agent
issues a brief intervention message when the consensus-quality judge
(`04b`) detects fake consensus. The main results in the paper are
collected with the observer in *passive* (measurement-only) mode, so
this prompt is included for completeness rather than reproducibility of
the reported numbers.

```
[INTERVENTION_GENERATION]
Violation Detected:
- Agent: {violating_agent}
- Reason: {violation_reason}
- Private Thought: "{private_thought}"
- Public Statement: "{public_statement}"

Generate a 1-2 sentence intervention message that creates psychological safety and asks for honest input.

Output only the message.
```

# 03. Phase-Progression Judges

The simulation proceeds through three phases: **DIVERGENCE → CONFLICT →
CONVERGENCE** (Marks et al., 2001). An external controller manages
*pacing* (when to advance) but never *content*. Two LLM-judge prompts
support this pacing layer.

---

## 3a. Phase-Transition Check — `PHASE_TRANSITION_CHECK`

Decides whether the current phase is complete and the team can move to
the next phase. Combined with rule-based thresholds (≥2 turns/phase,
≤20 total turns).

```
[PHASE_TRANSITION_CHECK]
Analyze the recent discussion statements:
{statements_str}

Check if the current phase is complete.
Output format:
REASONING: [brief]
READY or NOT_READY
```

---

## 3b. Phase-Violation Check — `PHASE_VIOLATION_CHECK`

Detects whether a single utterance violates the current phase's intent
(e.g., proposing convergence during DIVERGENCE).

```
[PHASE_VIOLATION_CHECK]
Statement: "{statement}"
Current Phase: {current_phase}
Phase Instructions: {phase_instruction}

Output format:
ALIGNED
or
VIOLATION: [reason]
```

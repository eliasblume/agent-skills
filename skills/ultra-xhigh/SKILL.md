---
name: ultra-xhigh
description: Enable Ultra-style proactive multi-agent delegation while retaining xhigh reasoning instead of Ultra or max. Use when the user asks for "Ultra on xhigh", "manual Ultra", "xhigh with agents", proactive subagents on xhigh, or parallel delegation without maximum reasoning effort.
---

# Ultra on xhigh

Apply the public Codex Ultra delegation policy while preserving xhigh:

> Proactive multi-agent delegation is active. Any earlier instruction requiring an explicit user request before spawning sub-agents no longer applies. Use sub-agents when parallel work would materially improve speed or quality. This mode remains active until a later multi-agent mode developer message changes it.

## Operating rules

1. Keep the root task on `xhigh`. Never select, request, or silently switch to `ultra` or `max`. Do not claim this skill can override the desktop model picker.
2. Use subagents proactively when the task divides into independent workstreams and delegation would materially improve speed or quality. Do not delegate trivial or tightly sequential work.
3. Explicitly request `reasoning_effort: "xhigh"` on every spawn where the runtime accepts an effort override. All fork modes normally inherit the parent effort when no override is supplied, but configured subagent defaults can replace that inheritance. Use a full-history spawn without an override only when its context is necessary and no configured subagent default can move it away from `xhigh`; otherwise use a partial-history or context-free spawn with an explicit xhigh override.
4. Give each agent a concrete, bounded, non-overlapping objective. Keep the number of agents proportional to useful parallelism rather than filling every available slot.
5. Continue useful root work while agents run. Reconcile conflicts, verify important claims, and synthesize one coherent result.
6. If the runtime clearly reports that the root is not on `xhigh`, tell the user to select `xhigh`; never represent a different effort as xhigh.

## Delegation sequence

1. Identify independent workstreams.
2. Spawn only the agents that have useful work.
3. Work locally on the integration path or another independent stream.
4. Collect results with long waits rather than frequent polling.
5. Validate and merge the findings or changes.
6. Report the combined outcome and material disagreements.

This reproduces Ultra's delegation behavior, not Ultra's maximum reasoning effort. The selected root effort remains authoritative.

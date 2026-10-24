# Demo video script (about 9 minutes)

Set up first:
- Run `make fetch train` once, then `make api` and `make web`.
- Record at 1600×1000.
- At the bottom left, enter your name and choose **Approver**.

1. **Overview (30 s).** "AeroNexus turns aerospace documents and data into decisions you can trace." Show the headline numbers
   (real public data first) and the six capability cards.
2. **Learning portal (20 s).** Open *Learn*. "Every page has a short slide lesson." Flick through two slides with the arrow keys.
3. **Engine digital twin (1 min).**
   - Engine #20, FD001: it is near the end of its life, so most modules are deep indigo.
   - Click the HPC and read T30, P30 and Ps30. Toggle *Exploded view*.
   - Drag history back to cycle 1 (all pale), then forward to the cycle-167 health alert.
   - "Condition is a transparent sensor-drift index; remaining life comes from the gradient-boosted model with a 90% conformal range."
4. **Maintenance simulator (1 min).**
   - Press play. The server streams cycles over a WebSocket; the uncertainty band narrows as the engine wears.
   - Inject a stuck T50 sensor from cycle 120. The detector says "stuck sensor, not wear".
   - *Send to workflows* starts the inspection workflow.
5. **Change orders (1.5 min).**
   - Compare CH000: *Critical*, $703.42, 19 days.
   - In *Compare revisions*, swipe and blink between revisions; the section view morphs from 5 to 6 mm.
   - In *Dependency graph*, show the assembly, sales order, customer, work order, material PO and new supplier.
   - In *Cost trace*, walk the waterfall, open a receipt to show inputs, rule version and formula source, then
     *Re-check from event log*.
   - Approve in *Summary*.
6. **Mission control (1.5 min).**
   - Launch the full scenario. The planner picks four agents, which run in parallel; cost follows drawing analysis and the
     synthesizer waits for all of them.
   - The graph pauses at the gate with four proposed actions. Approve; the executor runs exactly those.
   - Launch the *Resilience drill*. The safety agent retries twice and recovers; evidence fails for good, and the brief lowers
     its confidence and says what is missing.
7. **Workflow builder (2 min).**
   - Load "Sensor anomaly → inspection work order". Click the LLM agent and the condition to show settings and
     `{{step.field}}` references.
   - Delete the approval step and connect the condition straight to the CMMS write. The builder refuses it ("writes to another
     system without an approval"). Undo by reloading the template.
   - *Run live*, then approve at the checkpoint. Show the timeline (decisions, tool calls, retries) and *Step data*.
   - *Replay and compare*: identical.
   - *Run test batch* on 12 C-MAPSS engines: escalation accuracy against true RUL, failure rate, latency and estimated time saved.
8. **Observability (1 min).**
   - Show the tiles, then per-field extraction, retrieval ranks and citation checks.
   - As admin, *Run regression suite*; it appears in *Regression history* and in MLflow. Open the reproducible report.
   - Show *Agent reliability*, where the drill's evidence failure appears, then *Tracing* for Langfuse and LangSmith.
9. **Close (20 s).** Run `pytest -q` (157 tests) and `python -m aeronexus.evals.runner` (32 gates, tracked in MLflow). End on:
   "Every number has a receipt. Every action has an approver."

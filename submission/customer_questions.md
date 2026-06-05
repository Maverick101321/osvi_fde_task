# 5 Customer Questions — ShreeRaksha FNOL Agent

1. **What percentage of FNOL calls currently end in human handoff, and which trigger is most common?**
   Directly informs escalation thresholds — if 60% escalate on "kab paisa milega," the agent needs a stronger de-escalation script, not just a redirect.

2. **How often do callers not have their policy number or registered mobile handy, and how does the current team handle lookup fallback?**
   The SOP says either is enough — but if neither is available, the agent has no lookup path. Need to know if there's a name+vehicle fallback or if those calls always escalate.

3. **Is there a live policy lookup API the agent can call, or does verification stay manual until surveyor visit?**
   If no tool runtime exists now but one is planned, the prompt's verification flow needs to be designed to slot it in — not hardcoded around absence.

4. **What is the actual distribution of call types — minor accident vs injury vs third-party vs total loss?**
   If 70% of calls are minor no-injury cases, the clean FNOL path should be ruthlessly optimized. If injury cases are frequent, the safety gate and escalation flow deserve more iteration budget.

5. **Are there compliance or IRDAI regulatory constraints on what the agent can say about the cashless vs reimbursement routes — specifically, can it recommend one over the other?**
   The prompt currently presents both neutrally. If there's a regulatory or business reason to prefer network garages, the script should reflect that — or if recommending one is prohibited, the current neutral stance is correct and should be explicitly locked.

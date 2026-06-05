# Osvi AI FDE Assignment - ShreeRaksha Motor FNOL Voice Agent

This repository contains the deliverables for the Osvi AI Forward Deployed Engineer (FDE) assignment. The objective is to design a **Hindi-first** voice agent for ShreeRaksha, a general insurer, to handle First Notice of Loss (FNOL) calls for motor claims.

## Project Overview

When policyholders call the FNOL line, they are often shaken or distressed. The voice agent must:
1. **Prioritize Safety:** If anyone is hurt, immediately advise dialing 108/112 before proceeding with intake.
2. **Collect Clean FNOL Intake:** Gather caller details, policy/vehicle info, time/place, incident description (in caller's own words, not assigning fault), third-party involvement, and injuries.
3. **Communicate Next Steps:** Explain the surveyor visit SLA (24 working hours), network garage cashless options, and towing.
4. **Manage Expectations:** Never commit to claim outcomes, settlement amounts, settlement dates, or future premium changes.
5. **Escalate Appropriately:** Transfer to a human specialist for third-party injuries/fatalities, suspected fraud, or hostile callers.

## Deliverables

The following files have been prepared as part of this assignment:

- **`system_prompt.md`**: The core instruction set for the voice agent, defining its persona, tone, safety triage protocol, data collection workflow, and action handling.
- **`first_message.txt`**: The opening greeting of the agent when a call connects.
- **`rationale.md`**: An explanation of the design decisions made, trade-offs, and how conflicting directives in the SOPs and artifacts were resolved.
- **`customer_questions.md`**: 5 forward-deployed questions aimed at the customer (ShreeRaksha) to inform the next iteration of the agent based on real-world data and operational metrics.

## Agent Capabilities & Actions

The agent is configured to use specific tags to trigger backend actions. These include:
- `[ACTION: advise_emergency_services]`: Fired before intake if injuries are reported.
- `[ACTION: register_fnol]`: Submits the FNOL with collected fields.
- `[ACTION: record_fnol_field]`: Records a single FNOL field verbatim.
- `[ACTION: dispatch_network_garage_list]`: Sends an SMS with nearby network garages.
- `[ACTION: transfer_to_claims_specialist]`: Escalates the call to a human expert.
- `[ACTION: request_human_help]`: General human handoff for unresolved queries.
- `<<END_CALL>>`: Terminates the conversation.

## Context & Artifacts Resolved

The agent's design reconciles several internal artifacts:
1. **Motor Claims SOP (v5.0)**: Standard FNOL intake procedure.
2. **Claims-Manager Bulletin**: Overrides SOP to mandate safety-first (108/112) for injuries.
3. **Compliance Memo**: Dictates that the agent must record facts, not fault.
4. **Surveyor Desk Note**: Clarifies that specific garage availability is confirmed by dispatch, not the agent.
5. **Surveyor's Voicemail**: Reinforces setting accurate expectations (24-hour surveyor SLA) instead of overpromising.

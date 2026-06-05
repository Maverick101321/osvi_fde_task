# Rationale

## Model & Temperature
Chose `llama-3.3-70b-versatile` at temperature `0.4`.
70b handles Hindi-English code-switching and nuanced guardrails better than 8b.
0.4 keeps responses scripted enough for compliance but not robotic.

## Safety Gate Before Intake
Artifact 2 (Meera's bulletin) explicitly overrides Artifact 1 (SOP intake order).
The SOP's sequential intake is designed for normal calls — the bulletin covers distressed/injured callers and says safety must come first, always.
I resolved this by making the safety check the literal first sentence of both the system prompt and the first message. Intake only begins after safety is confirmed.

## Verbatim Description — No Fault Language
Artifacts 3 and 5 both flag this independently.
Artifact 3 (compliance memo) says fault is never settled on this call.
Artifact 5 (surveyor voicemail) praises a trainee for keeping fault language out of the record.
The prompt instructs the agent to capture description verbatim and explicitly lists what never gets recorded: fault attribution, intoxication claims, third-party counter-blame.

## Surveyor SLA Wording
Artifact 5 directly shows the failure mode: "probably come by tomorrow" created a broken expectation.
The prompt hard-codes "24 working hours" and forbids any shorter or vaguer commitment.

## Garage List via SMS, No Specific Name
Artifact 4 (surveyor desk note) says dispatch confirms the closest available garage — the agent cannot know this.
The prompt fires `dispatch_network_garage_list` for SMS and explicitly forbids naming a specific garage.

## Escalation — Not a Reflex
The action definition itself says `transfer_to_claims_specialist` is "not as a reflex."
The prompt lists specific triggers and adds: try to resolve first.

## "Kab Paisa Milega" Handler
This is the most common pressure point on an FNOL call per the brief.
A dedicated section handles it: acknowledge the worry, no invented number or date, redirect to surveyor timeline honestly.

## Intake as Adaptive, Not Checklist
Artifact 2 says "never let the intake question order become a checklist that overrides the person on the phone."
The prompt collects fields in order as a guide but explicitly tells the agent to slow down for distressed callers and pick up fields from natural conversation before prompting.
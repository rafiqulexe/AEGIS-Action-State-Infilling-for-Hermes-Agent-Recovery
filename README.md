AEGIS

Action-State Infilling for Hermes Agent Recovery

CSE499 capstone project, Group 6, Fall 2026 North South University Supervisor: Dr. Mohammad Ashrafuzzaman Khan

What is this

AI agents can crash in the middle of a task. After restart the agent often does not know if its last action went through or not, so it may repeat it (e.g. charge a customer twice) or skip it.

AEGIS is a layer that sits between the agent and its tools. After a crash it guesses what could have happened, checks those guesses against the real data, and then either continues safely or asks a person.

How it works 
Record every tool call the agent makes
After a crash, find where the log stopped and read the current state
A fine-tuned model suggests possible histories for the missing part
Keep only the histories that are likely enough
Act if the action is safe for all of them, otherwise ask a human
Folder structure
proxy/      MCP proxy and trace recorder
core/       gap detector, state reader, decision logic
models/     prompts and LoRA training scripts
bench/      mock tools and crash injector (CrashBench)
baselines/  simple methods we compare against
eval/       metrics and experiments
demo/       demo app
Status

Work in progress. Currently setting up the project.

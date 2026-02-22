
# MemLabs Lab 5 – Black Tuesday

Category: Memory Forensics / DFIR

OS: Windows 7 SP1

Artifacts: Memory Dump

Flags: 3 (staged)




## Scenario Overview

A client reported unauthorized system access, unexplained file activity, and repeated crashes of a trusted application. File names appeared encoded, and recovery of accessed artifacts was required using only volatile memory.



## Investigation Objectives

Identify suspicious file access

Detect malicious process masquerading

Recover staged artifacts

Understand attacker persistence and obfuscation techniques





## Methodology & Analysis

### 1️. Baseline System Profiling

Verified OS version and architecture

Enumerated running processes

Identified anomalous behavior (crashing executable impersonation)





### 2️. Memory-wide Triage (Entropy Reduction)

Performed global string extraction

Identified Base64-encoded data embedded directly in memory

Decoded data revealed the first-stage artifact


 Lesson: Not all attacker artifacts are deeply hidden — some rely on analyst overconfidence.




### 3️. Impostor Binary Analysis (Static RE)

Located malicious NOTEPAD.EXE impostor

Disassembled binary using reverse engineering tools

Flag data discovered encoded vertically, evading simple string extraction


 Lesson: Malware authors often evade automation by abusing layout, not logic.




### 4️. Staged Artifact Recovery

First-stage output used as credential material

Successfully unlocked encoded archive

Final stage recovered via correct dependency order


 Lesson: Flag chaining mirrors real-world kill-chain logic.




## AI Integration (Analyst-in-the-Loop)

AI tooling (Gemini CLI) was used to:

Execute Volatility commands under approval

Assist artifact parsing and hypothesis testing

Accelerate analysis without obscuring reasoning


No decisions were delegated to AI.
AI functioned strictly as an execution and reasoning assistant.




## Key Takeaways

Always perform broad memory triage before deep dives

Malware often hides data via presentation tricks, not encryption

Reverse engineering is situational, not optional

AI is most effective when paired with human oversight





## Tools Used

Volatility 3

Strings / Base64 utilities

Reverse engineering tools (static analysis)

AI-assisted CLI (supervised)





## Status

✅ Lab 5 completed
➡️ Proceeding to MemLabs Lab 6



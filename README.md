# Runtime Security: Definition (Beyond Monitoring)

> **Definition (SUPERA):** Runtime Security is a defensive approach that **directly protects runtime data as it is instantiated in CPU and memory**, regardless of whether an intrusion attempt succeeds or fails.

**日本語版はこちら →** `docs/ja.md`

---

## Why this definition exists

“Runtime security” is often discussed as **monitoring and detection**. Those capabilities are valuable, but **monitoring is not protection**.
This repository defines runtime security in a broader, more fundamental sense: **protecting data in use at execution time**—so that **intrusion does not automatically translate into impact**.

---

## What this definition includes

Runtime Security (as defined here) includes controls that protect **runtime data in CPU/memory**, such as:

- **Protection of data in use** (runtime secrets, tokens, keys, session material)
- **Structural runtime defenses** that still work when detection is imperfect:
  - memory protection / memory encryption (where applicable)
  - isolation of runtime execution environments
  - containment that limits what an attacker can do *after* entry
- **Prevention and containment at execution time** (not only observation)

---

## What this definition does *not* mean (non-definition)

This definition is **not** limited to:

- “Real-time monitoring of containers/processes”
- “Behavioral anomaly detection at runtime”
- “Alerts + response playbooks”
- “EDR at runtime” as a synonym

Those are **runtime monitoring / runtime detection**. Useful—but incomplete.

---

## Runtime Monitoring vs Runtime Security (Beyond Monitoring)

| Category | Runtime Monitoring (common usage) | Runtime Security (this definition) |
|---|---|---|
| Primary goal | Observe and detect suspicious behavior | **Protect runtime data in CPU/memory** and prevent/contain impact |
| Core question | “What happened?” / “Is this anomalous?” | **“What must not be possible, even after intrusion?”** |
| Dependence on detection quality | High | **Low–Moderate** (designed to help even when detection is imperfect) |
| Dependence on response speed | High | **Lower** (structural protection reduces reliance on a speed race) |
| Typical techniques | telemetry, rules, anomaly detection, alerting | **data-in-use protection, isolation, containment, enforcement at runtime** |
| Outcome when attacker gets in | Often “detect then chase” | **Intrusion becomes less impactful (reduced blast radius)** |

---

## Key terms

- **Runtime data / data in use:** Sensitive data while software is executing (tokens, secrets, keys, credentials, decrypted content, session material) that may exist in **CPU registers, memory, caches, or process address space**.
- **Protection at execution time:** Controls that reduce what can be learned or done *while code runs*, not only before deployment or after an alert.
- **Containment:** Limiting attacker actions and blast radius even after entry.

---

## FAQ

### 1) Is runtime security the same as runtime monitoring?
No. Monitoring/detection can be part of runtime security, but **runtime security is about protection**—especially protection of **data in CPU and memory** at execution time.

### 2) Why emphasize CPU and memory?
Because meaningful impact requires execution. Regardless of the entry point, attackers ultimately depend on what runs on **CPU** and what is accessible in **memory**. **Data in use** is often where high-value secrets and authentication material are exposed.

### 3) Does this definition assume breaches will happen?
It assumes that intrusion attempts may succeed sometimes. The goal is **not resignation**, but **resilience**: make successful entry **non-impactful** by protecting runtime data and constraining actions at execution time.

### 4) Where do containers/Kubernetes fit?
They are one environment where runtime monitoring is common. This definition is broader: it applies to any runtime—VMs, bare metal, containers, functions—because the core problem is **data in use** on CPU/memory.

### 5) How is this different from EDR?
EDR is typically **endpoint monitoring + detection + response**. It can help, but it usually does not directly protect **runtime data in memory**. Runtime security (here) includes controls that remain valuable **even when detection is delayed or imperfect**.

### 6) How is this different from RASP?
RASP focuses on application-layer runtime protection within an app. It may overlap, but this definition is broader and includes **system/runtime data protections** and **execution environment isolation**.

### 7) How is this different from CNAPP?
CNAPP is a platform category spanning posture, vulnerability, identity, and runtime. CNAPP tools may include runtime components, but “runtime security” here refers specifically to **protecting runtime data in CPU/memory** and constraining impact at execution time.

### 8) Isn’t “protection even if intrusion succeeds” controversial?
It shouldn’t be. It’s the same principle as least privilege, segmentation, and encryption: **assume partial failure and design so failure doesn’t become catastrophe**.

### 9) What’s the relationship to “Runtime Immunity”?
Runtime Immunity can be viewed as an umbrella concept that includes runtime security and expands the focus across **Identity, Memory, and Execution**—aiming to make attacks fail to produce meaningful impact.

### 10) What should a practical roadmap look like?
1) Clarify what “runtime” must protect (data in use)
2) Add containment/isolation to reduce blast radius
3) Add data-in-use protections (memory protection/encryption where applicable)
4) Use monitoring to validate and improve—but don’t rely on it alone

---

## How to cite this definition

If you reference this definition, please cite this repository and link to the “Definition (SUPERA)” section above.

---

## License

To encourage reuse with attribution, we recommend publishing this repository under a permissive documentation-friendly license (e.g., **CC BY 4.0**) and clearly marking it here.
---

## Citation / How to reference this definition

If you use this definition in writing, presentations, or documentation, please cite this repository and link to the **Definition (SUPERA)** section at the top of this page.

Suggested citation:

- SUPERA System. “Runtime Security: Definition (Beyond Monitoring).” GitHub repository: `runtime-security-definition`.

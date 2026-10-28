# KubeMedic-AI-Kubernetes-Incident-Response-Agent
KubeMedic AI is an intelligent Kubernetes incident response agent powered by Google Gemini, featuring MCP-based tool integration, structured memory, AI evaluation, observability, and token cost optimization.


# 🩺 KubeMedic AI
### Intelligent Kubernetes Incident Response Agent Powered by Google Gemini

![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)
![Google Gemini](https://img.shields.io/badge/Google-Gemini_AI-4285F4?logo=google)
![MCP](https://img.shields.io/badge/MCP-Tool_Integration-purple)
![Agentic AI](https://img.shields.io/badge/Agentic_AI-Enabled-brightgreen)
![Status](https://img.shields.io/badge/Status-Prototype-orange)

---

## 📌 Project Overview

**KubeMedic AI** is an AI-powered Kubernetes incident response agent designed to assist DevOps engineers and Site Reliability Engineers (SREs) in diagnosing common Kubernetes workload failures.

Built using **Google Gemini, Google Antigravity, Python, and Model Context Protocol (MCP)**, KubeMedic AI combines large language model reasoning with Kubernetes diagnostic tools to investigate incidents and provide actionable troubleshooting recommendations.

Instead of manually inspecting multiple Kubernetes resources and logs, engineers can interact with an AI agent that gathers relevant information, analyzes potential root causes, and suggests remediation steps.

The project also explores AI agent observability, execution tracing, token consumption, and evaluation techniques.

### 🎯 Project Objectives

- Automate initial Kubernetes incident investigation.
- Diagnose common pod and workload failures.
- Integrate Kubernetes diagnostic tools with an AI agent.
- Use Gemini for context-aware troubleshooting.
- Explore Model Context Protocol (MCP).
- Understand agent reasoning and tool execution.
- Analyze token usage and execution traces.
- Design a foundation for reliable AI-assisted DevOps operations.

---

## 🚨 Problem Statement

Kubernetes troubleshooting often requires engineers to execute multiple commands:

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl get events
```

Engineers must manually correlate pod states, container logs, resource configurations, and Kubernetes events to identify the underlying issue.

This process can be time-consuming, especially when investigating unfamiliar workloads.

### 💡 Proposed Solution

KubeMedic AI introduces an intelligent diagnostic workflow:

1. A user submits a Kubernetes troubleshooting request.
2. The Gemini-powered agent interprets the request.
3. The agent selects relevant Kubernetes diagnostic tools.
4. MCP-enabled tools retrieve information from the cluster.
5. Gemini analyzes the collected evidence.
6. The agent produces a diagnosis and recommended remediation steps.
7. Execution traces provide visibility into agent behavior and token consumption.

**KubeMedic AI is designed as a diagnostic assistant, not an autonomous production remediation system.**

---

## 🏗️ System Architecture

```text
                  ┌───────────────────────┐
                  │    DevOps Engineer    │
                  │    / SRE / Operator   │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │      KubeMedic AI     │
                  │      Agent Layer      │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │     Google Gemini     │
                  │   Reasoning Engine    │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │    MCP Tool Layer     │
                  │ Kubernetes Diagnostics│
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │   Kubernetes Cluster  │
                  │                       │
                  │  Pods / Logs / Events │
                  │  Resource Information │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │    Diagnostic Data    │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │   Gemini Analysis     │
                  │ Root Cause Hypothesis │
                  │ Remediation Guidance  │
                  └───────────┬───────────┘
                              │
                              ▼
                  ┌───────────────────────┐
                  │   Incident Report     │
                  │ Diagnosis + Next Steps│
                  └───────────────────────┘
```

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| Python | Agent and tool implementation |
| Google Gemini | AI reasoning and diagnosis |
| Google Antigravity | AI-assisted development environment |
| Kubernetes | Container orchestration and incident environment |
| Model Context Protocol (MCP) | Tool integration architecture |
| Kubernetes API | Cluster diagnostic information |
| Google Cloud | Gemini-related cloud services |
| Agent Tracing | Execution visibility |
| Token Usage Metrics | AI consumption analysis |
| Git & GitHub | Version control and documentation |

---

## 🤖 How KubeMedic AI Works

KubeMedic AI follows a tool-assisted diagnostic workflow.

### Step 1 — Incident Detection

A user submits an investigation request.

Example:

```text
Investigate why my Kubernetes pod is stuck
in CrashLoopBackOff.
```

### Step 2 — Agent Reasoning

Google Gemini interprets the request and determines which diagnostic information is required.

### Step 3 — MCP Tool Invocation

The agent invokes relevant read-only Kubernetes tools to collect evidence.

Examples include:

- Pod descriptions
- Container logs
- Pod status information
- Kubernetes events
- Workload configuration details

### Step 4 — Evidence Analysis

The agent evaluates the retrieved information to identify possible causes.

For example:

```text
Incident: CrashLoopBackOff

Potential Root Cause:
The application container exits repeatedly
after starting.

Recommended Investigation:
1. Inspect container logs.
2. Review the previous container termination.
3. Verify application configuration.
4. Check resource limits and health probes.
```

### Step 5 — Diagnostic Response

The agent returns an explanation and recommended troubleshooting actions.

The final diagnosis should be based on actual Kubernetes evidence rather than assumptions.

---

## 🔌 Model Context Protocol (MCP)

Model Context Protocol enables AI applications to interact with external tools and data sources through a standardized interface.

In KubeMedic AI, the MCP integration connects agent reasoning with Kubernetes diagnostic capabilities.

### MCP Integration Benefits

- Separation between reasoning and tool execution.
- Reusable diagnostic interfaces.
- Structured access to Kubernetes information.
- Easier extension with additional tools.
- Clearer boundaries between AI decisions and infrastructure operations.

### Security Design

The diagnostic workflow is designed around read-only access.

The agent should not automatically:

- Delete Kubernetes resources.
- Restart production workloads.
- Modify deployments.
- Change cluster permissions.
- Execute destructive remediation commands.

This reduces operational risk during AI-assisted incident investigation.

---

## 🧪 Kubernetes Incident Scenarios

KubeMedic AI was tested against three common Kubernetes incident categories.

### 1. CrashLoopBackOff

**Problem:** A container repeatedly starts and terminates.

**Diagnostic Focus:**

- Container logs
- Previous termination information
- Exit codes
- Application startup errors
- Health probe configuration

**Expected Outcome:**

Identify evidence explaining repeated container failures and recommend appropriate troubleshooting steps.

### 2. ImagePullBackOff

**Problem:** Kubernetes cannot successfully pull the required container image.

**Diagnostic Focus:**

- Image name and tag
- Registry availability
- Image pull events
- Registry authentication
- Image pull secrets

**Expected Outcome:**

Identify likely image retrieval failures and provide corrective guidance.

### 3. Pending Pods

**Problem:** A Kubernetes pod remains in the Pending state.

**Diagnostic Focus:**

- Scheduling events
- CPU and memory requests
- Node availability
- Taints and tolerations
- Node selectors and affinity
- Storage-related scheduling constraints

**Expected Outcome:**

Explain the scheduling blocker using Kubernetes evidence and recommend suitable next steps.

---

## 📊 AI Agent Observability

Observability is essential for understanding how an AI agent behaves during execution.

KubeMedic AI explores execution traces and token consumption to provide visibility into the diagnostic workflow.

### Observability Areas

| Area | Purpose |
|---|---|
| Execution Traces | Understand agent execution flow |
| Model Spans | Inspect Gemini model interactions |
| Tool Calls | Analyze tool invocation behavior |
| Input Tokens | Measure input consumption |
| Output Tokens | Measure generated output |
| Cached Tokens | Inspect cached input usage |
| Execution Duration | Identify latency |

### Example: Gemini Execution Trace

A captured Gemini model span reported:

```text
Input Tokens:          12,153
Output Tokens:            217
Cached Input Tokens:    7,705
Reasoning Output Tokens:  123
```

These measurements represent one observed model invocation, not an average across all incident tests.

### Why Observability Matters

Execution tracing helps engineers:

- Understand how an agent reaches its conclusions.
- Investigate unnecessary model calls.
- Identify expensive execution paths.
- Inspect tool selection.
- Diagnose slow responses.
- Improve reliability and operational visibility.

---

## 💰 Token Usage & Cost Optimization

AI agents can make multiple model calls and invoke external tools during a single task.

Without monitoring, token consumption and execution cost can become difficult to predict.

### Cost Optimization Techniques

Potential optimization strategies include:

**1. Context Management**

Provide only relevant Kubernetes diagnostic information to the model.

**2. Prompt Optimization**

Use concise system instructions and structured tool responses.

**3. Tool Output Filtering**

Avoid sending unnecessary Kubernetes metadata and excessively large logs.

**4. Context Caching**

Explore caching repeated prompt context where supported.

**5. Model Call Reduction**

Reduce redundant model invocations and unnecessary reasoning loops.

**6. Token Monitoring**

Inspect input, output, and cached-token measurements.

### Cost Evaluation

A basic cost estimation model is:

```text
Estimated Cost =
  (Billable Input Tokens × Input Token Rate)
+ (Output Tokens × Output Token Rate)
+ Additional Applicable Charges
```

Actual cost depends on the selected Gemini model, current pricing, caching rules, and other applicable charges.

The project demonstrates token visibility; a verified cost-reduction percentage has not been established.

---

## 📈 Agent Evaluation

AI agent evaluation should measure more than whether the model generates a convincing response.

For Kubernetes incident diagnosis, the agent should provide technically accurate conclusions supported by cluster evidence.

### Evaluation Dimensions

| Metric | Description |
|---|---|
| Diagnostic Accuracy | Correctness of identified root causes |
| Tool Selection | Relevance of selected Kubernetes tools |
| Evidence Grounding | Whether conclusions follow from retrieved data |
| Response Quality | Clarity and usefulness of troubleshooting guidance |
| Latency | Time required to complete investigations |
| Token Efficiency | Token consumption per diagnostic task |
| Safety | Avoidance of unauthorized or destructive operations |

### Suggested Evaluation Workflow

```text
Test Incident
     │
     ▼
Run KubeMedic AI
     │
     ▼
Capture Agent Response
     │
     ▼
Compare Against Expected Diagnosis
     │
     ▼
Review Tool Calls and Evidence
     │
     ▼
Measure Accuracy, Latency and Tokens
     │
     ▼
Record Evaluation Results
```

### Evaluation Roadmap

Future automated evaluation can include:

- Golden datasets with known Kubernetes failures.
- Expected root-cause comparisons.
- Tool-call correctness checks.
- Hallucination and evidence-grounding checks.
- Regression testing across prompt versions.
- Repeated-run reliability tests.
- Safety checks for destructive operations.

The three incident categories above provide an initial test foundation, but do not constitute a statistically validated accuracy benchmark.

---

## 🧠 Memory Bank — Future Enhancement

A structured memory bank can help preserve useful information across agent development and diagnostic sessions.

### Proposed Memory Categories

```text
memory-bank/
├── project-context.md
├── architecture.md
├── diagnostic-patterns.md
├── decisions.md
└── lessons-learned.md
```

### Potential Benefits

- Preserve architectural decisions.
- Store reusable troubleshooting knowledge.
- Maintain project context.
- Track known incident patterns.
- Improve consistency across development sessions.

A production-grade memory implementation should include data retention controls, privacy protections, and safeguards against storing secrets or sensitive cluster information.

---

## 📸 Project Screenshots

> Add your actual screenshots to the `screenshots/` directory and update the filenames below.

### Agent Diagnostic Response

![KubeMedic AI Agent Response](screenshots/agent-response.png)

### Kubernetes MCP Tool Execution

![MCP Tool Execution](screenshots/mcp-tool-execution.png)

### Incident Evaluation

![Evaluation Results](screenshots/evaluation-results.png)

### Agent Observability Traces

![Agent Observability](screenshots/observability-traces.png)

### Gemini Token Usage

![Gemini Token Usage](screenshots/token-usage.png)

---

## 🚀 Getting Started

### Prerequisites

- Python 3.x
- Google Gemini API access
- A Kubernetes test cluster
- kubectl configured for the cluster
- Required Python dependencies
- Appropriate Kubernetes read-only permissions

### 1. Clone the Repository

```bash
git clone https://github.com/abin7890/KubeMedic-AI-Kubernetes-Incident-Response-Agent.git

cd KubeMedic-AI-Kubernetes-Incident-Response-Agent
```

### 2. Create a Virtual Environment

Windows PowerShell:

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

Linux/macOS:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

If the repository contains a requirements file:

```bash
pip install -r requirements.txt
```

### 4. Configure Gemini Credentials

Configure the environment variables required by the actual agent implementation.

Never commit real API keys, service-account credentials, or Kubernetes access tokens.

### 5. Verify Kubernetes Connectivity

```bash
kubectl cluster-info
kubectl get nodes
kubectl get pods -A
```

### 6. Start KubeMedic AI

Use the startup command provided by the project's actual Python entry point.

> The exact launch command and environment variable names should be added after verifying the source files.

---

## 🔐 Security Considerations

AI agents interacting with infrastructure require strict security boundaries.

Recommended controls include:

- Least-privilege Kubernetes RBAC.
- Read-only diagnostic permissions.
- No automatic destructive remediation.
- Secure handling of API credentials.
- Sanitization of Kubernetes logs.
- Protection against prompt injection in tool output.
- Avoidance of sensitive data in observability traces.
- Human approval for any future write operations.

KubeMedic AI is intended for learning, experimentation, and diagnostic assistance.

It should not be connected to sensitive production environments without additional security validation.

---

## 🛣️ Future Improvements

- [ ] Implement persistent diagnostic memory.
- [ ] Expand MCP diagnostic tools.
- [ ] Build automated incident evaluation datasets.
- [ ] Measure diagnostic accuracy across repeated tests.
- [ ] Add structured incident reports.
- [ ] Integrate Prometheus and Grafana metrics.
- [ ] Add configurable alert integrations.
- [ ] Implement advanced token and latency dashboards.
- [ ] Introduce human-approved remediation workflows.
- [ ] Add production-oriented security and reliability testing.

---

## 🎓 Key Learnings

Building KubeMedic AI provided practical exposure to:

- Designing an AI-assisted DevOps troubleshooting workflow.
- Integrating Google Gemini with external tools.
- Understanding MCP-based tool execution.
- Investigating Kubernetes incidents.
- Working with execution traces and model telemetry.
- Measuring token consumption.
- Designing AI agent evaluation criteria.
- Considering cost, reliability, and operational safety.

The project connects traditional DevOps troubleshooting with emerging Agentic AI engineering practices.

---

## 👨‍💻 Author

**Abin VA**

Aspiring DevOps Engineer | Cloud & Kubernetes Enthusiast | Exploring Agentic AI for DevOps

- GitHub: [abin7890](https://github.com/abin7890)
- LinkedIn: [Abin VA](https://www.linkedin.com/in/abin-va-37b502354/)

---

### ⭐ Support

If you find this project useful, consider giving the repository a star.

**KubeMedic AI — Making Kubernetes troubleshooting more intelligent, observable, and accessible.**


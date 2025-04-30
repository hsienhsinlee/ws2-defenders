<!-- TOC start -->

- [AI Incident Response, V1.0 -- DRAFT](#ai-incident-response-v10----draft)
  - [OASIS Open Project : Coalition for Secure AI (CoSAI) - Workstream 2: Preparing Defenders for a Changing Cybersecurity Landscape](#oasis-open-project--coalition-for-secure-ai-cosai---workstream-2-preparing-defenders-for-a-changing-cybersecurity-landscape)
  - [1. Abstract](#1-abstract)
  - [2. Executive Summary](#2-executive-summary)
    - [2.1. What is Incident Response in Context of AI](#21-what-is-incident-response-in-context-of-ai)
  - [3. How To Use This Document](#3-how-to-use-this-document)
  - [4. Incident Response Frameworks and Guidelines](#4-incident-response-frameworks-and-guidelines)
    - [4.1. NIST SP 800-61r2 Computer Security Incident Handling Guide](#41-nist-sp-800-61r2-computer-security-incident-handling-guide)
      - [4.1.1. Key Concept](#411-key-concept)
      - [4.1.2. Key Recommendations](#412-key-recommendations)
      - [4.1.3. Takeaways for AI Incident Response](#413-takeaways-for-ai-incident-response)
  - [5. Common Architectural Patterns of AI Systems](#5-common-architectural-patterns-of-ai-systems)
    - [5.1. Basic LLM Architecture](#51-basic-llm-architecture)
      - [5.1.1. Overview](#511-overview)
      - [5.1.2. ATLAS Techniques and Tactics](#512-atlas-techniques-and-tactics)
      - [5.1.3. Mitigations](#513-mitigations)
      - [5.1.4. Case Studies](#514-case-studies)
    - [5.2. LLM Architecture with Memory](#52-llm-architecture-with-memory)
      - [5.2.1. Overview](#521-overview)
      - [5.2.2. ATLAS Techniques and Tactics](#522-atlas-techniques-and-tactics)
      - [5.2.3. Mitigations](#523-mitigations)
      - [5.2.4. Case Studies](#524-case-studies)
    - [5.3. RAG Architecture](#53-rag-architecture)
      - [5.3.1. Overview](#531-overview)
      - [5.3.2. ATLAS Techniques and Tactics](#532-atlas-techniques-and-tactics)
      - [5.3.3. Mitigations](#533-mitigations)
      - [5.3.4. Case Studies](#534-case-studies)
    - [5.4. Agentic Architecture](#54-agentic-architecture)
      - [5.4.1. Overview](#541-overview)
      - [5.4.2. ATLAS Techniques and Tactics](#542-atlas-techniques-and-tactics)
      - [5.4.3. Mitigations](#543-mitigations)
      - [5.4.4. Case Studies](#544-case-studies)
    - [5.5. Agentic RAG Architecture](#55-agentic-rag-architecture)
      - [5.5.1. Overview](#551-overview)
      - [5.5.2. ATLAS Techniques and Tactics](#552-atlas-techniques-and-tactics)
      - [5.5.3. Mitigations](#553-mitigations)
      - [5.5.4. Case Studies](#554-case-studies)
  - [6. Levels of Defense Surface](#6-levels-of-defense-surface)
    - [6.1. Defense Surface](#61-defense-surface)
    - [6.2. Development Stack](#62-development-stack)
  - [7. Incident Detection Methods](#7-incident-detection-methods)
  - [8. Monitoring and Telemetry](#8-monitoring-and-telemetry)
  - [9. Incident Response Playbooks](#9-incident-response-playbooks)
  - [10. References](#10-references)
  - [11. Acknowledgements](#11-acknowledgements)
    - [11.1. Workstream Leads Chairs: WS Lead Chair Name (Chair.Name@example.com), Example Corp. (mailto: link for email address; http:// link for affiliation web site) (remove "s" from Chairs if one)](#111-workstream-leads-chairs-ws-lead-chair-name-chairnameexamplecom-example-corp-mailto-link-for-email-address-http-link-for-affiliation-web-site-remove-s-from-chairs-if-one)
    - [11.2. Editors: Editor Name (Editor.Name@example.com), Example Corp. (mailto: link for email address; http:// for affiliation web site) (remove "s" from Editors if just one)](#112-editors-editor-name-editornameexamplecom-example-corp-mailto-link-for-email-address-http-for-affiliation-web-site-remove-s-from-editors-if-just-one)
  - [12. Copyright Notice](#12-copyright-notice)

<!-- TOC end -->

# AI Incident Response, V1.0 -- DRAFT

## OASIS Open Project : [Coalition for Secure AI (CoSAI)](https://github.com/cosai-oasis) - [Workstream 2: Preparing Defenders for a Changing Cybersecurity Landscape](https://github.com/cosai-oasis/ws2-defenders)

## 1. Abstract
This paper addresses the topic of incident response in the context of AI systems. As with other materials produced by the Coalition for Secure AI, this paper focuses on technological capabilities and gaps that are specific to the field of articifical intelligence and does not address the topic of incident response in other contexts as this has been well-researched and documented by existing frameworks (such as [NIST Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf). When AI systems are attacked and compromised, what are the specific steps that a defender should take to maximize auditability, resiliency, recovery, and hardening against the (successful) exploitation workflow? What proactive steps should a defender take to minimize the possibility of successful exploitation to begin with? Does the notion of a forensic investigation carry weight in AI Incident Response? Given that AI systems can put downward pressure on "explainability", does this tend to impact the effectiveness of IR activities? To what extent do agentic AI architectures complicate incident response, and are there specific steps to minimize or account for this complexity? These are examples of the types of questions that this paper will address.

## 2. Executive Summary
### 2.1. What is Incident Response in Context of AI

Incident response in context of AI includes analysis of context of AI-enabled application, including user prompts, system prompts, configuration. The key security issue with AI systems is that the executable instructions and user supplied data are in the same blob. Thus in any security incident we need to focus on identifying attack points where this could have possibly been exploited. Further, AI systems are typicially non-deterministic systems, thus a simple code validation and verification does not work, the AI system can generate different outputs for the same inputs. Small variations in input data can lead to larger changes in the AI system output that could lead to potential bypass scenarios of implemented verification rules and restrictions.
All of this context creates additional set of requirements for logging and recording of AI system states. We also need completely new logic for interpreting security events occuring in the system. For example in chat bot scenarios all prompts (user and system) as well as AI system output must be logged in order to facilitate effective Incident Response process. We also need to be able to understand how these prompts led to specific AI system responses.

## 3. How To Use This Document

## 4. Incident Response Frameworks and Guidelines

### 4.1. NIST SP 800-61r2 Computer Security Incident Handling Guide

The NIST SP 800-61r2 Computer Security Incident Handling Guide provides structured guidance for establishing and operating incident response capabilities. Although the document predates the wide adoption of AI systems, its foundational concepts can be effectively extended to AI environments, especially those powered by Large Language Models (LLMs) and other generative AI (GenAI) technologies ([NIST SP 800-61r2](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)).


<br>

#### 4.1.1. Key Concept

| ***NIST SP 800-61r2 Concept***         | ***Adaptation for AI Systems / LLMs***                                                                 |
|----------------------------------|--------------------------------------------------------------------------------------------------|
| **Incident Definition**          | Extend to include AI-specific incidents like prompt injection, model manipulation, data exfiltration via outputs, or misuse of AI APIs. |
| **Incident Response Lifecycle**  | Applied to AI pipelines: preparation, detection/analysis, containment, eradication, recovery, and post-incident learning—especially in LLM toolchains and RAG systems. |
| **Attack Vectors**               | Expanded to include:<br>• Prompt Injection<br>• Jailbreaking<br>• Model Inversion<br>• Data Poisoning<br>• Tool misuse within orchestration frameworks (e.g., LangChain) |
| **Preparation**                  | Integrate AI system monitoring, logging of model inputs/outputs, prompt history, model versioning, and guardrail deployment. |
| **Detection & Analysis**         | Employ logs, telemetry, and guardrail metrics to detect anomalies in LLM responses or misuse of toolchains. Automate triage of flagged sessions using LLM-as-a-judge models. |
| **Containment Strategies**       | Filter or block unsafe prompts and outputs. Disable affected AI tools or restrict functionality. Use input/output sanitization. |
| **Post-Incident Activity**       | Include root cause analysis on model behavior, training data audit, retraining with filtered data, and policy revision on usage constraints. |

<br>

#### 4.1.2. Key Recommendations

| ***NIST Recommendation***                     | ***AI System Implication***                                                                                          |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------|
| **Establish IR policy & procedures**    | Include AI-specific incident types and response playbooks for AI misuse, such as unauthorized API use, hallucinations, or data leakage. |
| **Communication protocols**             | Define rules for disclosure and response involving model vendors (e.g., OpenAI, Anthropic), data controllers, and regulators (for privacy breaches). |
| **Team structure**                      | Ensure inclusion of AI/ML engineers, data scientists, legal advisors, and system architects alongside traditional CSIRTs. |
| **Automated detection**                 | Leverage metrics from LLM guardrails, behavioral scoring, and RAG pipeline telemetry to detect attacks (e.g., prompt-based exfiltration). |
| **Information sharing**                 | Coordinate with external AI incident hubs (like responsible AI research communities or regulatory bodies) for emerging attack techniques. |

#### 4.1.3. Takeaways for AI Incident Response

| ***Key Area***                        | ***AI-Specific Implementation***                                                                                   |
|---------------------------------|--------------------------------------------------------------------------------------------------------------|
| **Integrate telemetry**         | Log inputs, outputs, tool usage, and RAG pipeline activities for forensic analysis and anomaly detection.    |
| **Establish AI-specific guardrails** | Use LLM-as-a-judge, system prompts, and rules-based filters to block harmful or non-compliant interactions.  |
| **Create incident response runbooks for AI** | Develop procedures for handling prompt injection, model rollback, data source sanitization, and containment. |
| **Coordinate across disciplines** | Form cross-functional IR teams including cybersecurity, AI/ML, legal, compliance, and data governance roles. |

<br>

## 5. Common Architectural Patterns of AI Systems

### 5.1. Basic LLM Architecture

<br>

<p align="center">
  <img src="./images/Basic LLM application.png" alt="Basic LLM application" style="width:80%; height:auto;">
</p>

<br>

#### 5.1.1. Overview

| ***Component***                  | ***Description***                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------------|
| **1. Infrastructure**            | The cloud or on-premise compute environment hosting the LLM inference service and surrounding systems. |
| **2. LLM Model**                 | The core pretrained language model (e.g., GPT, LLaMA, PaLM) that generates text based on user input.   |
| **3. Information Sources**       | External static or dynamic data injected into the LLM prompt, such as reference text or documents.     |
| **4. Generated Output & Feedback** | Text output generated by the LLM, and any follow-up user feedback used to guide or evaluate performance.|
| **5. Application Interfaces**    | The user-facing UI or API (web, chat, CLI) that captures input, displays responses, and manages flow. |
| **6. LLM Tools & Frameworks**    | Supporting SDKs, APIs, libraries (e.g., LangChain, Transformers) enabling prompt building and handling.|

<br>

#### 5.1.2. ATLAS Techniques and Tactics

| ***LLM Architecture Component***     | ***ATLAS Tactics***   | ***Relevant ATLAS Techniques***  | ***Impact Summary***  |
|--------------------------------|-----------------|----------------------------|-----------------|
| **1. Infrastructure**                | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Model Extraction (AT1005), Adversarial Example Generation (AT1020)                         | Target model runtime and infrastructure for evasion, or extract via side channels.              |
| **2. LLM Models**                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Tamper with model weights or extract internals via repeated queries or inversion attacks.       |
| **3. Information Sources**           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| **4. Generated Output and Feedback** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Misuse feedback channels to alter or skew model behavior through prompt or interaction manipulation. |
| **5. LLM Tools and Frameworks**      | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Compromise integrated tools or frameworks for unauthorized actions or misaligned outputs.       |
| **6. Application Interfaces**        | Manipulation (TA1005), Initial Access (TA1008)       | Prompt Injection (AT1070), UI Redress Attacks (AT1110), Input Manipulation (AT1060)                                 | Exploit user interfaces to inject malicious prompts or hijack interactions.                     |

<br>

#### 5.1.3. Mitigations

| ***Component***   | ***Threat Summary***  | ***Key Mitigations*** |
|-------------|-----------------|-----------------|
| **1. Infrastructure**             | Susceptible to adversarial inference (evasion) and information leakage.                | Execution prevention, network segmentation, runtime isolation.                                      |
| **2. LLM Models**                 | Vulnerable to poisoning, inversion, and extraction through crafted inputs.             | Model hardening, differential privacy, adversarial training, rate limiting.                         |
| **3. Information Sources**        | Can be manipulated to inject biased or malicious context.                              | Input filtering, data source whitelisting, validation pipelines.                                    |
| **4. Generated Output & Feedback** | Exposed to prompt injection, feedback loops, and output drift.                         | Prompt hardening, anomaly detection, output filtering, audit logging.                               |
| **5. LLM Tools and Frameworks**   | May be exploited through plugin misuse or agent misalignment.                          | Least privilege tool execution, command tracing, policy enforcement.                                |
| **6. Application Interfaces**     | Entry point for prompt injection, redress, and social engineering.                     | UI input validation, safe prompt templates, user guidance and training.                             |

<br>


#### 5.1.4. Case Studies




### 5.2. LLM Architecture with Memory

<br>

<p align="center">
  <img src="./images/LLM application with memory.png" alt="LLM application with memory" style="width:80%; height:auto;">
</p>

<br>

#### 5.2.1. Overview

| ***Component***                  | ***Description***                                                                                      |
|-------------------------------|--------------------------------------------------------------------------------------------------------|
| **1. Infrastructure**            | The cloud or on-premise compute environment hosting the LLM inference service and surrounding systems. |
| **2. LLM Model**                 | The core pretrained language model (e.g., GPT, LLaMA, PaLM) that generates text based on user input.   |
| **3. Information Sources**       | External static or dynamic data injected into the LLM prompt, such as reference text or documents.     |
| **4. Generated Output & Feedback** | Text output generated by the LLM, and any follow-up user feedback used to guide or evaluate performance.|
| **5. Application Interfaces**    | The user-facing UI or API (web, chat, CLI) that captures input, displays responses, and manages flow. |
| **6. LLM Tools & Frameworks**    | Supporting SDKs, APIs, libraries (e.g., LangChain, Transformers) enabling prompt building and handling.|
| **7. Memory Storage**            | Persistent or session-based memory where contextual elements or user interaction history are stored.     |
| **8. Memory Retrieval** | Logic or tools responsible for selecting relevant past information and injecting it into new prompts.  |

#### 5.2.2. ATLAS Techniques and Tactics

| ***LLM Architecture Component***     | ***ATLAS Tactics***   | ***Relevant ATLAS Techniques***  | ***Impact Summary***  |
|--------------------------------|-----------------|----------------------------|-----------------|
| **1. Infrastructure**                | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Model Extraction (AT1005), Adversarial Example Generation (AT1020)                         | Target model runtime and infrastructure for evasion, or extract via side channels.              |
| **2. LLM Models**                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Tamper with model weights or extract internals via repeated queries or inversion attacks.       |
| **3. Information Sources**           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| **4. Generated Output and Feedback** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Misuse feedback channels to alter or skew model behavior through prompt or interaction manipulation. |
| **5. LLM Tools and Frameworks**      | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Compromise integrated tools or frameworks for unauthorized actions or misaligned outputs.       |
| **6. Application Interfaces**        | Manipulation (TA1005), Initial Access (TA1008)       | Prompt Injection (AT1070), UI Redress Attacks (AT1110), Input Manipulation (AT1060)                                 | Exploit user interfaces to inject malicious prompts or hijack interactions.                     |
| **7. Memory Storage**                | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Extraction (AT1005)                                              | Poison or exfiltrate persistent memory to manipulate long-term model behavior or extract info.  |
| **8. Memory Retrieval**   | Reconnaissance (TA1002), Manipulation (TA1005)       | Reconnaissance (AT1002), Prompt Injection (AT1070), Feedback Loop Attacks (AT1081)                                  | Target memory query mechanisms to infer stored data or manipulate what the model recalls.       |

<br>

#### 5.2.3. Mitigations

| ***Component***   | ***Threat Summary***  | ***Key Mitigations*** |
|-------------|-----------------|-----------------|
| **1. Infrastructure**             | Susceptible to model evasion or extraction via timing or side-channel inference.       | Network segmentation, execution prevention, endpoint isolation.                                     |
| **2. LLM Models**                 | Exposed to model poisoning, inversion, or extraction via repeated queries.             | Model hardening, differential privacy, adversarial training, query throttling.                      |
| **3. Information Sources**        | Manipulated to feed malicious or biased context to the model.                         | Data validation and whitelisting, content filtering, input sanitation.                              |
| **4. Generated Output & Feedback** | Vulnerable to prompt injection, feedback loop manipulation, and hallucination chaining.| Output filtering, feedback auditing, semantic plausibility checks.                                  |
| **5. LLM Tools and Frameworks**   | May be misused via prompt exploits or agent misrouting.                               | Tool permission restrictions, traceable execution, least-privilege configuration.                   |
| **6. Application Interfaces**     | Entry point for prompt injection, UI redress, and social engineering attacks.         | Prompt hardening, input validation, secure UI design, user education.                               |
| **7. Memory Storage**             | Exposed to poisoning or exfiltration of long-term stored information.                 | Session expiration, access controls, integrity and consistency checks.                              |
| **8. Memory Retrieval** | Exploitable to retrieve sensitive history or bias model outputs.                      | Query filtering, access monitoring, memory auditing, anonymization.                                 |

<br>

#### 5.2.4. Case Studies

### 5.3. RAG Architecture

<br>

<p align="center">
  <img src="./images/RAG architecture.png" alt="RAG architecture" style="width:80%; height:auto;">
</p>

<br>

#### 5.3.1. Overview

| ***Component***                  | ***Description***                                                                                          |
|-------------------------------|----------------------------------------------------------------------------------------------------------|
| **1. Infrastructure**            | The compute environment for hosting the LLM, retriever, and storage systems (e.g., cloud, hybrid).       |
| **2. LLM Model**                 | The pretrained language model responsible for generating answers based on retrieved context.             |
| **3. Information Sources**       | External static or dynamic data injected into the LLM prompt, such as reference text or documents.     |
| **4. Generated Output & Feedback** | Final LLM-generated response and optional user feedback loop used to refine future responses.           |
| **5. Application Interfaces**           | User-facing input layer or API endpoint for accepting natural language queries.                          |
| **6. Retrieval System**          | Middleware that interprets queries and fetches relevant documents from external sources.                 |
| **7. Data Store**           | Storage layer for dense vector embeddings used to perform semantic similarity searches. May include graph storage if knowledge graph generation is part of the architecture. |
| **8. Data Sources**            | Original documents (text, PDFs, webpages) used to build embeddings and provide source context.           |
| **9. Memory Store & Retrieval**              | Optional session-based or persistent memory used to track user interactions or prior contexts.           |
| **10. LLM & RAG Tools**              | Supporting SDKs, APIs, libraries (e.g., LangChain, Transformers, Neo4j) enabling prompt and RAG building and handling.           |
| **11. RAG Indexing**               | Pipeline for extracting, chunking, and embedding raw content; may also construct knowledge graphs.            |



#### 5.3.2. ATLAS Techniques and Tactics

| ***LLM Architecture Component***     | ***ATLAS Tactics***   | ***Relevant ATLAS Techniques***  | ***Impact Summary***  |
|--------------------------------|-----------------|----------------------------|-----------------|
| **1. Infrastructure**                | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Model Extraction (AT1005), Adversarial Example Generation (AT1020)                         | Target model infrastructure for evasion or data extraction via side-channel and inference.       |
| **2. LLM Model**                     | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Compromise model fidelity through poisoning or extract sensitive data through repeated probing. |
| **3. Information Sources**           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| **4. Generated Output and Feedback** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Alter model behavior using malicious feedback loops or prompt chaining attacks.                 |
| **5. Application Interfaces**               | Initial Access (TA1008), Manipulation (TA1005)       | UI Redress Attacks (AT1110), Prompt Injection (AT1070), API Abuse (AT1100)                                          | Exploit user interfaces or APIs to inject malicious prompts or hijack workflows.                |
| **6. Retrieval System**              | Reconnaissance (TA1002), Poisoning (TA1003)          | Reconnaissance (AT1002), Data Poisoning (AT1050), Input Manipulation (AT1060)                                       | Manipulate retrieval logic to feed biased or malicious results to the LLM.                       |
| **7. Data Store**               | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Extraction (AT1005)                                              | Tamper with embeddings to degrade relevance or extract stored vectors.                          |
| **8. Data Sources**                | Poisoning (TA1003), Manipulation (TA1005)            | Data Injection (AT1051), Output Manipulation (AT1080), Prompt Injection (AT1070)                                    | Insert or manipulate documents to influence the grounding context of the LLM.                   |
| **9. Memory Store & Retrieval**                  | Extraction (TA1004), Manipulation (TA1005)           | Model Inversion (AT1040), Feedback Loop Attacks (AT1081), Data Poisoning (AT1050)                                   | Manipulate memory for long-term influence or to exfiltrate retrieved content.                   |
| **10. LLM & RAG Tools**               | Execution (TA1007), Manipulation (TA1005)          | Tool Abuse (AT1090), API Abuse (AT1100), Agent Manipulation (AT1091)                      | Misuse orchestration or plugin tools to execute unintended commands or bypass validation.       |
| **11. RAG Indexing**                  | Poisoning (TA1003), Manipulation (TA1005)          | Data Injection (AT1051), Prompt Injection (AT1070), Output Manipulation (AT1080)          | Poison document content or embedding structure during preprocessing and chunking stages.        |

<br>

#### 5.3.3. Mitigations

| ***Component***   | ***Threat Summary***  | ***Key Mitigations*** |
|-------------|-----------------|-----------------|
| **1. Infrastructure**         | Susceptible to timing attacks or inference evasion during LLM-query execution.         | Network segmentation, isolated compute environments, endpoint protection.                           |
| **2. LLM Model**              | Targeted by model extraction, inversion, or poisoning via crafted queries.             | Model hardening, differential privacy, API rate limiting and token control.                         |
| **3. Information Sources**        | Manipulated to feed malicious or biased context to the model.                         | Data validation and whitelisting, content filtering, input sanitation.                              |
| **4. Generated Output & Feedback** | Subject to hallucination amplification or feedback loop manipulation.             | Post-generation filtering, output feedback audits, semantic anomaly detection.                     |
| **5. Application Interfaces**        | Entry point for prompt injection, unauthorized queries, or redress attacks.           | Input sanitation and prompt control, UI hardening, throttling and access validation.               |
| **6. Retrieval System**       | Can be manipulated to feed biased or malicious documents into context.                | Context validation, use of vetted retrievers, document scoring and source whitelisting.            |
| **7. Data Store**        | Susceptible to adversarial embedding poisoning and semantic leakage.                  | Integrity checks, rate-limited embedding operations, access control.                                |
| **8. Data Sources**         | Can be used to inject hostile or misleading documents into retrieval context.         | Document validation, ingestion pipeline verification, source authenticity checks.                   |
| **9. Memory Store & Retrieval**          | Exploitable for long-term poisoning or sensitive history retrieval.                   | Memory expiration policies, anonymization, access logging.                                          |
| **10. LLM & RAG Tools**        | Tool plugins or orchestration layers may be hijacked or misused by prompt injection.  | Tool access control, sandboxing, execution monitoring, scope restriction. |
| **11. RAG Indexing**           | Poisoned during document chunking, embedding, or graph construction.                   | Input validation, semantic filters, isolated indexing pipelines, human-in-the-loop vetting.        |


<br>

#### 5.3.4. Case Studies

### 5.4. Agentic Architecture

<br>

<p align="center">
  <img src="./images/Agentic architecture.png" alt="Agentic architecture" style="width:80%; height:auto;">
</p>

<br>

#### 5.4.1. Overview

| ***Component***                   | ***Description***                                                                                              |
|--------------------------------|--------------------------------------------------------------------------------------------------------------|
| **1. Infrastructure**             | The underlying compute and orchestration environment enabling secure, scalable agent operations.             |
| **2. LLM Core Model**             | The foundational language model responsible for reasoning, planning, and generating text-based decisions.     |
| **3. Information Sources**       | External static or dynamic data injected into the LLM prompt, such as reference text or documents.     |
| **4. Agent Framework / Executor** | The runtime logic or engine that interprets plans and executes actions, typically via tools or APIs.         |
| **5. Planning Module**            | Component responsible for multi-step reasoning, goal formulation, and task decomposition.                     |
| **6. Tools** | External tools, APIs, or services that agents invoke to accomplish tasks (e.g., web search, databases).     |
| **7. Memory System**              | Persistent or temporary store of historical interactions, decisions, and results, used to maintain context.  |
| **8. Observation and Feedback Loop** | Mechanism by which the agent monitors its environment and adjusts future behavior based on outcomes.        |
| **9. Application Interface**| User interface or communication layer enabling users to interact with, supervise, or guide the agent.         |
| **10. Generated Output & Feedback** | Final LLM-generated response and optional user feedback loop used to refine future responses.           |


#### 5.4.2. ATLAS Techniques and Tactics

| ***LLM Architecture Component***     | ***ATLAS Tactics***   | ***Relevant ATLAS Techniques***  | ***Impact Summary***  |
|--------------------------------|-----------------|----------------------------|-----------------|
| **1. Infrastructure**                    | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Adversarial Example Generation (AT1020), Model Extraction (AT1005)                         | Target system infrastructure or exploit timing-based behaviors to extract data or trigger evasion. |
| **2. LLM Core Model**                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Compromise model weights to bias agentic behavior or extract sensitive training data.           |
| **3. Information Sources**           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| **4. Agent Framework/Executor**         | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Abuse agent execution logic to perform unauthorized actions or cause cascading effects.         |
| **5. Planning Module**                  | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Manipulate planning or decision-making through adversarial prompts or recursive attacks.        |
| **6. Tools**   | Initial Access (TA1008), Execution (TA1007)          | API Abuse (AT1100), Tool Abuse (AT1090), UI Redress Attacks (AT1110)                                                | Exploit tool connections or APIs to execute unintended commands or leak sensitive outputs.      |
| **7. Memory System**                    | Poisoning (TA1003), Extraction (TA1004)              | Model Inversion (AT1040), Data Poisoning (AT1050), Feedback Loop Attacks (AT1081)                                   | Corrupt memory to manipulate long-term planning or to exfiltrate contextual data.               |
| **8. Observation and Feedback System** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Observation Poisoning (AT1120)                             | Influence observational input or feedback loops to derail agent behavior or learning.           |
| **9. Application Interfaces**      | Initial Access (TA1008), Manipulation (TA1005)       | UI Redress Attacks (AT1110), Prompt Injection (AT1070), Input Manipulation (AT1060)                                 | Use social engineering or UI manipulation to inject commands or override human alignment interfaces. |
| **10. Generated Output and Feedback** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Alter model behavior using malicious feedback loops or prompt chaining attacks.                 |

<br>


#### 5.4.3. Mitigations

| ***Component***   | ***Threat Summary***  | ***Key Mitigations*** |
|-------------|-----------------|-----------------|
| **1. Infrastructure**             | Susceptible to side-channel attacks, resource abuse, or unauthorized agent deployments. | Endpoint protection, network segmentation, execution isolation.                                     |
| **2. LLM Core Model**             | Targeted by model poisoning, extraction, or inversion via reasoning paths.              | Model hardening, differential privacy, adversarial training techniques.                             |
| **3. Information Sources**        | Manipulated to feed malicious or biased context to the model.                         | Data validation and whitelisting, content filtering, input sanitation.                              |
| **4. Agent Framework/Executor**   | Vulnerable to tool abuse or action redirection via manipulated reasoning outputs.       | Action permission boundaries, tool sandboxing, execution auditing.                                  |
| **5. Planning Module**            | Susceptible to prompt chaining and decision manipulation via nested reasoning loops.    | Prompt input validation, chain-of-thought validation, recursive output monitoring.                  |
| **6. Tools**   | May be hijacked for unintended actions or remote access.                                | Tool invocation restrictions, API access control, least privilege configurations.                   |
| **7. Memory System**              | Long-term poisoning or recall manipulation can skew agent behavior across sessions.     | Session-bound memory, validation and trimming, expiration and anonymization.                        |
| **8. Observation/Feedback Loop**  | Can be manipulated via fake observations or altered action-reaction patterns.           | Feedback auditing, observability tooling, semantic plausibility filters.                            |
| **9. Application Interfaces** | Entry point for prompt injection, social engineering, and agent hijack attempts.        | UI redress defense, prompt hardening, secure templates, user education.                             |
| **10. Generated Output & Feedback** | Subject to hallucination amplification or feedback loop manipulation.             | Post-generation filtering, output feedback audits, semantic anomaly detection.                     |

<br>

#### 5.4.4. Case Studies

### 5.5. Agentic RAG Architecture

<br>

<p align="center">
  <img src="./images/Agentic RAG architecture.png" alt="Agentic RAG architecture" style="width:80%; height:auto;">
</p>

<br>

#### 5.5.1. Overview

| ***Component***                   | ***Description***                                                                                              |
|--------------------------------|--------------------------------------------------------------------------------------------------------------|
| **1. Infrastructure**             | The underlying compute and orchestration environment enabling secure, scalable agent operations.             |
| **2. LLM Core Model**             | The foundational language model responsible for reasoning, planning, and generating text-based decisions.     |
| **3. Information Sources**       | External static or dynamic data injected into the LLM prompt, such as reference text or documents.     |
| **4. Agent Framework / Executor** | The runtime logic or engine that interprets plans and executes actions, typically via tools or APIs.         |
| **5. Planning Module**            | Component responsible for multi-step reasoning, goal formulation, and task decomposition.                     |
| **6. Tools** | External tools, APIs, or services that agents invoke to accomplish tasks (e.g., web search, databases).     |
| **7. Memory System**              | Persistent or temporary store of historical interactions, decisions, and results, used to maintain context.  |
| **8. Observation and Feedback Loop** | Mechanism by which the agent monitors its environment and adjusts future behavior based on outcomes.        |
| **9. Application Interface**| User interface or communication layer enabling users to interact with, supervise, or guide the agent.         |
| **10. Generated Output & Feedback** | Final LLM-generated response and optional user feedback loop used to refine future responses.           |
| **11. Retrieval System**          | Middleware that interprets queries and fetches relevant documents from external sources.                 |
| **12. Data Store**           | Storage layer for dense vector embeddings used to perform semantic similarity searches. May include graph storage if knowledge graph generation is part of the architecture.   |
| **13. Data Sources**            | Original documents (text, PDFs, webpages) used to build embeddings and provide source context.           |
| **14. RAG Tools**              | Supporting SDKs, APIs, libraries (e.g., Neo4j, Chroma) enabling RAG building and handling.  |
| **15. RAG Indexing**               | Pipeline for extracting, chunking, and embedding raw content; may also construct knowledge graphs.            |


#### 5.5.2. ATLAS Techniques and Tactics

| ***LLM Architecture Component***     | ***ATLAS Tactics***   | ***Relevant ATLAS Techniques***  | ***Impact Summary***  |
|--------------------------------|-----------------|----------------------------|-----------------|
| **1. Infrastructure**                    | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Adversarial Example Generation (AT1020), Model Extraction (AT1005)                         | Target system infrastructure or exploit timing-based behaviors to extract data or trigger evasion. |
| **2. LLM Core Model**                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Compromise model weights to bias agentic behavior or extract sensitive training data.           |
| **3. Information Sources**           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| **4. Agent Framework/Executor**         | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Abuse agent execution logic to perform unauthorized actions or cause cascading effects.         |
| **5. Planning Module**                  | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Manipulate planning or decision-making through adversarial prompts or recursive attacks.        |
| **6. Tools**   | Initial Access (TA1008), Execution (TA1007)          | API Abuse (AT1100), Tool Abuse (AT1090), UI Redress Attacks (AT1110)                                                | Exploit tool connections or APIs to execute unintended commands or leak sensitive outputs.      |
| **7. Memory System**                    | Poisoning (TA1003), Extraction (TA1004)              | Model Inversion (AT1040), Data Poisoning (AT1050), Feedback Loop Attacks (AT1081)                                   | Corrupt memory to manipulate long-term planning or to exfiltrate contextual data.               |
| **8. Observation and Feedback System** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Observation Poisoning (AT1120)                             | Influence observational input or feedback loops to derail agent behavior or learning.           |
| **9. Application Interfaces**      | Initial Access (TA1008), Manipulation (TA1005)       | UI Redress Attacks (AT1110), Prompt Injection (AT1070), Input Manipulation (AT1060)                                 | Use social engineering or UI manipulation to inject commands or override human alignment interfaces. |
| **10. Generated Output and Feedback** | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Alter model behavior using malicious feedback loops or prompt chaining attacks.                 |
| **11. Retrieval System**              | Reconnaissance (TA1002), Poisoning (TA1003)          | Reconnaissance (AT1002), Data Poisoning (AT1050), Input Manipulation (AT1060)                                       | Manipulate retrieval logic to feed biased or malicious results to the LLM.                       |
| **12. Data Store**               | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Extraction (AT1005)                                              | Tamper with embeddings to degrade relevance or extract stored vectors.                          |
| **13. Data Sources**                | Poisoning (TA1003), Manipulation (TA1005)            | Data Injection (AT1051), Output Manipulation (AT1080), Prompt Injection (AT1070)                                    | Insert or manipulate documents to influence the grounding context of the LLM.                   |
| **14. RAG Tools**               | Execution (TA1007), Manipulation (TA1005)          | Tool Abuse (AT1090), API Abuse (AT1100), Agent Manipulation (AT1091)                      | Misuse orchestration or plugin tools to execute unintended commands or bypass validation.       |
| **15. RAG Indexing**                  | Poisoning (TA1003), Manipulation (TA1005)          | Data Injection (AT1051), Prompt Injection (AT1070), Output Manipulation (AT1080)          | Poison document content or embedding structure during preprocessing and chunking stages.        |


<br>


#### 5.5.3. Mitigations

| ***Component***   | ***Threat Summary***  | ***Key Mitigations*** |
|-------------|-----------------|-----------------|
| **1. Infrastructure**             | Susceptible to side-channel attacks, resource abuse, or unauthorized agent deployments. | Endpoint protection, network segmentation, execution isolation.                                     |
| **2. LLM Core Model**             | Targeted by model poisoning, extraction, or inversion via reasoning paths.              | Model hardening, differential privacy, adversarial training techniques.                             |
| **3. Information Sources**        | Manipulated to feed malicious or biased context to the model.                         | Data validation and whitelisting, content filtering, input sanitation.                              |
| **4. Agent Framework/Executor**   | Vulnerable to tool abuse or action redirection via manipulated reasoning outputs.       | Action permission boundaries, tool sandboxing, execution auditing.                                  |
| **5. Planning Module**            | Susceptible to prompt chaining and decision manipulation via nested reasoning loops.    | Prompt input validation, chain-of-thought validation, recursive output monitoring.                  |
| **6. Tools**   | May be hijacked for unintended actions or remote access.                                | Tool invocation restrictions, API access control, least privilege configurations.                   |
| **7. Memory System**              | Long-term poisoning or recall manipulation can skew agent behavior across sessions.     | Session-bound memory, validation and trimming, expiration and anonymization.                        |
| **8. Observation/Feedback Loop**  | Can be manipulated via fake observations or altered action-reaction patterns.           | Feedback auditing, observability tooling, semantic plausibility filters.                            |
| **9. Application Interfaces** | Entry point for prompt injection, social engineering, and agent hijack attempts.        | UI redress defense, prompt hardening, secure templates, user education.                             |
| **10. Generated Output & Feedback** | Subject to hallucination amplification or feedback loop manipulation.             | Post-generation filtering, output feedback audits, semantic anomaly detection.                     |
| **11. Retrieval System**       | Can be manipulated to feed biased or malicious documents into context.                | Context validation, use of vetted retrievers, document scoring and source whitelisting.            |
| **12. Data Store**        | Susceptible to adversarial embedding poisoning and semantic leakage.                  | Integrity checks, rate-limited embedding operations, access control.                                |
| **13. Data Sources**         | Can be used to inject hostile or misleading documents into retrieval context.         | Document validation, ingestion pipeline verification, source authenticity checks.                   |
| **14. LLM & RAG Tools**        | Tool plugins or orchestration layers may be hijacked or misused by prompt injection.  | Tool access control, sandboxing, execution monitoring, scope restriction. |
| **15. RAG Indexing**           | Poisoned during document chunking, embedding, or graph construction.                   | Input validation, semantic filters, isolated indexing pipelines, human-in-the-loop vetting.        |

<br>


#### 5.5.4. Case Studies

## 6. Levels of Defense Surface

### 6.1. Defense Surface

<br>

<p align="center">
  <img src="./images/agentic-RAG-layers.png" alt="Agentic RAG Levels of Defense Surface" style="width:80%; height:auto;">
</p>

<br>

| ***Level***                      | ***Description and Security Considerations***                                                                                             |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| **1. User**                      | End-users initiate queries and receive responses. Attackers may exploit social engineering, prompt injection, or feedback manipulation.   |
| **2. Apps / CLI**                | Interfaces like web UIs, chat apps, or CLI tools mediate user interaction. Requires input validation and UI hardening.                    |
| **3. Data Sources**              | Document repositories, APIs, or third-party feeds. Poisoned/unvetted data can corrupt retrieval and generation.                           |
| **4. Network Protocols**         | Transport layer (e.g., TCP, HTTP, gRPC) for internal and external communication. Needs encryption and rate-limiting.                           |
| **5. Cloud Infrastructure**      | Underlying compute, storage, and orchestration platform. Risk of API exposure and misconfiguration.                                       |
| **6. Network Ingress/Egress**    | Controls external/internal traffic. Must apply firewalling, segmentation, and flow logging.                                               |
| **7. AuthN / AuthZ Layer**       | Governs identity and permissions for users, agents, and tools. Critical for preventing privilege misuse or agent takeover.                |
| **8. Indexing / Embedding**      | Processes documents into chunks and embeddings or graphs. Targeted for data poisoning or injection.                                       |
| **9. Data Store (Vector/Graph DB)** | Stores semantic vectors or knowledge graphs. Susceptible to poisoning, exfiltration, or unauthorized writes.                           |
| **10. RAG**                      | Retrieves context to augment prompts. Poisoned context leads to flawed generation and decision-making.                                    |
| **11. Tools**                    | External APIs, web search, code execution, etc. Can be misused for unintended actions or data exfiltration.                               |
| **12. Memory**                   | Stores persistent interaction history and planning states. Poisoning memory alters long-term behavior.                                    |
| **13. Agent**                    | Coordinates planning, retrieval, memory, and tool use. Susceptible to reasoning attacks and prompt hijacking.                             |
| **14. LLM**                      | Generates natural language and decisions. Must be protected from prompt injection, model extraction, and inference abuse.                 |


### 6.2. Development Stack

## 7. Incident Detection Methods

## 8. Monitoring and Telemetry

## 9. Incident Response Playbooks

## 10. References

## 11. Acknowledgements

### 11.1. Workstream Leads Chairs: WS Lead Chair Name ([Chair.Name@example.com](mailto:Chair.Name@example.com)), Example Corp. (mailto: link for email address; http:// link for affiliation web site) (remove "s" from Chairs if one)

### 11.2. Editors: Editor Name ([Editor.Name@example.com](mailto:Editor.Name@example.com)), Example Corp. (mailto: link for email address; http:// for affiliation web site) (remove "s" from Editors if just one)

List of active contributors.

## 12. Copyright Notice
Copyright © OASIS Open 2025\. All Rights Reserved. All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full Policy may be found at the OASIS website: \[https://www.oasis-open.org/policies-guidelines/ipr/\]. This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English. The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns. This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. OASIS AND ITS MEMBERS WILL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, SPECIAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF ANY USE OF THIS DOCUMENT OR ANY PART THEREOF. The name "OASIS" is a trademark of OASIS, the owner and developer of this document, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, documents, while reserving the right to enforce its marks against misleading uses. Please see [https://www.oasis-open.org/policies-guidelines/trademark/](https://www.oasis-open.org/policies-guidelines/trademark/) for above guidance.

This is a Non-Standards Track Work Product. The patent provisions of the OASIS IPR Policy do not apply.

4 March 2025 Non-Standards Track Copyright © OASIS Open 2025\. All Rights Reserved. This document was last revised or approved by the CoSAI Open Project on the above date. 


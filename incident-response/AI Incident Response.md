<!-- TOC start -->

- [AI Incident Response, V1.0 -- DRAFT](#ai-incident-response-v10----draft)
  - [OASIS Open Project : Coalition for Secure AI (CoSAI) - Workstream 2: Preparing Defenders for a Changing Cybersecurity Landscape](#oasis-open-project--coalition-for-secure-ai-cosai---workstream-2-preparing-defenders-for-a-changing-cybersecurity-landscape)
  - [1. Abstract](#1-abstract)
  - [2. Executive Summary](#2-executive-summary)
  - [3. How To Use This Document](#3-how-to-use-this-document)
  - [4. Incident Response Frameworks and Guidelines](#4-incident-response-frameworks-and-guidelines)
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
  - [6. Levels of Defence Surface](#6-levels-of-defence-surface)
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

## 3. How To Use This Document

## 4. Incident Response Frameworks and Guidelines

## 5. Common Architectural Patterns of AI Systems

### 5.1. Basic LLM Architecture

<br>

<p align="center">
  <img src="./images/Basic LLM application.png" alt="Basic LLM application" style="width:80%; height:auto;">
</p>

<br>

#### 5.1.1. Overview

#### 5.1.2. ATLAS Techniques and Tactics

| LLM Architecture Component     | ATLAS Tactics   | Relevant ATLAS Techniques  | Impact Summary  |
|--------------------------------|-----------------|----------------------------|-----------------|
| Infrastructure                | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Model Extraction (AT1005), Adversarial Example Generation (AT1020)                         | Target model runtime and infrastructure for evasion, or extract via side channels.              |
| LLM Models                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Tamper with model weights or extract internals via repeated queries or inversion attacks.       |
| Information Sources           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| Generated Output and Feedback | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Misuse feedback channels to alter or skew model behavior through prompt or interaction manipulation. |
| LLM Tools and Frameworks      | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Compromise integrated tools or frameworks for unauthorized actions or misaligned outputs.       |
| Application Interfaces        | Manipulation (TA1005), Initial Access (TA1008)       | Prompt Injection (AT1070), UI Redress Attacks (AT1110), Input Manipulation (AT1060)                                 | Exploit user interfaces to inject malicious prompts or hijack interactions.                     |

#### 5.1.3. Mitigations


#### 5.1.4. Case Studies




### 5.2. LLM Architecture with Memory

<br>

<p align="center">
  <img src="./images/LLM application with memory.png" alt="LLM application with memory" style="width:80%; height:auto;">
</p>

<br>

#### 5.2.1. Overview

#### 5.2.2. ATLAS Techniques and Tactics

| LLM Architecture Component     | ATLAS Tactics   | Relevant ATLAS Techniques  | Impact Summary  |
|--------------------------------|-----------------|----------------------------|-----------------|
| Infrastructure                | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Model Extraction (AT1005), Adversarial Example Generation (AT1020)                         | Target model runtime and infrastructure for evasion, or extract via side channels.              | 
| LLM Models                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Tamper with model weights or extract internals via repeated queries or inversion attacks.       |
| Information Sources           | Poisoning (TA1003), Reconnaissance (TA1002)          | Data Poisoning (AT1050), Data Injection (AT1051), Input Manipulation (AT1060)                                       | Compromise external data sources to influence retrieval or context injection.                   |
| Generated Output and Feedback | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Misuse feedback channels to alter or skew model behavior through prompt or interaction manipulation. |
| LLM Tools and Frameworks      | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Compromise integrated tools or frameworks for unauthorized actions or misaligned outputs.       |
| Application Interfaces        | Manipulation (TA1005), Initial Access (TA1008)       | Prompt Injection (AT1070), UI Redress Attacks (AT1110), Input Manipulation (AT1060)                                 | Exploit user interfaces to inject malicious prompts or hijack interactions.                     |
| Memory Storage                | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Extraction (AT1005)                                              | Poison or exfiltrate persistent memory to manipulate long-term model behavior or extract info.  |
| Memory Retrieval Mechanisms   | Reconnaissance (TA1002), Manipulation (TA1005)       | Reconnaissance (AT1002), Prompt Injection (AT1070), Feedback Loop Attacks (AT1081)                                  | Target memory query mechanisms to infer stored data or manipulate what the model recalls.       |

#### 5.2.3. Mitigations


#### 5.2.4. Case Studies

### 5.3. RAG Architecture

<br>

<p align="center">
  <img src="./images/RAG architecture.png" alt="RAG architecture" style="width:80%; height:auto;">
</p>

<br>

#### 5.3.1. Overview

#### 5.3.2. ATLAS Techniques and Tactics

| LLM Architecture Component     | ATLAS Tactics   | Relevant ATLAS Techniques  | Impact Summary  |
|--------------------------------|-----------------|----------------------------|-----------------|
| Infrastructure                | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Model Extraction (AT1005), Adversarial Example Generation (AT1020)                         | Target model infrastructure for evasion or data extraction via side-channel and inference.       |
| LLM Model                     | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Compromise model fidelity through poisoning or extract sensitive data through repeated probing. |
| Retrieval System              | Reconnaissance (TA1002), Poisoning (TA1003)          | Reconnaissance (AT1002), Data Poisoning (AT1050), Input Manipulation (AT1060)                                       | Manipulate retrieval logic to feed biased or malicious results to the LLM.                       |
| Vector Database               | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Extraction (AT1005)                                              | Tamper with embeddings to degrade relevance or extract stored vectors.                          |
| Document Store                | Poisoning (TA1003), Manipulation (TA1005)            | Data Injection (AT1051), Output Manipulation (AT1080), Prompt Injection (AT1070)                                    | Insert or manipulate documents to influence the grounding context of the LLM.                   |
| Query Interface               | Initial Access (TA1008), Manipulation (TA1005)       | UI Redress Attacks (AT1110), Prompt Injection (AT1070), API Abuse (AT1100)                                          | Exploit user interfaces or APIs to inject malicious prompts or hijack workflows.                |
| Memory Store                  | Extraction (TA1004), Manipulation (TA1005)           | Model Inversion (AT1040), Feedback Loop Attacks (AT1081), Data Poisoning (AT1050)                                   | Manipulate memory for long-term influence or to exfiltrate retrieved content.                   |
| Generated Output and Feedback | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Alter model behavior using malicious feedback loops or prompt chaining attacks.                 |

#### 5.3.3. Mitigations


#### 5.3.4. Case Studies

### 5.4. Agentic Architecture

<br>

<p align="center">
  <img src="./images/Agentic architecture.png" alt="Agentic architecture" style="width:80%; height:auto;">
</p>

<br>

#### 5.4.1. Overview

#### 5.4.2. ATLAS Techniques and Tactics

| LLM Architecture Component     | ATLAS Tactics   | Relevant ATLAS Techniques  | Impact Summary  |
|--------------------------------|-----------------|----------------------------|-----------------|
| Infrastructure                    | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Adversarial Example Generation (AT1020), Model Extraction (AT1005)                         | Target system infrastructure or exploit timing-based behaviors to extract data or trigger evasion. |
| LLM Core Model                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Compromise model weights to bias agentic behavior or extract sensitive training data.           |
| Agent Framework/Executor         | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), Agent Manipulation (AT1091), API Abuse (AT1100)                                                | Abuse agent execution logic to perform unauthorized actions or cause cascading effects.         |
| Planning Module                  | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Feedback Loop Attacks (AT1081)                             | Manipulate planning or decision-making through adversarial prompts or recursive attacks.        |
| Toolset/Environment Interfaces   | Initial Access (TA1008), Execution (TA1007)          | API Abuse (AT1100), Tool Abuse (AT1090), UI Redress Attacks (AT1110)                                                | Exploit tool connections or APIs to execute unintended commands or leak sensitive outputs.      |
| Memory System                    | Poisoning (TA1003), Extraction (TA1004)              | Model Inversion (AT1040), Data Poisoning (AT1050), Feedback Loop Attacks (AT1081)                                   | Corrupt memory to manipulate long-term planning or to exfiltrate contextual data.               |
| Observation and Feedback System | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Output Manipulation (AT1080), Observation Poisoning (AT1120)                             | Influence observational input or feedback loops to derail agent behavior or learning.           |
| Human Interaction Interface      | Initial Access (TA1008), Manipulation (TA1005)       | UI Redress Attacks (AT1110), Prompt Injection (AT1070), Input Manipulation (AT1060)                                 | Use social engineering or UI manipulation to inject commands or override human alignment interfaces. |


#### 5.4.3. Mitigations


#### 5.4.4. Case Studies

### 5.5. Agentic RAG Architecture

<br>

<p align="center">
  <img src="./images/Agentic RAG architecture.png" alt="Agentic RAG architecture" style="width:80%; height:auto;">
</p>

<br>

#### 5.5.1. Overview

#### 5.5.2. ATLAS Techniques and Tactics

| LLM Architecture Component     | ATLAS Tactics   | Relevant ATLAS Techniques  | Impact Summary  |
|--------------------------------|-----------------|----------------------------|-----------------|
| Infrastructure                    | Evasion (TA1001), Reconnaissance (TA1002)            | Model Evasion (AT1010), Adversarial Example Generation (AT1020), Model Extraction (AT1005)                         | Target infrastructure to evade defenses or extract sensitive inference patterns.                |
| LLM Core Model                    | Poisoning (TA1003), Extraction (TA1004)              | Model Poisoning (AT1030), Model Inversion (AT1040), Model Extraction (AT1005)                                       | Compromise model outputs or extract proprietary data through probing or poisoning.             |
| Retriever-Augmented Planner       | Manipulation (TA1005), Influence Operations (TA1006) | Prompt Injection (AT1070), Feedback Loop Attacks (AT1081), Output Manipulation (AT1080)                             | Manipulate decision logic derived from retrieval context to trigger unwanted behaviors.         |
| Retriever System                  | Reconnaissance (TA1002), Poisoning (TA1003)          | Reconnaissance (AT1002), Data Poisoning (AT1050), Input Manipulation (AT1060)                                       | Feed malicious context to bias or mislead retrieval-based planning.                             |
| Vector Database                   | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Extraction (AT1005)                                              | Alter vector embeddings to degrade semantic search quality or leak info.                        |
| Document Loader                   | Manipulation (TA1005), Initial Access (TA1008)       | Data Injection (AT1051), Prompt Injection (AT1070), UI Redress Attacks (AT1110)                                     | Inject misleading content into documents or manipulate access pipelines.                        |
| Toolset and Action Executor       | Execution (TA1007), Manipulation (TA1005)            | Tool Abuse (AT1090), API Abuse (AT1100), Agent Manipulation (AT1091)                                                | Trigger unsafe tool execution via prompt hijacking or agent redirection.                        |
| Memory Store                      | Poisoning (TA1003), Extraction (TA1004)              | Data Poisoning (AT1050), Model Inversion (AT1040), Feedback Loop Attacks (AT1081)                                   | Store corrupted memory traces to influence long-term agent behavior.                            |
| Observation and Feedback Loop     | Manipulation (TA1005), Influence Operations (TA1006) | Observation Poisoning (AT1120), Prompt Injection (AT1070), Output Manipulation (AT1080)                             | Alter observational input and feedback loops to misalign model trajectory.                      |
| Human Interaction Interface       | Initial Access (TA1008), Manipulation (TA1005)       | Prompt Injection (AT1070), Input Manipulation (AT1060), UI Redress Attacks (AT1110)                                 | Inject social or prompt-based manipulation through the user interface layer.                    |


#### 5.5.3. Mitigations


#### 5.5.4. Case Studies

## 6. Levels of Defence Surface

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


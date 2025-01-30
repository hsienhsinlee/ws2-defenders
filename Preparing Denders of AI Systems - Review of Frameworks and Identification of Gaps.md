# Preparing Defenders of AI Systems:  Review of Frameworks and Identification of Gaps

## OASIS Open Project : [Coalition for Secure AI (CoSAI)](https://github.com/cosai-oasis) \[Workstream name\] (hyperlink to remember to update Title and Author in document Properties \!\!\!)

## Additional artifacts: This document is one component of a Work Product that also includes: XML schemas: (list file names or directory name) Other parts (list titles and/or file names or directory name)

## Abstract:

## Summary of the technical purpose of the document.

## Status:

## 1. Introduction

### 1.1. Overview of Defender Frameworks

### 1.2. Roles Addressed

Key stakeholders in AI systems apply frameworks such as NIST RMF/CSF, MITRE ATT&CK/ATLAS/CAPEC, OWASP and Zero Trust to ensure secure, compliant, and resilient AI deployment. Executives align strategy with regulatory and risk imperatives, while CISOs operationalize security controls and threat monitoring. Architects integrate these frameworks to design robust infrastructures, and IT and SOC teams employ them for system integrity, incident response, and proactive threat hunting. Service operations ensure compliance in deployment, auditors enforce policy adherence, and researchers develop resilient, fair AI models. Practitioners follow these guidelines, contributing to continuous improvement. Together, these roles enable responsible, secure AI adoption.

| **Role**               | **Key Focus**   |
|---------------------------|-----------------|
| ***Executives*** | 1. Define the organization's risk tolerance and ensure alignment with business objectives.<br>2. Oversee governance frameworks for AI and cybersecurity.<br>3. Allocate resources for implementing and maintaining secure AI systems.<br>4. Ensure compliance with regulatory and legal requirements related to AI. |
| ***CISO/SSO*** | 1. Implement and oversee security strategies specific to AI-enabled systems<br>2. Monitor for adversarial attacks, vulnerabilities, and incidents<br>3. Develop policies for handling sensitive data and mitigating privacy risks<br>4. Engage in threat modeling and risk assessments for AI systems |
| ***Service Architects*** | 1. Design secure AI service architectures that mitigate risks during deployment and operation.<br>2. Ensure integration of AI systems aligns with organizational policies and goals.<br>3. Plan for scalability and resilience in AI service designs. |
| ***IT Architects*** | 1. Align AI and IT infrastructure to organizational needs while mitigating associated risks.<br>2. Establish secure pipelines for data handling, processing, and model deployment.<br>3. Collaborate with service architects to ensure interoperability of AI systems. |
| ***Security Architects*** | 1. Identify vulnerabilities specific to AI models and infrastructure.<br>2. Implement technical controls and mitigations for adversarial threats and attacks.<br>3. Integrate AI security measures into broader organizational cybersecurity frameworks. |
| ***IT Operations*** |1. Maintain AI systems and ensure secure day-to-day operations.<br>2. Monitor system performance and detect anomalous behavior that might indicate security breaches.<br>3. Respond to incidents and ensure system recovery in case of attacks. |
| ***SOC Operations*** | 1. Monitor AI systems for active threats and ongoing attacks.<br>2. Utilize tools such as MITRE ATT&CK and ATLAS to understand and mitigate AI-specific adversarial tactics.<br>3. Report and escalate AI security incidents in real time. |
| ***Service Operations*** | 1. Ensure AI services meet security, resilience, and reliability standards during deployment<br>2. Oversee compliance and adherence to operational policies.<br>3. Support pre-deployment testing and post-deployment monitoring. |
| ***Auditors/Policy Makers*** | 1. Develop policies and standards for secure AI adoption.<br>2. Conduct audits to ensure compliance with established frameworks and guidelines.<br>Promote ethical and responsible AI use across sectors. |
| ***Researchers/Data Scientists*** | 1. Develop robust AI models that can resist adversarial attacks.<br>2. Investigate vulnerabilities and propose mitigations.<br>3. Work on explainability, fairness, and trustworthiness of AI systems. |
| ***Users/Practitioners*** | 1. Use AI systems according to organizational policies and ethical standards.<br>2. Report any suspicious behavior or potential vulnerabilities to the appropriate teams.<br>3. Provide feedback on the effectiveness and usability of AI systems for continuous improvement. |

### 1.3. What Defender Frameworks are missing for Defending AI Systems

MITRE ATLAS, NIST AI RMF, NIST AI AML provide defenders of AI systems with the most AI-specific guidance.  MITRE ATLAS covers adversarial tactics and techniques in detail, specifying attacker general goals against AI systems and the steps in the attack.  NIST CSF, NIST RMF, MITRE CAPEC and CISA Zero Trust Maturity Model provide more general security guidance, but could be expanded to better incorporate AI-specific risks, both for adversarial attacks and for vulnerabilities related to data, models or guardrails for AI systems.  The MIT Risk Repository offers insights for governance stakeholders, but doesn't provide enough low-level detail to inform defenders of AI systems about security measures.  Current defender frameworks require some extension to properly deal with securing AI systems.

## 2. Section Title

### 2.1. Level 2 Section Title

#### **2.1.1. Level 3 Section Title**

##### **2.1.1.1. Level 4 Section Title**

###### *2.1.1.1.1. Level 5 Section Title*

Note: Avoid using more than five heading levels.

## 3. Takeaways and Conclusion

## 4. References

## 6. Acknowledgements

## Workstream Leads Chairs: WS Lead Chair Name ([Chair.Name@example.com](mailto:Chair.Name@example.com)), Example Corp. (mailto: link for email address; http:// link for affiliation web site) (remove "s" from Chairs if one)

## Editors: Editor Name ([Editor.Name@example.com](mailto:Editor.Name@example.com)), Example Corp. (mailto: link for email address; http:// for affiliation web site) (remove "s" from Editors if just one)

List of active contributors.

## 5. Appendix

Appendix Notice Copyright © OASIS Open 2025\. All Rights Reserved. All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full Policy may be found at the OASIS website: \[https://www.oasis-open.org/policies-guidelines/ipr/\]. This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English. The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns. This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. OASIS AND ITS MEMBERS WILL NOT BE LIABLE FOR ANY DIRECT, INDIRECT, SPECIAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF ANY USE OF THIS DOCUMENT OR ANY PART THEREOF. The name "OASIS" is a trademark of OASIS, the owner and developer of this document, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, documents, while reserving the right to enforce its marks against misleading uses. Please see [https://www.oasis-open.org/policies-guidelines/trademark/](https://www.oasis-open.org/policies-guidelines/trademark/) for above guidance.

This is a Non-Standards Track Work Product. The patent provisions of the OASIS IPR Policy do not apply.

DD Month 2025 3 Non-Standards Track Copyright © OASIS Open 2025\. All Rights Reserved. Page 2 of 10 This document was last revised or approved by the CoSAI Open Project on the above date. 
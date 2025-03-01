# CVE → CWE "Root Cause Mapping" Guidance

This guidance is intended to help [CVE Numbering Authorities (CNAs)](https://www.cve.org) and those who produce or analyze [CVE Records](https://www.cve.org) to better identify and disclose the root causes of vulnerabilities. It is also likely to be helpful to those who are analyzing vulnerabilities that are not tracked by the CVE Program.

## What is Root Cause Mapping?

Root cause mapping is the identification of the underlying cause(s) of a vulnerability. This is best done by correlating CVE Records and/or bug or vulnerability tickets with CWE entries. Today, this is not done accurately at scale by the vulnerability management ecosystem.

Accurate root cause mapping is valuable because it directly illuminates where investments, policy, and practices can address the root causes responsible for vulnerabilities so that they can be eliminated. This applies to both industry and government decision makers. Additionally, it enables:

1. **Driving the removal of classes of vulnerabilities:**  
   Root cause mapping encourages a valuable feedback loop into a vendor’s SDLC or architecture design planning.

2. **Saving money:**  
   The more weaknesses avoided in your product development, the fewer vulnerabilities to manage after deployment.

3. **Trend analysis:**  
   For example, assessing how big of a problem memory safety is compared to issues like injection.

4. **Further insight into potential “exploitability”:**  
   For instance, command injection vulnerabilities tend to see increased adversary attention and may be targeted by certain actors.

5. **Transparency:**  
   Organizations can demonstrate to customers how they are targeting and tackling problems in their products.

## Overview – What Is CWE?

**Common Weakness Enumeration (CWE™)** is a community-developed list of common software and hardware weaknesses. A “weakness” is a condition in a software, firmware, hardware, or service component that, under certain circumstances, could contribute to the introduction of vulnerabilities. Referred to as CWEs, weaknesses are named, defined, and given a unique identifier on the CWE website. They can occur in the design, implementation, or other phases of a product lifecycle. Many vulnerabilities share the same CWE as their root cause, regardless of vendor or coding language.

### Weakness vs. Vulnerability Language

- **Vulnerability (as defined by the CVE Program):** An instance of one or more weaknesses in a product that can be exploited, causing a negative impact to confidentiality, integrity, or availability. It describes the result of an exploitation (e.g., “bypass authorization”, “gain privileges”, “execute malicious code”) or lists exploitation prerequisites (e.g., “unauthorized user”, “unauthenticated remote attacker”, “admin user”).

- **Weakness:** Describes an issue in the product such as “missing authentication”, “improper bounds check”, or “stack-based buffer overflow” that can lead to a vulnerability.

For example:

> **Example:**  
> *Weakness:* Insecure Direct Object Reference (IDOR) in MyProduct 10.1 to 10.6  
> *Impact:* Allows an unauthenticated attacker to read sensitive data and execute specific commands and functions with full admin rights via the page parameter to the `/api/xyz` API endpoint.

## CWE Resources & CWE Entry Structure

Familiarity with how CWE defines weaknesses is essential before diving into mapping methods. A clear grasp of these components will enhance the overall mapping process.

### Glossary

CWE offers a [glossary of terminology](#) derived from vulnerability theory. Terms can vary in meaning based on context, individual experience, and the specific area of vulnerability management. Familiarity with these terms will help streamline the mapping process.

#### Common and Widely Used Terms in CWE

The following highlights some of the most common terms, chosen based on their prevalence within CWE, vulnerability theory, and industry. These terms help in selecting accurate and precise CWE(s) for root cause mapping:

- **Important characteristics of weaknesses:**  
  - Behavior  
  - Property  
  - Technology  
  - Resource

- **Behavior qualifiers:**  
  - Improper  
  - Incorrect  
  - Missing

- **Protection mechanisms:**  
  - Authentication  
  - Authorization  
  - Neutralization  
  - Permissions

### CWE Relationships

CWE contains over 900 weaknesses ranging from abstract to technology-specific. A precise weakness typically has a “parent” (a more abstract weakness) and may have additional hierarchical relationships.

There are four types of weakness abstractions:

- **Pillar**
- **Class**
- **Base**
- **Variant**

These abstraction types indicate the level of specific information available in the CWE (such as behavior, property, resource, coding language, and technology). Weaknesses can also be grouped into a **Category** (a collection of similar weaknesses), but **vulnerabilities should never be mapped to a CWE Category**.

> **Note:** For root cause mapping, CWEs at the **Base** and **Variant** levels should be used whenever possible. **Class** level CWEs may be used only if a more specific Base or Variant CWE is not available.

Every CWE includes a Vulnerability Mapping label and Mapping Notes. The labels are:

- **ALLOWED**  
  (this CWE ID could be used to map to real-world vulnerabilities)
- **ALLOWED** *(with careful review of mapping notes)*
- **DISCOURAGED**  
  (this CWE ID should not be used to map to real-world vulnerabilities)
- **PROHIBITED**  
  (this CWE ID must not be used to map to real-world vulnerabilities)

Mapping Notes provide additional details and considerations for using the CWE for root cause mapping. For example, see the mapping notes from [CWE-20](#).


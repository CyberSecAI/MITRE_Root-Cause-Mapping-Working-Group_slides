# Unified CWE Mapping Guidance for LLMs

This document provides consolidated guidance for mapping vulnerabilities to Common Weakness Enumeration (CWE) IDs. It explains general principles, navigation strategies, and specific examples to help identify the root cause of a vulnerability accurately. Use this as a reference when automating or assisting with CWE mapping.

---

## 1. Introduction

### 1.1 What is CWE?
- **Common Weakness Enumeration (CWE™)** is a community-developed list of software and hardware weaknesses.  
- **Weakness vs. Vulnerability:**  
  - A **weakness** is an inherent flaw (e.g., “missing authentication”, “improper bounds check”) that can lead to a vulnerability.  
  - A **vulnerability** is an exploited instance of one or more weaknesses (e.g., “bypass authorization”, “execute malicious code”).

### 1.2 What is Root Cause Mapping?
- **Root Cause Mapping** identifies the underlying causes of vulnerabilities by correlating vulnerability records (e.g., CVE Records) with CWE entries.
---

## 2. General Mapping Principles

### 2.1 Selecting the Right CWE Entry
- **Type of Entry:**  
  - **Allowed:** Use entries that are defined as *Weakness* or *Composite/Chain types*.  
  - **Avoid:** Do not map to a **View** or a **Category**; these are not structured around CWE’s behavioral model.
  
- **Level of Abstraction:**  
  - Choose the **lowest level** (preferably **Base** or **Variant**) that accurately represents the weakness.
  - If no precise match exists, a higher-level CWE may be used with caution (see “Mapping Analysis” for further discussion).

- **Mapping Labels:**  
  - Each CWE includes a mapping label (e.g., **ALLOWED**, **DISCOURAGED**, or **PROHIBITED**). Use these as guidance for appropriate mapping.

### 2.2 Best Practices
- **Be Specific:** Always prefer a more detailed (child) CWE over a generic (parent) CWE if the available information supports it.
- **Distinguish Impact from Root Cause:** Ensure that the chosen CWE represents the **root cause** rather than a technical impact (e.g., avoid mapping to CWE-200 when the root cause is a missing authorization check).
- **Iterative Review:** Validate mappings using multiple sources (e.g., CNA advisories, NVD, additional documentation) and update as needed.

---

## 3. Navigating CWE for Mapping

### 3.1 CWE Website Navigation
- **Multiple Views:**  
  - **Research Concepts (e.g., CWE-1000)** and **Development Concepts (e.g., CWE-699)** offer different organizational perspectives.
  - **View-1003:** Specifically designed for simplified mapping of published vulnerabilities. Although useful, it may force mapping to a higher-level parent in some cases—always check if a more precise CWE is available.

### 3.2 Display Modes
- **Hierarchical Display:**  
  - Use the **Graph** tabs (e.g., for CWE-1000 or CWE-699) to view relationships via indented lists.  
  - Expand trees to inspect parents, children, and multiple-parent scenarios.
  
- **Slice and List Displays:**  
  - **Slice Display:** Provides a flat list with detailed fields (e.g., summary, alternate terms).  
  - **List Display:** Offers a quick view with only IDs and names; requires familiarity with CWE terminology.

- **In-Site Search & PDFs:**  
  - Utilize in-site searches (with filters like `inurl:definitions`) for finding individual CWE entries.
  - PDFs provide graphical depictions but may be less interactive.

### 3.3 Additional Navigation Tips
- **Review Ancestors/Descendants:** Look at an entry’s parents for general context and its children for more specific details.
- **Alternate Resources:** Use related databases (e.g., CAPEC) when search terms are ambiguous.

---

## 4. Specific Mapping Scenarios and Examples

### 4.1 Command Injection
- **Common Mapping:**  
  - **CWE-77**: Improper Neutralization of Special Elements used in a Command.
  - **Preferred Detail:** When details indicate operating system command injection, map to its child, **CWE-78**.
details and references to decide the most accurate mapping.

### 4.2 Memory Buffer Issues
- **General Guidance:**  
  - For buffer-related vulnerabilities, map to the most specific CWE (e.g., **CWE-122** for Heap-based Buffer Overflow rather than generic **CWE-119**).

### 4.3 Exposure of Sensitive Information
- **CWE-200 is Discouraged:**  
  - It is a high-level class that is often misused to indicate loss of confidentiality.
  - **Root Cause vs. Impact:**  
    - Map the underlying error (e.g., missing authorization, insecure permissions) rather than the resulting impact.
- **Examples:**
  - **Bad Mapping:** Mapping an authorization failure directly to CWE-200.
  - **Good Mapping:** Instead, use CWE-209 for error messages revealing sensitive information, or map to CWE-285, CWE-287, or others that represent the actual weakness.

### 4.4 Privilege Management Issues
- **CWE-269 – Improper Privilege Management:**  
  - Often misused when “privilege escalation” is described.  
  - **Clarification:**  
    - **Privileges** refer to roles or capabilities assigned to users.
    - **Permissions** are the explicit access controls on resources.
- **Best Mapping Practice:**
  - When an error leads to unauthorized privilege escalation, identify the root cause error (e.g., use CWE-266 for Incorrect Privilege Assignment rather than CWE-269 if it better captures the flaw).
- **Examples:**
  - **Bad Mapping:** Using CWE-269 solely based on “gain privileges” phrases.
  - **Good Mapping:** Map to CWE-266 when a missing or incorrect privilege assignment is the root cause.

---

## 5. Special Considerations for CWE Views

### 5.1 Using View-1003
- **Purpose:**  
  - View-1003 is intended for simplified mapping of published vulnerabilities.
- **Limitations:**  
  - It may force mapping to a broader parent (e.g., mapping HTTP request splitting to CWE-93 instead of the more specific CWE-113).
- **Advice:**  
  - Always select the most precise and specific CWE available rather than settling for the closest parent from a given view.

---

## 6. Best Practices and Final Recommendations

- **Be Specific and Iterative:**  
  - Use detailed mapping notes and check multiple fields (e.g., summary, alternate terms, parent/child relationships) before finalizing a mapping.
- **Distinguish Root Cause from Impact:**  
  - Map the error in the code (e.g., missing authorization, improper input handling) rather than the technical impact (e.g., information disclosure, resource exhaustion).
- **Leverage Multiple Views:**  
  - Utilize both hierarchical and flat (slice/list) views, and compare across Research and Developer concepts to ensure accuracy.
- **Consult Additional Resources:**  
  - When in doubt, cross-reference with external databases (e.g., CAPEC) and the CWE glossary for clarification on terminology.
- **Document Mapping Decisions:**  
  - Record any mapping corrections or justifications, as these can be used to train or refine an LLM’s understanding over time.

---

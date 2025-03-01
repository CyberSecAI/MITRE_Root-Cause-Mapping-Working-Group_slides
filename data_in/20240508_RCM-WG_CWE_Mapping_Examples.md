# Root Cause Mapping WG – CWE Mapping Examples  
**Date:** May 8, 2024  

---

## CWE-77: Improper Neutralization of Special Elements used in a Command ('Command Injection')

- Most of the time, this should map to its child **CWE-78**: Improper Neutralization of Special Elements used in an OS Command ('OS Command Injection').
- An annual problem in **Top 25 analysis**.

### CWE Site Search Results

- **Search for**: "OS command injection"

### Vulnogram

- **CWE-77 is listed before CWE-78**  
  - No parent/child relationships displayed.

### CWE-77 Examples

#### CVE-2023-20075
- "Injecting operating system commands into a legitimate command."
- **Cisco CNA** maps to CWE-77.
- **NVD** maps to CWE-78.

#### CVE-2023-36642
- "An improper neutralization of special elements used in an OS command vulnerability [CWE-78]."
- **Fortinet CNA** maps to CWE-77, even though its own advisory says CWE-78.
- **NVD** maps to CWE-78.

#### CVE-2024-21887
- "A command injection vulnerability in web components of Ivanti Connect Secure."
- This is one of the **CVE Records** cited in the recent **MITRE incident**.
- **Mapped in NVD to CWE-77**.
- Because the description only has "command injection," we need to look at the references to see if we can get more specific.
  - **Reference**: [Ivanti 0-day "command injection"](https://www.vicarius.io/vsociety/posts/two-zero-day-critical-vulnerabilities-in-ivanti-cve-2023-48605-and-cve-2024-21887-21889) appears to be basic shell metacharacters, thus OS command injection.

---

## CWE-119: Improper Restriction of Operations within the Bounds of a Memory Buffer

- Mostly used in buffer errors with low info, but a more specific child is always preferable when the info is there.

### CWE-119 Example

#### CVE-2023-30774
- "This security flaw causes a heap buffer overflow issue."
- **Red Hat CNA** maps to CWE-119: **Out-of-bounds Write**.
- **NVD** maps to CWE-787 (**closest parent forced by view-1003 compliance**).
- **Best mapping is CWE-122**: Heap-based Buffer Overflow based on keyword matching.

---

## Problems with the Phrase "Stack Overflow"

- Sometimes used for two meanings:
  1. **Stack-based buffer overflow**
  2. **Running out of available stack memory** ("Stack Exhaustion")


### "Stack Overflow" Example

#### CVE-2023-2798
- "May be vulnerable to Denial of Service attacks (DoS). If HtmlUnit is running on user-supplied web pages, an attacker may supply content that causes HtmlUnit to crash by a stack overflow."
- **Google CNA** mapped to CWE-400: **Uncontrolled Resource Consumption**.
- **NVD** mapped to CWE-787: **Out-of-bounds Write**.
- Looking at a commit reference indicates excessive recursion, so it should be mapped to CWE-674: **Uncontrolled Recursion**.

### Why is CWE-400: Uncontrolled Resource Consumption Not a Good Mapping Here?

---






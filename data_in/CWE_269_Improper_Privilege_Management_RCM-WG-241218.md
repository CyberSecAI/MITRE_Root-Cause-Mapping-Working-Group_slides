## Level set – Privileges vs Permissions 
* **Privileges**: code can assign (or define) privileges for a particular user (e.g. administrator, regular, guest). [cite: 7]
    * Generally speaking, within CWE, the "privilege" concept can include roles or capabilities. [cite: 8]
* **Permissions**: "the explicit specifications for a resource, or a set of resources, that defines which actors are allowed to access that resource, and which actions may be performed by those actors. Permissions can contribute to the definition of one or more intended control spheres.“
    * Defines who can access an object or resource (ex: a file).
    * Roughly: privileges are tied to people; permissions are for resources.
* **CWE glossary**: [https://cwe.mitre.org/documents/glossary/index.html](https://cwe.mitre.org/documents/glossary/index.html)
* **Significant challenge**: for different CWE users, the same concept has different meanings in different technologies and access control models (privilege, role, permission [sic], capability, …).



## Mapping Discussion – Privileges 
* **CWE-269: Improper Privilege Management**
    * The product does not properly assign, modify, track, or check privileges for an actor, creating an unintended sphere of control for that actor.
    * A common mapping mistake is using CWE-269 in situations where an adversary is able to gain privileges as an impact. [cite: 10]
    * "gain privileges" / "gain root access" / "escalate privileges" and other phrases do not prove CWE-269. [cite: 10]
    * 151+ CWEs have “Gain Privileges or Assume Identity” potential impact. [cite: 10]
    * Ranked 15th on this year’s Top 25 with 324 total mappings despite being “discouraged”. [cite: 10]
    * The name attempts to generalize from a classification perspective. [cite: 10]



## Bad Mapping Example – CWE-269 
* “[Product] contains a local privilege escalation vulnerability. [cite: 11]
    * A console user with access to [Product] may exploit this vulnerability to escalate privileges to gain root access to the system. [cite: 12]
    * **Original CNA mapping**: CWE-269 Improper Privilege Management [cite: 13]
    * **Corrected mapping after consult**: CWE-78 OS Command Injection [cite: 13]
    * **Explanation**: A better CVE description would have made this mapping easier to identify by including information about the root cause. [cite: 13]
    * **Additional considerations**: Considering all technical references at the time of mapping could have helped as well (… assuming such references were available at that time). [cite: 14]



## Good mapping example - Privileges 
* A Improper Privilege Management vulnerability in [Product] causes permission changes in [Product] not to be reflected to users while they are logged in the [Product]. [cite: 15]
    * This would cause the users to retain their previous permissions, even if they change groups on [Product], for example, to a lower privileged group, or are removed from a group, thus retaining their access instead of losing it. [cite: 16]
    * **Original mapping**: CWE-269 Improper Privilege Management [cite: 17]
    * **Corrected mapping after consult**: CWE-266 Incorrect Privilege Assignment [cite: 17]
    * **Explanation**: The original mapping encompassed the root cause weakness, although a more specific child was a better mapping choice. [cite: 17]
    * **Note**: this is part of a broader pattern of “not propagating changes” that may need a new CWE entry(ies). [cite: 17]



## Technical Impact Phrases - Privileges 
* Privileges "gain privileges" / "gain root access" / "gain [XYZ] access/privileges" [cite: 18]
* "escalate privileges" / "escalation of privileges" [cite: 18]
* "elevation of privilege" / "elevate privilege" [cite: 18]
* "privilege escalation" / "vertical privilege escalation" / "horizontal privilege escalation" [cite: 18]
* "local privilege escalation" / LPE [cite: 18]






### CWE-269 Vulnerability Mapping Notes 



* CWE-269 is commonly misused. It can be conflated with "privilege escalation", which is a technical impact that is listed in many low-information vulnerability reports. [cite: 20]
* It is not useful for trend analysis. [cite: 20]
* If an error or mistake allows privilege escalation, then use the CWE ID for that mistake. Avoid using CWE-269 when only phrases such as "privilege escalation" or "gain privileges" are available, as these indicate technical impact of the vulnerability - not the root cause weakness. If the root cause seems to be directly related to privileges, then examine the children of CWE-269 for additional hints, such as Execution with Unnecessary Privileges (CWE-250) or Incorrect Privilege Assignment (CWE-266). [cite: 20]

[Image 4]

[Image 5]

[Image 6]

[Image 7]
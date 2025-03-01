
* Mapping Discussion – “Exposure of Sensitive Information” 


## CWE-200: Exposure of Sensitive Information to an Unauthorized Actor 

* High-level class encompassing many children. [cite: 3]
* DISCOURAGED for mapping. [cite: 3]
* Ranked 17th in the 2024 Top 25. [cite: 3]

### Why CWE-200 is discouraged 


Reason: Frequent Misuse

Rationale:
CWE-200 is commonly misused to represent the loss of confidentiality in a vulnerability, but confidentiality loss is a technical impact - not a root cause error. As of CWE 4.9, over 400 CWE entries can lead to a loss of confidentiality. Other options are often available. [REF-1287].

Comments:
If an error or mistake causes information to be disclosed, then use the CWE ID for that error. Consider starting with improper authorization (CWE-285), insecure permissions (CWE-732), improper authentication (CWE-287), etc. Also consider children such as Insertion of Sensitive Information Into Sent Data (CWE-201), Observable Discrepancy (CWE-203), Insertion of Sensitive Information into Externally-Accessible File or Directory (CWE-538), or others.




### Distinguishing between root cause and impact 
* Before mapping to a CWE in the CWE-200 tree, ensure that the root cause weakness is exposing information directly and not as an impact of a weakness. [cite: 5]
* Information exposures can occur in different ways: 
    * The code explicitly inserts sensitive information into resources or messages that are intentionally made accessible to unauthorized actors, but should not contain the information - i.e., the information should have been “scrubbed” or “sanitized”. [cite: 6]
    * A different weakness or mistake indirectly inserts the sensitive information into resources, such as a web script error revealing the full system path of the program. [cite: 6]
    * The code manages resources that intentionally contain sensitive information, but the resources are unintentionally made accessible to unauthorized actors. In this case, the information exposure is resultant - i.e., a different weakness enabled the access to the information in the first place. [cite: 6]

(emerging suspicion: this can happen when the product doesn’t “redact” information it’s supposed to)


## Bad Mapping Example 
* **[Product]** fails to perform authorization checks in the endpoint of the **[Product]** plugin allowing an attacker to get limited information about a post if they know the post ID. [cite: 7]
    * **Original mapping**: CWE-200: Exposure of Sensitive Information to an Unauthorized Actor [cite: 7]
    * **Corrected mapping after consult**: CWE-862: Missing Authorization [cite: 7]
    * **Explanation**: Getting the information about a post is a technical impact and the actual root cause that allowed this was the missing authorization check. [cite: 7]



## Good Mapping Example 
* **[Product]** contains a vulnerability when using various commands that can cause the content of shell interpreted variables to be printed in the terminal. [cite: 8, 9]
    * **Original CNA mapping**: CWE-200 [cite: 9]
    * **Additional info from CNA**: “raslog (error message) printing sensitive information when the command is not entered correctly.” [cite: 9]
    * **Corrected mapping after consult**: CWE-209: Generation of Error Message Containing Sensitive Information [cite: 10]
    * **Explanation**: The weakness was correct, but greatly benefited from a lower-level child providing more detail. A better description would have helped. [cite: 10]



## Technical Impact Phrases – Information Disclosure 
* “Information disclosure vulnerability” [cite: 11]
* "Information Exposure" [cite: 11]
* "unauthorized read access" [cite: 11]
* "access sensitive / restricted information" [cite: 11]
* "obtain sensitive information" [cite: 11]






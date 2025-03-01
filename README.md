# MITRE_Root-Cause-Mapping-Working-Group_slides

- [MITRE\_Root-Cause-Mapping-Working-Group\_slides](#mitre_root-cause-mapping-working-group_slides)
  - [Overview](#overview)
  - [Recipe](#recipe)
  - [Slides](#slides)
  - [Guidance](#guidance)
    - [Recipe](#recipe-1)
  - [Summarize](#summarize)


## Overview
[Unified_CWE_Mapping_Guidance_for_LLMs.md](./Unified_CWE_Mapping_Guidance_for_LLMs.md) is a summary of the MITRE CWE Guidance in a form suitable for an LLM to use.

> [!NOTE]
> This guidance is a complement to the specific "Vulnerability Mapping Notes" per CWE e.g. "Vulnerability Mapping Notes" section of https://cwe.mitre.org/data/definitions/20.html 

## Recipe
1. Convert relevant  Root Cause Mapping Working Group meeting slide decks to MarkDown.
2. Convert relevant guidance from MITRE CWE website to MarkDown 
3. Summarize the Markdown documents to one Markdown document suitable for use by an LLM

> [!NOTE]
> ChatGPT was used to convert to MarkDown (as it worked better than MarkItDown or other such tools), and to summarize the content.
> 
> Some parts were manually removed (if not relevant to mapping guidance).

## Slides

All slides from https://github.com/Root-Cause-Mapping-Working-Group/RCM-WG/tree/main/meeting_slides were reviewed and a subset were deemed relevant for mapping information.

Note: RCM-WG-241204 is a subset of RCM-WG-241218 so not converted.

## Guidance

1. https://cwe.mitre.org/documents/cwe_usage/guidance.html
2. https://cwe.mitre.org/documents/cwe_usage/mapping_navigation.html

### Recipe

1. Prompt to ChatGPT:
>convert the guidance on this page to markdown: https://cwe.mitre.org/documents/cwe_usage/guidance.html
2. Manually remove parts not relevant for guidance of an LLM


## Summarize

Unified_CWE_Mapping_Guidance_for_LLMs.md is the Unified CWE Mapping Guidance for LLMs.


>review all this guidance and create a markdown document for it. 
The result will be used by an LLM for mapping CWEs so it should optimal for an LLM - so reiterate or summarize where necessary. And remove duplicated parts.

- 20240508_RCM-WG_CWE_Mapping_Examples.md
- CWE_200_sensitive_info_RCM-WG-250115.pptx.md
- CWE_269_Improper_Privilege_Management_RCM-WG-241218.md
- CWE_Mapping_ Navigation_Guidance.md
- CWE_RCWG_Mapping_Guidance.md
- View_1003_RCM-WG_240925.md

*This document is intended to serve as an optimal reference for an LLM performing CWE mapping, integrating guidance from multiple sources while eliminating redundancy. Use it to guide automated mapping decisions and ensure consistency in identifying the root cause weaknesses in vulnerabilities.*
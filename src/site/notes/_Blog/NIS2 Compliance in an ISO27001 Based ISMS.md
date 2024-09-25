---
{"dg-publish":true,"permalink":"/blog/nis-2-compliance-in-an-iso-27001-based-isms/","tags":["blog","iso27001"],"noteIcon":"1","created":"2024-08-15T09:44:50.123+02:00","updated":"2024-08-14T10:46:13.000+02:00"}
---

## About NIS2
NIS2 is an EU directive that enhances cybersecurity across critical sectors, expanding on the original NIS Directive from 2016. It covers more industries, requires stronger security measures, and mandates faster incident reporting. NIS2 aims to improve overall cybersecurity and cooperation across the EU, ensuring a safer digital environment.
It goes into effect on October 24 this year.

## The Challenge
Implementing a new framework, such as NIS2, presents several challenges, even for organisations with established processes and controls, like those based on ISO 27001. The first critical step in this process is understanding the purpose and scope of the new framework. This involves thoroughly analysing how the framework’s objectives align with the organisation’s goals and security posture.

Once the purpose is clear, the next challenge is mapping the new requirements to your current framework. This means identifying where the new regulations overlap with existing controls and where they introduce new obligations. The goal is to integrate these new requirements without duplicating efforts or creating unnecessary complexity. This mapping process requires a detailed comparison of both frameworks, understanding their differences and similarities, and determining how best to align them to ensure compliance while maintaining efficiency.

This step is crucial because it helps organisations avoid redundant work, ensures that existing strengths are leveraged, and facilitates a smoother transition to compliance with the new framework. It also helps identify any gaps that need to be addressed, allowing for a more targeted and effective implementation strategy.

## NIS2 To ISO27001/2
The cybersecurity requirements of NIS2 are well covered under ISO27001, both based upon my own investigation and other sources such as [KPMG](https://assets.kpmg.com/content/dam/kpmg/pl/pdf/2023/10/kpmg-network-and-information-security-directive-nis2.pdf)
In summary, the primary mapping of the cybersecurity requirements can be done like this,

| **Control Title**                      | **NIS2**              | **ISO27001**                             |
| -------------------------------------- | --------------------- | ---------------------------------------- |
| Cybersecurity roles & responsibilities | NIS 2 Article 7 & 20  | ISO 27001:2022 Clause 5.3                |
| ISMS Scope                             | NIS 2 Article 7 & 21  | ISO 27001:2022 Clause 4.3                |
| Third-party risk management            | NIS 2 Article 12 & 21 | ISO 27001:2022 Annex A.15                |
| Malware protection                     | NIS 2 Article 21      | ISO 27002 8.7 Protection against malware |
### What about Article 23 ?
Even though the main cybersecurity requirements are covered within other ISO27001 controls, the requirements of Article 23 are not. 
Article 23 deals with reporting requirements to government oversight entities and regulators in cases of incidents and breaches. 
A good way to approach this is to define a new control, such as "The company has reporting routines in place for reporting incidents to appropriate authorities."
Then create the routine described as a topic-specific policy under the incident management policy or similar, depending on your structure. This document should define how reporting is done, who has responsibility in the org and also define how records of such reports are to be kept (important for evidence that the process is followed).

## Finally
Hopefully this information will help you on the journey of making NIS2 part of their ISMS and my plan is to also do a similar dive into other frameworks in the future.
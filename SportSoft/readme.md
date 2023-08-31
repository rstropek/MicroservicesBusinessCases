# *SportSoft* - Reinventing the Future of Sports Management Software

## Background

You are applying for a job as the Chief Technical Officer (CTO) in a thriving software company, *SportSoft Ltd*. The company is reputable for its flagship software, *SoccerAccountant*, catering to the administrative needs of large soccer clubs. While SoccerAccountant has enjoyed considerable market success, the software is grappling with technical obsolescence, performance issues, and a lack of modern features.

## Introduction to SportSoft Ltd

*SportSoft* was established in 1993 and quickly became a pioneer in sports management software. The company has a global footprint, with clients ranging from emerging soccer clubs to established international organizations. Their success is largely attributed to SoccerAccountant, but they also provide consulting and customized solutions.

## Current Scenario

*SoccerAccountant*, once a market leader, is now facing stiff competition from modern, cloud-based solutions. The software is built on outdated technologies, with a monolithic architecture using *Delphi* and an *Informix SQL* database. It is notorious for consuming excessive memory, slow response times, and frequent crashes. The *Online Fan Shop* module, despite being relatively less complex, has already been rewritten in PHP, but is infamously unreliable and sluggish. The high upfront licensing cost coupled with 20% annual maintenance fees adds to customer grievances.

## SoccerAccountant Modules

SoccerAccountant is segmented into the following modules:

* Accounting (*Buchhaltung*)
* Asset Accounting (*Anlagenbuchhaltung*)
* Payroll Accounting (*Loh- und Gehaltsverrechnung*)
* Online Fan Shop
* Human Resource Management (*Personalentwicklung*)

An external audit revealed that all modules except the Online Fan Shop have comparable complexity and codebase size. The only exception is the online fan shop module, which is simpler. It has approximately half the complexity and size of the other software modules.

At customers, the different modules are typically used by different departments. All modules share some common master data (*Stammdaten*) like user profiles, employees, products (for fan shop), players and teams, etc.

## Project Objective

*SportSoft* intends to revamp *SoccerAccountant*, transitioning it into a cloud-based Software-as-a-Service (SaaS) application, with no immediate functional enhancements planned. The focus is to modernize the technology stack, improve performance, and lay a foundation for future scalability and feature expansions. The customers will now pay a monthly subscription fee and access the application via web browsers and/or mobile devices.

## Resources

*SportSoft* has assembled a development team of 40 experts. Half of them are long-time employeess with in-depth knowledge of *SoccerAccountant*. They have participated in technical trainings to update their software development skills. The rest are new recruits skilled in modern technologies. Additionally, there are five business domain experts assigned for each module to clarify functional and non-functional requirements.

## Your Tasks

As a prospective CTO, you are tasked with crafting a revitalization strategy that encompasses the software architecture and team organization.

### Software Architecture

Outline and elaborate on your architectural vision by addressing the following questions:

* Which development technologies will you use?
* Will you split the software into modules? If you do, which modules will you build and how will they communicate?
* Will you use container technology?
* If any, which cloud computing components will you use?

### Team Organization

Propose an optimal structure for the development team by tackling these questions:

* Will you split them up in teams?
* How will they work together (e.g. exchange source code)?
* Which tools will they use (e.g. requirements management, development tools, bug tracking, communication, document management etc.)?
* How will the organizational and operational structure look like?

# Building a Microservices Architecture for *Reviewr*

## Company Overview

*Reviewr* is a startup aiming to revolutionize the way reviews are done across various sectors. The brainchild of a passionate founder, who identified gaps in the current review processes in domains ranging from construction to software security, the company seeks to offer a unified platform where standardized and quality reviews can be conducted seamlessly.

The founder, Aisha Khan, an astute entrepreneur, realized the vast potential of aggregating the fragmented review processes under a singular, holistic platform. Having seen firsthand the importance and impact of reviews, he envisioned a SaaS platform that not only streamlines the review process but also ensures consistency and quality. Although well-versed in the world of business and having a basic understanding of software, Aisha's strengths lie in her networking, vision, and ability to secure funding, as demonstrated by her recent acquisition of 10 million USD in venture capital.

Aisha's vision for *Reviewr* is threefold:

- *Standard Creation*: Allow professionals to create review standards or guidelines. This includes documentations, checklists, diagrams, etc., detailing the intricacies of conducting reviews for specific sectors.
- *Review Execution*: Reviewers should have the capability to execute the reviews based on the set guidelines, ensuring uniformity and standardization.
- *Transparency and Accessibility*: The results of these reviews should be easily accessible to external parties, such as end customers, for transparency and trust-building.

Aisha thinks big. She wants to build a platform that can rapidly grow and onboard a large number of users spread across the globe. She also wants to ensure that the platform is scalable and can be easily extended to support new features and functionalities.

## Business Model

### Domain Experts

Domain experts, recognized professionals in their respective fields, have the opportunity to use the Reviewr platform to design and draft comprehensive review guidelines tailored to their domains. To facilitate this, domain experts are charged a *monthly subscription fee*. This fee grants them the tools and platform access required to craft their review guidelines and update them as required.

### In-house Experts

Understanding the demand for standardized and frequently used guidelines, *Reviewr* invests in its own team of domain experts. These experts create widely-recognized and frequently-utilized review guidelines. These in-house guidelines serve as the backbone of the platform, ensuring even new users have immediate access to high-quality review standards. These guidelines, designed by *Reviewr*’s in-house team, are available *at no cost* to all platform users.

### Review Performers

Individuals or businesses seeking to perform reviews using the Reviewr platform have a tiered pricing structure:

- Usage of up to *three free guidelines* is available at no cost.
- Should reviewers wish to utilize more than three guidelines, they are charged a *monthly subscription fee*.
  - For specialized guidelines designed by external domain experts:
  - Reviewers pay a *one-time fee* for each guideline they wish to access.
  - Of this fee, *75% is disbursed to the domain expert* who crafted the guideline, acknowledging their expertise and contribution.
  - Reviewr retains the remaining *25%* to cover platform maintenance, transaction processing, and other associated costs.

Reviewers can share the results of the review processes with end customers. This is done by providing the end customer with a *unique URL* that grants them access to the review results. This URL is generated by the *Reviewr* platform and is available to the reviewer at no cost.

Reviewers can also generate digitally signed certificates of the review results. These certificates are generated and signed by the *Reviewr* platform. They are only available for reviewers paying a higher monthly subscription fee ("Professional" plan).

### Summary

This business model ensures a continuous flow of revenue for *Reviewr*, from both domain experts and those performing the reviews. At the same time, it incentivizes domain experts to provide high-quality, comprehensive guidelines, knowing they stand to earn from each purchase. With free access to select guidelines, *Reviewr* encourages wider platform adoption, while the tiered pricing structures cater to both casual users and professionals.

## Modules

Aisha has hired you as a consultant to help her build the platform. She has provided you with a list of modules that she believes are required to build the platform:

- *Standards Service* (web application): Manages the creation, updating, and deletion of review standards.
- *Review Execution Service* (web application, mobile app): This service manages the actual review process, from initiation to completion. It uses the standards set by the Standards Service to guide reviewers.
- *Result Service* (web application): Post-review, the results are stored and managed by this service. It ensures that the results are stored securely and can be retrieved quickly.
- *User Management Service* (web application): Manages user profiles, authentication, and roles (e.g., professional, reviewer, end customer).
- *Notification Service* (emails, push notifications): To keep all stakeholders informed about review statuses, updates, and any necessary feedback.
- *Integration Service* (public APIs): As *Reviewr* grows, integration with external tools and platforms may become essential.

## *Reviewr* - Your Tasks

### High-level Architecture of *Reviewr*

Draft a high-level architecture diagram for *Reviewr*. This should visually represent how the platform's services interact and the flow of data.

- Break down the Microservices as mentioned in the case study: Standards Service, Review Execution Service, etc.
- Define the databases, caching mechanisms, APIs, or other systems each service might require.
- Describe how these services communicate, the protocols they might use, and any potential bottlenecks or single points of failure.

### Security-Related Aspects of the Architecture

Ensure that all data within *Reviewr*, especially reviews and user data, is protected from unauthorized access, alteration, or deletion.

- Discuss encryption methods, both for data in transit and data at rest.
- Examine the authentication and authorization mechanisms for users, especially differentiating between domain experts, reviewers, and end consumers.
- Propose strategies to handle DDoS attacks, and methods to prevent SQL injection, cross-site scripting, etc.
- Describe other vulnerability points you can think of and how to mitigate them.

### Organizational Structure and Hiring Plan

Propose an organizational structure that will support the architecture and long-term goals of *Reviewr*. Assist Aisha in determining the roles required for success.

- Break down the teams needed to manage each microservice.
- Describe support roles such as Quality Assurance, DevOps, and Database Administrators.
- Suggest the initial key hires Aisha should prioritize.
- Estimate the potential size of each team and provide a hiring timeline, prioritizing critical roles/services.

### Cloud Usage for *Reviewr*

Describe how *Reviewr* can best leverage cloud technologies for scalability, reliability, and cost-effectiveness.

- Suggest a suitable cloud provider (e.g., AWS, Azure, or Google Cloud) and the specific services offered by it that would benefit *Reviewr*.
- Discuss strategies for scaling services up or down based on demand.
- Explain potential multi-region deployments.
- Consider cost-saving measures, like serverless computing or spot instances, and when they might be appropriate.
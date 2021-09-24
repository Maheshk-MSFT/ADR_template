# Improving Developer Velocity - a Case Study

## Introduction

In a 2020 paper published by McKinsey titled *Developer Velocity: How software
excellence fuels business performance*, it stated that companies with top "Developer Velocity Index (DVI)" outperform the market with 4-5 times revenue grow and 55% higher innovation ("Measured by level of adoption of new technologies and ability to innovate faster and beat competition through innovation led growth"). To learn more about Developer Velocity, you can [download a copy of the white paper at this Azure page](https://azure.microsoft.com/en-us/overview/developer-velocity).

From the McKinsey paper, Developer Velocity is defined as the ability to drive transformative business performance through software development. Empowering developers, creating the right environment to innovate, and removing points of friction can all contribute to a high Developer Velocity.

The goal of this white paper is highlight some best practices that could help an organization to achieve these high-level ideal organizational states. The best practices in this paper is more focused on communication and collaboration best practices in an Software Engineering Team. We will use the engagement between Microsoft and XP Investments as a case study and demonstrate on how we used these best practices to improve developer velocity.

## Engagement Background and Challenges

[XP](https://www.xpi.com.br/quem-somos/) is a financial services company located in Brazil. According to their "about us" page, their purpose is to "transform the financial market to improve people's lives."

[Microsoft](https://www.microsoft.com/) is a global software company whose mission is to "empower every person and organization on the planet to achieve more."

In Spring 2021, XP and Microsoft started an engagement with engineers from both companies to co-develop the foundation of the next generation of XP's data platform.

The goal of this data platform is to provide a centralized platform that has:

1. Data Catalog
2. Monitoring / Observability
3. Alerts
4. Logging
5. Discoverability
6. Workflow Management
7. Self-Service

Not only are the engineers from the two companies never worked with one another before this engagement, the teams within the respective companies are also relatively new. This presented challenges are how to foster a culture of collaboration and healthy communication. The team was also geo-distributed. Engineers from Microsoft were primarily located various parts in the US and XP engineers were located in Brazil. The team needed to adapt and effectively collaborate across different timezones.

This project was limited to 8 weeks. This meant the team needed to design, scope and execute within that timeframe. Given this timeframe, the scope needed to be reasonable but still needed to implement a demonstrable product that has a high ROI in terms of impact to future development.

## Core Principles

Here are the core principles that are at the root of the best practices utilized in this engagement:

* **Build Trust**: Trust is at the center of how we worked with one another. There are assumptions about trust that is central in our day-to-day work: Trust that developers will raise any blockers or issues that arise. Trust that leads will be transparent about risks and manage external distractions. Trust that colleagues have the project's and other colleagues' best interest at heart. Some of the best practices outlined fosters trust in one another.
* **Provide Context over Control**: [One of the core tenants on Netflix's Culture Page](https://jobs.netflix.com/culture#context-not-control), Context over Control is about providing the team with as much context as possible so that the team can achieve autonomy and self-direction.
* **Aim for Clarity over Consensus**: It is better to have clarity on the situation or challenge, and understand the tradeoffs between options than to strive for agreements amongst the team without having clarity on the whole picture.
* **Validate Early and Fail Fast**: An invalidated hypotheses is as important as a validated one. It's advantageous to prioritize the risks in the early part of the project; this allows more time to pivot.
* **Strive for Depth**: Understanding the foundations is essential for a team to stay flexible and agile. It allows us to make better decisions. And understanding the motivations behind the tools, languages, and frameworks we use allows us to choose the right ones for the job.

## Best Practices

We used the following best practices during the 8 week engagement. In combination, these best practices created a highly-functional project team. Despite time zone differences and language barriers, the team accomplished what was scoped and maintained high morale and strong sense of team.

### Envision Together

Forming a vision together allows the everyone on the team to have a shared ownership of the end-product. However collectively shaping a vision is often a messy and long process. XP used a methodology called [Lean Inception](https://martinfowler.com/articles/lean-inception/) to provide a structure for this process. Lean Inception facilitates the process by providing discussion goals and milestones. The result of this process is a shared vision of a solution that everyone is excited about.

### Architecture Design Sessions (ADS) and Records (ADR)

Architecture Design Sessions (ADS) are designed to guide the participants through a series of design discussions. During the design sessions, participants can break into smaller groups to answer certain architecture questions and conduct investigations on the viability of certain ideas. These groups can then make recommendations on certain approaches. At the end of the ADS, the result is a detailed architecture diagram that specifies the initial design of the architecture. Accompanying the architecture diagram should be a collection of [Architecture Decision Records](https://adr.github.io)(ADRs).

Architecture Design Records are to capture the particular challenge, and the reasons why a particular decision was reached. It should also include other viable options considered as well as the impact and tradeoff of the decision. ADRs are designed to be iterable, meaning that designs and decisions can be changed if situations or new findings appear. This is done by adding to the collection of ADRs and reflect the change.

Because Architecture Design Records is a community-backed initiative, there is good community support on its tooling. [Markdown ADR (madr)](https://adr.github.io/madr) provides a definitive template for the document. There are even tools such as [Log4brains](https://github.com/thomvaill/log4brains) that allows for statically generated websites built on madr.

### MonoRepo

There is fierce debate within the development community around MonoRepos. We found MonoRepos helpful for projects as it helps with collaboration, and enables team members to jump between different workstreams. The design around MonoRepos requires more effort as the project can grow quickly and become unwieldy. We were intentional on the file structure to ensure that there is minimal effort for a team to break off of the monorepo and create a separate repo. We achieved this by encapsulate all aspects of a particular application into its own directory, shown below:

```tree
/(project)
|  /docs
|  /infrastructure
|  |  /pipelines
|  |  /iac
|  /apps
|  |  /app-a
|  |  |  /cicd
|  |  |  /docs
|  |  |  /tests
|  |  |  /src
|  |  /app-b  
|  |  |  /cicd  
|  |  |  /docs
|  |  |  /tests
|  |  |  /src
```

### Code-With

An important statement we made at the outset of this project was that the teams from the two companies operation as ONE team, working together towards a common goal. As a single project team from disparate companies, we were able to devote 100% of our energy to achieving our project milestone. Every member of the team brought their unique knowledge and abilities to bear on their work items and we leveraged pairing to ensure cross pollination of knowledge.

### Workstreams

We identified the following workstreams:

* DevOps
* API
* Transformation
* Streaming

With these workstreams, we identified small v-teams of engineers. A best practice we used for code-with, was that every v-team had a good mix of people from both companies, working together to complete the definition of done and success criteria for user stories assigned to their workstream. Engineers were not pigeonholed to a single workstream and there was freedom to move between workstreams as tasks completed. Some people preferred to stay in a workstream for the duration and that was also acceptable.

One issue we discovered with the workstreams during a sprint retrospective, was that workstreams were becoming siloed and information that might be useful outside of the workstream wasn't shared. We mitigated this by proactively sharing knowledge in our Teams channel and prefixing the subject with [workstream].

i.e. [API] Learned this cool thing about Helm charts!

### End of Sprint Demos

We scheduled weekly sprint demos to showcase our work to each other (the different workstreams) but also to stakeholders outside of the project team. The XP cloud team and management attended demos when they could and also we recorded them all for anyone to view at their own convenience. We time-boxed our demo meetings to 30 minutes long and with 4 workstreams, alloted 7 minutes per workstream demo.

### Informed Captain

The informed captain is a transitory role empowered to gather all facts and opinions about a subject that requires a decision or direction, and is further empowered to make a decision for the team. (and to document that decision!) We assigned different informed captains for different decisions and rotated the feeling of responsibility.

The informed captain can help with problems of analysis paralysis which can be bad with one person but when a group or committee tries to make a decision by consensus, this can take a prohibitively long time to achieve.

### Working Agreements

Our working agreement defined HOW we worked together and comprised of 5 main sections:

* Collaboration
* Communication norms
* Code management [contributing guidelines](./CONTRIBUTING.md)
* Definition of done
* Norms for reviewing and submitting pull requests

Often these norms or practices are not written down. Eliminating assumptions makes working together more frictionless.
Communication norms contained items like:

* WHEN core working hours for the project - our team spread across 4 time zones
* WHERE our communications happen (Teams - not email, channels - not chat)
* WHAT our communication was (async, meetings should begin / end on time, should contain an agenda)
* HOW User stories broken down to small tasks, keeping pull requests small and manageably-sized

### PRolice

Many software projects have problems with pull requests. Problems like:

1. Pile ups - sudden large backlog of PRs
2. Stuck PRs - engineers disagreeing and gridlocking PRs
3. Large PRs - PRs that try to solve the problems of the universe in one PR and touch 100's of files

Our working agreement helped solve #3 - our PRs for this project remained small and manageable. The rest? Solved by the PRolice!

What is the PRolice?

The PRolice is a rotating person (rotated by Sprint) that monitors the PRs and tags people to review them. If a PR isn't approved in a day or more, the PRolice will investigate the reason. Is it stuck? Is it waiting on changes? Are people disagreeing? The PRolice facilitates the approval (i.e. nag submitter about making their changes, schedule a meeting with disagreeing engineers and go through the PR together in the meeting.)

After implementing the PRolice (and small tasks), we didn't have any PRs that spanned across the day boundary.

The key is to rotate the role - no one wants to be PRolice forever.

Benefits of this practice are:

1. Higher morale
2. Higher velocity
3. No one gets stuck in the "no one cares about my PRs" mentality

## Outcome

## Conclusion

The goal of this white paper is to outline and highlight some best practices utilized by a new, well-sized development team. This was a ideal project. We of course understand that every team is different and that no two teams are the same.

## References

* ["Developer Velocity" by McKinsey](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/developer-velocity-how-software-excellence-fuels-business-performance)
* [Work Agreement Template](./work-agreement-template.md)
* [Architecture Design Sessions](https://www.linkedin.com/pulse/architecture-design-session-ads-vs-business-ideation-junco-boquer/)
* [Lightweight Architecture Decision Records](https://www.thoughtworks.com/pt/radar/techniques/lightweight-architecture-decision-records)

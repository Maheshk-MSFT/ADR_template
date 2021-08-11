# (Title)

## Introduction

In a 2020 paper published by McKinsey on the importance of Developer Velocity, it stated that...(TODO: Set the stage to talk to highlight the importance of Developer Velocity.)

(TODO: Connect collaboration and velocity acceleration)

(TODO: Set up the transition to background by stating that the paper will use the XP-DevSquad engagement as a case study for rapid development, despite it being a brand new team, and working across timezones)

## Background

(TODO: Talk about XP and the goal to create a Data Platform)
(TODO: Talk about the team on both sides)
(TODO: Talk about the challenges from a project management perspective)

[XP](https://www.xpi.com.br/quem-somos/) is a financial services company located in Brazil. According to their "about us" page, their purpose is to "transform the financial market to improve people's lives."

[Microsoft](https://www.microsoft.com/) is a global software company whose mission is to "empower every person and organization on the planet to achieve more."

In Spring 2021, XP and Microsoft created a joint team to co-develop the beginnings of the next generation of XP's data platform. The Microsoft engagement period was limited to 8 weeks of scope so this specific team could not feasibly implement the entire data platform end-to-end in the time alloted. XP is running Generation 2 of their data platform and wished to implement an improved data platform for their main consumers: the data engineering team.

The goal of the next generation data platform is to provide a centralized platform that has:

1. Data Catalog
2. Monitoring / Observability
3. Alerts
4. Logging
5. Discoverability
6. Workflow Management
7. Self-Service

## Best Practices

We used the following best practices during the 8 week engagement. In combination, these best practices created a project team that had high velocity, morale, agility; and despite time zone differences and language barriers, we produced what set out to accomplish.

(TODO: could probably use more setup here.)

### MonoRepo

Our team decided on using a [monorepo](https://en.wikipedia.org/wiki/Monorepo) for development. We found this efficient as we were able to navigate between projects and view patterns / documentation. It improved collaboration between the workstreams.

(TODO: can someone add more here? I'm grasping at straws.)

### Code-With

An important statement we made at the outset of this project was we are ONE team, working together towards a common goal. People working for different companies on one project can sabotage this intent. Where this project succeeded in that intent where others have failed, is due BOTH companies giving the project members dedicated time to focus. There was no split attention, no competing agendas. As a single project team from disparate companies, we were able to devote 100% of our energy to making our milestone. Every member of the team brought their unique knowledge and abilities to bear on their work items and we leveraged pairing to ensure cross pollination of knowledge.

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

### Document Everything

### Working Agreements

Our working agreement defined HOW we worked together and comprised of 5 main sections:

* Collaboration
* Communication norms
* Code management (link to our contributing.md)
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

## References

* ["Developer Velocity" by McKinsey](https://www.mckinsey.com/industries/technology-media-and-telecommunications/our-insights/developer-velocity-how-software-excellence-fuels-business-performance)

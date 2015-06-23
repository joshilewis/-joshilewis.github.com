# Branching and Deployment Flow #
TL;DR: We can deploy and test each feature in our dev environment independently and in combination before promotion. This is done through some simple Git and Jenkins setup and simple team discipline. Promotion-ready features are not blocked by 'immature' work-in-progress (WIP), but WIP is still independently testable. The build server tells us when Feature Branches are out of date.

----------

I'm quite proud of the delivery flow that one of my teams is currently using. The setup and workflows/discipline are quite simple and relatively easy to create and have turned out to be quite big enablers for increased agility, responsiveness and quality.

##The basic setup##
- We use GitFlow with Feature Branching, without *release* or *hotfix* branches
- On *Git Push* each Feature Branch is built, tested and deployed to its own IIS Application/Virtual Directory in the dev environment (using msdeploy)
- Jenkins tells us when there are Merge Conflicts with *development*
- Developers can do testing on the deployed feature before marking the work as Ready for Test
- When the tester is happy with the feature, dev merges feature back into develop
- If bugs are found, work continues in isolation in the Feature Branch
- The changes to *develop* are merged into existing Feature Branches
- Each push to *develop* triggers another build-test-deploy CI job to the 'master' dev environment
- Deploys to the QA, Staging and Production environments are one-click and triggered manually. 
- Deploys to the Staging and Production environments are based on *master*
- When features are ready for production, *develop* is merged into *master*
- The team also makes use of a canary production server (served a fraction of live traffic through load balancing) with automated fan-out and roll-back.
- The team has little automated acceptance testing at the moment, but is working to improve this.

##Results##
This setup has solved some issues the team had in the past, such as not being able to deploy ready-for-test work to the QA environment, due to 'contamination' by not-ready-for-test work. This in turn was caused by unpredictable and highly varying priorities, and in variable cycle-time within the dev and ready-for-test phases. 

##Analysis##
Using feature branches means we're not doing true Continuous Delivery or even Continuous Integration. We have tried to mitigate this by being very disciplined around not letting Feature Branches diverge too far from *develop*. We have a Jenkins job which attempts a 'reverse merge' of the feature into *develop* on every feature branch push, which fails if there are any merge conflicts.

There is additional house-keeping in that feature branches need to be created on commencement of work and deleted at end-of-life. Not only that, the IIS Applications created for each Feature Branch need to be deleted manually (creation is automatic). The Git housekeeping is made easier using SourceTree, which has great GitFlow support.

--------

I'd love to hear your comments on this set-up, especially how it can be improved. If you want more details on any of the configuration/set-up/workflows/discipline, feel free to give me a shout :)




=Issues I've seen with Jira (and other similar tools)=

**TL;DR:** Jira (and similar tools) is great for keeping track of bugs, and for tracking, coordinating and auditing work. It is a terrible way to communicate and collaborate across a team. Don't use it as a communication tool. Rather speak in-person and then document your shared understanding in a tool like Jira, if such documentation is required.

-------------

There are some common anti-patterns I've seen in organisations that use Jira (and other similar tools). This is what I've experienced in several environments: A team goes into Backlog Refinement and/or Sprint Planning and the Product Owner (or whomever is responsible for documenting requirements) projects Jira onto the screen in the boardroom. One by one, each work-item is opened individually and the PO reads through what he or she has written. There's a little bit of discussion, the delivery team decides they're ready to play planning poker, they do so and provide an estimate for the work-item, which is captured, and then they move on to the next work-item.

Instead of having a conversation about what problem we're trying to solve and what outcome we want to achieve, what often happens is everyone just reads what's been written down. Yes, there is some discussion and a few questions, but fundamentally the conversation is framed (and limited) by what the PO had written down previously (however long ago that was). "We don't need a conversation because all you need to know is in Jira, just read it."

Because there is a lot of content, and because the PO clearly took a lot of time and effort to write all of this content, there is a tendency to avoid asking difficult question. "It must be the correct solution, right? The PO must have thought of everything, right?" How likely is the PO to be open to suggestions around solving the problem in a different way? (This is true for everyone, not just POs. Programmers are notorious for being attached to previous work.)

The opportunities for and likelihood of achieving **shared understanding** in this scenario are severely diminished. "There is so much written down, 'communication' must have taken place, right? We all understand what we're trying to achieve, right?" The likelihood of coming up with a good solution to the problem is also severely diminished.

What typically happens is during development of the feature, there will be multiple ad-hoc face-to-face conversations between the delivery team and the PO (assuming the PO is available to the delivery team), when it is discovered that the written content in Jira is deficient or defective in some way. 

What would happen if instead of the PO creating all the requirements documentation and then passing it to the delivery team, the parties had a real conversation, communicated effectively and gained shared understanding. If it is necessary to document this shared understanding, it can *then* be stored with a tool like Jira. This mitigates a lot of the pitfalls outlined above. I do also think tools like Jira can be very useful for attaching artifacts to work items, like screenshots, designs, wireframes etc.

Another big problem with Jira and similar tools is *tool enslavement*. Instead of making the tool work for us, we begin to work for the tool. I've seen much time and effort wasted through configuring and troubleshooting things like Jira workflows. I've seen things like Team A's Sprint being closed because Team B's Sprint was correctly closed, and the Sprints happened to have the same name (based on the date). Guess how much fun that was to resolve. 

In conclusion, Jira was originally created as a bug/work tracking tool, and its best use is as a tool to plan, coordinate and audit work, **not** as a communication medium. If you need to document shard understanding, or what work was done when by whom, experiment with capturing this information post-fact, instead of up-front.

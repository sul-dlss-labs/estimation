# Work Estimation Record Template

## Description

### EDITME: a short title clearly expressing the work for which an estimation was requested

* Requested By: **the work requester's name**
* Estimate requested: **(date)**
* Reason: **the rationale for how the estimate will be used/valued**

Add enough information here to contextualize any details given below, and/or links to an ADR, a document with more info, etc.

## Scope Assumptions / Constraints

Document scoping assumptions made and constraints given while producing the estimate. Surface these explicitly to ensure all parties have a shared understanding or what is included within, or without, the scope of the work.

### Assumptions

Assumptions in order to proceed with an approach to the work. Examples:
- if you're going to be using AWS, management will approve the $$.
- you can put information X in a config file (assume it is not considered sensitive and it won't change often)
- new technology X works in a certain way (that you don't have time to confirm, but the documentation is unclear)
- VM provisioning (call out that it is not included in the estimate)
- developers already know technologies (specify, e.g. javascript, React, Rails, terraform, whatever)

### Out of Scope
Closely related work that this estimate does NOT include.  It may or may not be helpful to have "stretch" goals with optional associated estimates. Examples:

- rebuilding the whole index from scratch (as opposed to incremental updates)
- automating a task (plan is to do it manually at first)
- providing a nice-to-have that is closely related (e.g. easy way for user to get list of all members in a group; indexing another field; ...)

## Work To Do

Describe the work in more detail, broken down into chunks of work that help with determining estimate.  Remember to include things like:
- time to learn any new technologies (at least to the MVP level), e.g. terraform, new language, docker, rails ...
- time to configure laptops if non-trivial (e.g. aws credentials and so on)
- each step of the work to be done

## Risks / Challenges / External Dependencies

Write up potential risks, challenges, or external dependencies that could significantly affect the produced estimate.

Examples of risk could include:

* Novel technologies
* APIs outside of our control

Examples of external dependencies could include:

* Stakeholders outside of your team, within DLSS, SUL, or Stanford University;
* Operations needs
* Open-source community review, approval, or interactions

## Open Questions

A list of questions that were not answered, or answerable, by the team producing the estimate. Answers to these questions could significantly alter the estimate - indicate that when possible.  (e.g. "will this be on AWS?  If so, we will need to figure out a way to XYZ and that could add significantly to the estimate")

## Estimation Contributors

Estimates are of higher quality when multiple parties participate. List here the people who contributed to the estimation:

* A
* List
* Of
* Contributors

The team that would likely do the work should ideally be the same people providing the estimate, but we acknowledge that this is not always the case so it is not assumed here that the contributors above are the people who would be doing the work being estimated.

## Time Spent Producing Estimate

Characterize the time spent producing the estimate. This is factored into the confidence level.

## Confidence Level

Express as a percentage, or range of percentages, the estimating team's overall confidence in the estimate.

## Estimate Range

This is the amount of time estimated for the above team to tackle the work as described. The estimate should be expressed as a range between two orders of magnitude, chosen from the below values, for a given number of team members at a given allocation (with the understanding that 100% of a DLSS engineer's time is roughly 75% of their "contact time," due to competing priorities and time spent in meetings):

* 1 hour
* 1 day
* 1 week
* 1 month
* 3 months
* 6 months
* 9 months
* 1 year
* \> 1 year

Examples:
* Between 1 hour and 1 week for 100% contact time of 2 engineers.
* 3-9 months for a team of 4 engineers, each devoting 75% of his/her/their contact time.

## Results _(conditional on work being undertaken, added afterwards)_

If the project was pursued in some form, use this section to give a brief description of how things went, and where they deviated from the estimate. Indicate how long the work actually took, who the contributors were if they differed from the contributors to the estimate, and a sentence or two about how scope differed from the scope assumptions in the doc. Then just link to the repo(s) for the project, which should provide lots more detail via commit and issue histories.

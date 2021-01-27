# Work Estimation Record 0007

## Description

### Integrating Profiles/SUL-Pub with ORCID and other integrations in support of Open Access Policy

* Requested By: Zach Chandler (Dean of Research office), Tom Cramer, Vivian Wong
* Estimate requested: ~February 2021, some part of the work to be completed by August 2021
* Reason: to be used for planning/scoping purposes and for communication to stakeholders about what may be possible by August 2021

At a high level, the request is to integrate Profiles with ORCID, which from our perpsective means
exporting citations from sul-pub to ORCID (via their API), and importing citations from ORCID back to sul-pub,
while not creating duplicates in either direction.

We also considering other related items, such as using ORCIDs in harvesting from Web of Science queries.

### Links

(all team members may not have access to this):

* [Google doc](https://docs.google.com/document/d/1Di6W7TSZQ3YDxL6_1Rd6-hopJDT83HlGcDHu4UOGqJY) describing all use cases, including those not in scope for SUL

(all team members should have access to these):

* [Google doc](https://docs.google.com/document/d/1BYezfFlkoAaKzdiTMUBdHE6zTmdKnzVFqslblW0uuO8) created by DLSS describing implications for SUL DLSS
* [Google diagram](https://docs.google.com/presentation/d/163ONdgfQERgwmoEaO4ZqJWrHhVdVxaWwJiTq1aDkrgo) created by DLSS showing possible connections between systems:

## Scope Assumptions / Constraints

### Major tasks

Major tasks, and estimates are in the google planning doc, links below:

* Use cases 2 and 3: export of citations from sul-pub database to ORCID, see [google doc](https://docs.google.com/document/d/1BYezfFlkoAaKzdiTMUBdHE6zTmdKnzVFqslblW0uuO8/edit#heading=h.2mj8fmexfmog)
* Use case 4: import of citstions from ORCID to sul-pub, see [google doc](https://docs.google.com/document/d/1BYezfFlkoAaKzdiTMUBdHE6zTmdKnzVFqslblW0uuO8/edit#heading=h.heuuhjcvv63h)
* Use case 12: use ORCID when harvesting from WoS, see [google doc](https://docs.google.com/document/d/1BYezfFlkoAaKzdiTMUBdHE6zTmdKnzVFqslblW0uuO8/edit#heading=h.et16jryr1lkq)

Note that other tasks that support Open Access, such as connections between SDR and ORCID, and SDR and DataCite/Cross-Ref are NOT considered.
This estimation record and the associated google doc are only concerned with sul-pub/Profiles.

## Risks / Challenges / External Dependencies

Risks:

* Some APIs we need (e.g. fetch ORCID for stanford people, get auth tokens for ORCID API) don't exist yet and our out of our control
* Import/export mechanisms may be high SLA if users' become dependent on them, increasing our support costs
* ORCID and other external API may evolve over time, requiring us to update our code
* Due to large number of external dependencies, integration testing may be time consuming and may fall during other workcycles

External dependencies:

* The Profiles API must be expanded to include ORCID in the user data model
* The Profiles or Stanford Registry API must provide a new endpoint for returning the list of researchers who have linked an ORCID with a SUNET
* The Profiles or Stanford Registry API must provide a new endpoint for return auth tokens and rights (read/write to ORCID Profiles) for all users who have linked their sunet
* We must have a current ORCID membership and have acess to their API
* We must establish the API interfaces with each group so that we can develop concurrently or out of order, but the service will not be complete until all of our dependencies are available

## Open Questions

We need to clearly establish which team is taking on which task.  There are currently three primary Stanford teams identified:

* SUL DLSS
* Profiles/School of Medicine (SoM)
* Stanford Registry

There are dependencies between the teams, mostly we are dependent on the other teams doing tasks that are specific to them.

## Estimation Contributors

* Peter Mangiafico
* Justin Littman
* Vivian Wong

The team that would likely do the work should ideally be the same people providing the estimate, but we acknowledge that this is not always the case so it is not assumed here that the contributors above are the people who would be doing the work being estimated.

## Time Spent Producing Estimate

Peter has spent approximately 3 hours, and Justin about 1 hour as of Jan 26.  There are having two phone calls so far with developers on the Profiles team.

## Confidence Level

50%?  Lots of unknowns.

## Estimate Range

This is the amount of time estimated for the above team to tackle the work as described. The estimate should be expressed as a range between two orders of magnitude, chosen from the below values, for a given number of team members at a given allocation (with the understanding that 100% of a DLSS engineer's time is roughly 75% of their "contact time," due to competing priorities and time spent in meetings):

* 3-4 months, team of 2-3 engineers, each devoting 75% of his/her/their contact time.

## Results

TBD

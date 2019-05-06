# Work Estimation Record 0003

## Description

### Automate the web archiving accessioning workflow

* Requested By: Vivian Wong and Nicholas Taylor
* Estimate requested: 2019-04-04
* Reason: Current web archiving accessinging workflow is entirely manual.

In order to allow for more efficient accessioning of web archives, the current manual process of:

* [Manually reviewing ARGO collections for last crawl status](https://consul.stanford.edu/display/WARC/Assessing+Previous+Crawl+Accessioning+Progress)
* Downloading necessary data into organized paths for was-registrar
* Triggering was-registrar

needs to be automated through replacement of the existing was-registrar system.

## Scope Assumptions / Constraints

[Proposal](https://docs.google.com/document/d/1oLlbtqxotfuCvkaIMmHGagzeGHjN2dt0JhiG_90sNJw/edit#)

Establish a new WAS accessioning application that will be a new rails app, with it's own data store for state information (thus not relying on DOR). We will reuse existing was_registrar code as appropriate.

This does not involve changing the web archiving preassembly workflow.

## Risks / Challenges / External Dependencies

* Lack of staff aware of current web archving functionality
* Lack of staff with ability to test web archiving functionality
* Reliance on WASAPI: as we don't control this external API, changes to the API output and/or availability will introduce unplanned maintenance cycles to the application.

## Open Questions

Should was-registrar be re-written? As currently used, can registration of seeds and crawls be performed directly in Argo? Is was-registrar used for anything else?

## Estimation Contributors

* Justin Littman
* Aaron Collier

## Time Spent Producing Estimate

30 minutes writing estimate from existing proposal.

## Confidence Level

80% - There are very few unknown components (i.e. new 3rd party APIs). We will be using and updating existing technologies.

## Estimate Range

1 month for a full infrastructure team.

## Results _(conditional on work being undertaken, added afterwards)_

If the project was pursued in some form, use this section to give a brief description of how things went, and where they deviated from the estimate. Indicate how long the work actually took, who the contributors were if they differed from the contributors to the estimate, and a sentence or two about how scope differed from the scope assumptions in the doc. Then just link to the repo(s) for the project, which should provide lots more detail via commit and issue histories.

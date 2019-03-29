# Work Estimation Record 0001

## Description

* **WHAT**: A workflow by which a developer can deploy, to the staging or production environment, lambdas or containers
* **WHO**: Aaron Collier and Justin Littman
* **WHEN**: March 28th, 2019
* **WHY**:
  * To make this a parallel workflow to how we interact with on premises resources (i.e. capistrano)
  * To reduce the possibility that staging and production code can be accidentally deployed or rolled back.

## Scope Assumptions / Constraints

* For both RIALTO and DLME:
  * Research and test tools for lambda packaging
  * Research and test tools for lambda deployment
  * Research and test tools for building docker images locally
  * Research and test tools for ECS deployment
  * Operations agreement on final approach
* Establish any necessary architecture decision records (ADRs)
* Update DevOpsDocs

## Risks / Challenges

* Existing approach for deploying infrastructure (terraform) cannot be used in conjunction with the proposed approach for deploying code. For example, will terraform require a lambda resource when creating an API gateway?

## Open Questions

* Can developers write to production lambdas and ecs resources
* While the [Serverless Framework](http://serverless.com) is currently being considered, additional technology decisions need to be researched

## Contributors (Team)

* Aaron Collier
* Justin Littman

## Time Spent

Thirty minutes

## Confidence Level

75% in estimate

## Estimate Range

* 1 week at 75% time for 2 devs
* 2 weeks or more with a smaller commitment. (Note: Just acknowledging that we are currently working on multiple higher priority projects concurrently.)

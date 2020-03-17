# Work Estimation Record 0005

## Description

### Decouple ETDs from Fedora 3

* Requested By: Vivian Wong
* Estimate requested: 2020-03-16
* Reason: The SDR evolution plan calls for decoupling ETDs from Fedora 3.  What are the details of that step.

The ETD project uses the Fedora 3 datastore to hold metadata entered by the depositor and information received from Peoplesoft.  It takes the deposited files and creates an augmented PDF (with the names of the approvers) and deposits this and the original files into the SDR.  Presently this is done across 3 systems (hydra_etd, common-accessioning, dor-services-app).  This process is tracked by the etdSubmitWF in the workflow service and is monitored by the service manager in argo (which depends on dor-indexing-app).

Currrently the ETD system is a bit of an outlier as it writes temporary data (readers, workflow and properties datastreams) into Fedora, and then does not put that information into the Moab in SDR.

## Scope Assumptions / Constraints

Assumptions:

* Only minimal UI changes will be made. We will endeavor to keep the existing depositor/approver GUI unchanged.
* No migration of existing data will need to be made.  We will cut over to an RDBMS in between submission periods.

### Major tasks

* Move cron jobs from common-accessioning to hydra_etd.  This will involve some symphony integration.
  * catalog-status: <https://github.com/sul-dlss/hydra_etd/issues/348>
  * check-marc: <https://github.com/sul-dlss/hydra_etd/issues/347>
  * submit-marc: <https://github.com/sul-dlss/hydra_etd/issues/346>
* Provision redis
* Provision sidekiq workers
* Move other-metadata & start-accession from common-accessioning robots to a background job (sidekiq)
  * <https://github.com/sul-dlss/hydra_etd/issues/348>
* Update deployment tools (capistrano) for managing sidekiq
* Move data stored in properties, workflow, and readers datastreams to an RDBMS
* Create a dashboard in the ETD application that gives the service manager the ability to inspect objects in the database (similar to looking at datastreams in Argo).
* Switch to the SDR deposit API, (currently using files in NFS mount + accssionWF)
* Manual integration testing
* etc

## Risks / Challenges / External Dependencies

Write up potential risks, challenges, or external dependencies that could significantly affect the produced estimate.

* ETD App is not widely understood by development team and this estimate is primarily based on the expertise of a single engineer.

External dependencies could include:

* Need to coordinate changes with the registrar
* Strict change policies around the ETD submission windows.
* Need assistance from DevOps and LibSys regarding data transfer to/from Symphony

## Open Questions

None

## Estimation Contributors

Estimates are of higher quality when multiple parties participate. List here the people who contributed to the estimation:

* Justin Coyne

The team that would likely do the work should ideally be the same people providing the estimate, but we acknowledge that this is not always the case so it is not assumed here that the contributors above are the people who would be doing the work being estimated.

## Time Spent Producing Estimate

2 person hrs

## Confidence Level

Express as a percentage, or range of percentages, the estimating team's overall confidence in the estimate.

80%

## Estimate Range

This is the amount of time estimated for the above team to tackle the work as described. The estimate should be expressed as a range between two orders of magnitude, chosen from the below values, for a given number of team members at a given allocation (with the understanding that 100% of a DLSS engineer's time is roughly 75% of their "contact time," due to competing priorities and time spent in meetings):

* 4-8 weeks for 75% time for 2-3 engineers

## Results

TBD

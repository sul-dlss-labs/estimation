# Work Estimation Record 0005

## Description

### Decouple ETDs from Fedora 3

* Requested By: Vivian Wong
* Estimate requested: 2020-03-16
* Reason: The SDR evolution plan calls for decoupling ETDs from Fedora 3.  What are the details of that step.

The hydra_etd application uses the Fedora 3 datastore to hold metadata entered by the depositor and information received from Peoplesoft.  It takes the deposited files and creates an augmented PDF (with the names of the approvers) and deposits this and the original files into the SDR.  Presently this is done across 3 systems (hydra_etd, common-accessioning, dor-services-app).  This process is tracked by the etdSubmitWF in the workflow service and is monitored by the service manager in argo (which depends on dor-indexing-app).

Currrently the ETD system is a bit of an outlier as it writes temporary data (readers, workflow and properties datastreams) into Fedora, and then does not put that information into the Moab in SDR.

## Scope Assumptions / Constraints

Assumptions:

* Only minimal UI changes will be made. We will endeavor to keep the existing depositor/approver GUI unchanged.
* No migration of existing data will need to be made.  We will cut over to an RDBMS in between submission periods.
* The temporary data does not need to be in Argo, and that a similar system for the service manager to view this data in the hydra_etd system will be sufficient.

### Major tasks

* Move ETD specific cron jobs (all have to do with getting descriptive metadata into our ILS) from common-accessioning to hydra_etd.  This will involve some symphony integration.
  * catalog-status: <https://github.com/sul-dlss/hydra_etd/issues/348>
  * check-marc: <https://github.com/sul-dlss/hydra_etd/issues/347>
  * submit-marc: <https://github.com/sul-dlss/hydra_etd/issues/346>
* Provision redis as a queuing system for background jobs
* Provision sidekiq workers to execute background processing jobs
* Move other-metadata & start-accession from common-accessioning robots to a background job (sidekiq)
  * <https://github.com/sul-dlss/hydra_etd/issues/348>
* Update deployment tools (capistrano) for managing sidekiq
* Move data stored in properties, workflow, and readers datastreams to an RDBMS
* Create a dashboard in the ETD application that gives the service manager the ability to inspect objects in the database. This will provide a capability to the service manager similar to looking at the properties and reader datastreams with Argo. These datastreams are currently persisted in Fedora.
* Switch to the SDR deposit API, (currently using files in NFS mount + accssionWF). See <https://github.com/sul-dlss/sdr-api/issues/135#issuecomment-599008166> and `@jcoyne`'s response.
* Manual integration testing
* etc

## Risks / Challenges / External Dependencies

Write up potential risks, challenges, or external dependencies that could significantly affect the produced estimate.

* ETD App is not widely understood by development team and this estimate is primarily based on the expertise of a single engineer.

External dependencies could include:

* Need to coordinate changes with the registrar
* Need to respect ETD app stability windows around ETD submission deadlines, which restricts when we can make changes to the app.
* Need assistance from DevOps and LibSys regarding data transfer to/from Symphony

## Open Questions

The ETD product owner needs to confirm that access to the "properties" and "readers" data in the ETD app will meet his/her needs if it is removed from Argo. In other words -- what is checked in Argo when an object is initially submitted to ETD app, but is not yet in accessioning.


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

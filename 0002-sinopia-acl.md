# Work Estimation Record 0002

## Description

### Grant permissions to AWS Cognito Sinopia users for their correct groups

* Requested by: Sinopia team (PO Michelle Futornick, TL Jeremy Nelson, Manager Vivian Wong)
* Estimate requested: 2019-04-04
* Reason: realistic estimate of when Sinopia ACL MVP can be completed, in context of other milestone 3 work remaining.

Stanford's part of the LD4P grant includes providing
- a cloud based linked data editor for bibliographic metadata,
- a "profile" editor for "templates" used in the creation of bibliographic metadata
- a cloud based server storing the metadata as well as the profiles/templates.

We call the above "Sinopia".  

The Sinopia server utilizes trellis-ldp, which uses Web Access Control (https://www.w3.org/wiki/WebAccessControl)
to grant users permissions to edit profiles/templates or metadata.  AWS Cognito is used for user authentication and authorization.

A git repo already exists with some of the code to create "Web Access Control" forms of "Access Control Lists", or ACLs: https://github.com/LD4P/sinopia_acl

We are trying to come up with the minimal viable product to appropriately grant Cognito users edit access to the appropriate LDP containers.

## Scope Assumptions / Constraints

__Assumptions__:
- it's okay to keep usernames and groups in .csv file in https://github.com/LD4P/sinopia_acl
  - cognito usernames are reasonably public (they are not email addresses, they do not have passwords, etc.)
  - .csv file will need to be kept up to date (see below - out of scope)
  - each row is a username and a group
    - if a user is in more than one group, they will have a row for each group
  - Michelle and Jeremy verbally agreed 2019-04-04 that .csv file is fine.
- the users with control access for any and all Sinopia groups will be Michelle plus the team of developers
  - this will allow us to keep the .csv simpler and will also allow an easier "default" WebAccessControl resource for a new group
  - Jeremy verbally agreed 2019-04-04
- Trellis does NOT determine missing control permissions block from a parent LDP container;  if there is a WebAccessControl resource for a container, it must be complete.
  - Mike verified this behavior empirically 2019-04-04
- We believe WebAccessControl "append" is implied when "write" access is given.
- Initial numbers of users:  100-150. Unknown eventual number of users, but same order of magnitude
- Admin users is a small number and Cognito userids can be in a config file
- It is relatively easy for developers (Naomi and Mike) to get private AWS credentials and the AWS CLI tool onto their laptops

---
__Work To Do__

(assume by magic, we already have .csv file of usernames and groups)

1. Authenticate/authorize user to make HTTP POST/PUT/PATCH requests to Cognito protected Sinopia server on AWS.
    - write current Cognito access token (as JWT) to a file (PR almost ready)
    - use access token in HTTP GET/PUT/POST/PATCH commands
2. Set up correct admin control access for every group encountered in .csv file
    - get admin users from config file
    - use command line AWS CLI command to get webids for each admin user
    - create appropriate WebAccessControl with
      - control access for all admins
      - read access to world
      - section for edit access, but without any agent webids
3. Get current mapping of Cognito usernames to Cognito webids
    - use command line AWS CLI command to get webids for all Cognito users in app pool and store results in a data structure
    - this method would be called before doing anything requiring a webid
4. Add a Cognito webid to WebAccessControl for a particular LDP container (Sinopia "group")
    - this could be an HTTP PATCH with a single triple, once 2. is done.
5. Read .csv file of usernames and groups and execute 3. for each row
    - call 3. to get webids
    - for each row, translate username to webid and call 4.

---

__Out of Scope (Stretch Goals)__:
- adding a single new user (i.e. without re-running the script for all users in the .csv file)
- adding a new group (i.e. without re-running the script for all groups and users in the .csv file)
- getting usernames (not webids) for a group
- redoing all the WebAccessControl resources in total
- removing a user from a group (other than wiping out all WebAccessControl resources and writing them all anew, based on .csv file)

__Out of Scope__:
- getting all the current active usernames and their groups into the .csv file in the repo (will fall to Michelle to get the initial .csv file ready;  expect updates as PRs by Michelle, with some training by us)
- automated way to keep csv up to date (new users, which groups, remove users, etc.)
- automated way to be notified of new cognito user
- provisioning VM(s) with AWS CLI tool and AWS credentials (https://github.com/LD4P/sinopia/issues/192)


## Risks / Challenges / External Dependencies

* given that AWS CLI tools and private AWS creds are required,
  - we do need the VMs in https://github.com/LD4P/sinopia/issues/192 for this work to be useful in the cloud

* getting the correct usernames and their correct groups into a csv could be a big headache for Michelle and us

* running into some Trellis / AWS / Cognito wrinkle we didn't anticipate (unlikely)
  - we've run curl commands testing interaction with WebAccessControl on dockerized trellis with basic auth on our laptops
  - John and Josh have successfully interacted with Trellis behind Cognito

## Open Questions

(none)

## Estimation Contributors

People who contributed to the estimation:

* Naomi Dushay
* Mike Giarlo
* John Martin

Team expected to do the work:

* Naomi Dushay
* Mike Giarlo
* John Martin (consulting as needed)

## Time Spent Producing Estimate

35 minutes for the 3 of us talking;  45 min for Naomi writing up this WER.

## Confidence Level

85% confident

## Estimate Range

between 1 day and 1 month  (likely 1-2 weeks) with Naomi and Mike spending 100% of their contact time (roughly 50-75% of their total time)

## Results _(conditional on work being undertaken, added afterwards)_

If the project was pursued in some form, use this section to give a brief description of how things went, and where they deviated from the estimate. Indicate how long the work actually took, who the contributors were if they differed from the contributors to the estimate, and a sentence or two about how scope differed from the scope assumptions in the doc. Then just link to the repo(s) for the project, which should provide lots more detail via commit and issue histories.

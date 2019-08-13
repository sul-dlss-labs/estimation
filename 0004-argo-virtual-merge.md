# Work Estimation Record 0004

## Description

### Make Virtual-Merge a bulk action in Argo

Summary: "virtual objects" (ie. objects made up of other SDR objects) are currently created by running the virtual-merge script in dor-utils (<https://github.com/sul-dlss/dor-utils/blob/master/bin/virtual-merge>). Ideally, this functionality would be brought into Argo as a bulk action - though there are likely design and functionality questions to be answered before this is possible.

- Requested by: SDR work Fall 2019 planning team (TL Naomi Dushay, Product advisors: Hannah Frost, Andrew Berger)
- Estimate requested: 2019-08-05
- Reason: realistic estimate of how much effort will be needed to implement virtual collection self-service .

Background - Existing documentation other than the code:

- <https://github.com/sul-dlss/dor-utils/issues/17>
  - <https://github.com/sul-dlss/dor-utils/issues/17#issuecomment-518770583>
- <https://consul.stanford.edu/display/chimera/Virtual+Object+Combinator+I>
- <https://consul.stanford.edu/display/DIGMETADATA/Preparing+and+describing+virtual+objects>
- <https://consul.stanford.edu/display/DIGMETADATA/Virtual+object+and+combinator+FAQ>

## Scope Assumptions / Constraints

__Assumptions__:

- Argo users beyond repo manager should be able to self-service virtual merge
- User could provide a spreadsheet with druid list on each row, if desired, as input.
  - first druid is the "parent" object (or make it separate part of form)
  - the list of druids to follow provides the child objects *in the order in which they should appear in the parent object*
  - all child objects must already be in an accessioned state and not dark or citation-only
  - running the script should completely replace the contentMD for the parent object, not append to it (if not the first time the virtual object has been created)
  - rels-ext for the child objects is updated with an is_constituent_of element pointing to the parent object
  - contentMetadata for the parent object points each resource (from each child object) to external file content
  - Examples:
    - parent "virtual" object: <https://argo.stanford.edu/view/druid:bb258cw1178>
    - sample "child" object of above parent: <https://argo.stanford.edu/view/druid:bd128dk8694>

Current input to the script is as follows:

```sh
bundle exec bin/virtual-merge --e=production druid:cr768rj4665 druid:by372cw6149 druid:vn515vk3705 druid:sh918nq3930 druid:sv576sr3765 druid:pn021qw4383 druid:yn253dq9120 druid:mz593xn2710 druid:jk409zp2668 druid:wn125wt2889
```

Assumptions:

__Work To Do__:

- fix current bug with virtual-merge script: <https://github.com/sul-dlss/dor-utils/issues/17>
- move script to argo
- create async bulk action
  - ActiveJob re-working of virtual-merge script
    - not sure about opening objects as part of script (<https://github.com/sul-dlss/argo/issues/1323#issue-407919335> (Desired Implementation)):
      - note sure open parent object? (what about failures?)
      - open child objects? (what about failures?)
    - do the merge
      - write tests for what were the run and merge methods in the script
    - close child objects?  (what about failures)
    - close the parent object?
    - kick off accessioning for children and parents (if close doesn't do it)
  - UI
    - nascent design <https://github.com/sul-dlss/argo/issues/1323#issuecomment-517491067>
    - add a bulk async button
    - field for parent druid ?
    - easy way to get list of child druids (e.g. a spreadsheet from the stakeholder listing the druid of the virtual composite object in the first column and the child objects in sequence in the following columns)
- what do we do with the output?
  - Bulk Actions provides a way to give the user feedback:
    - success/failure counts in the job list
    - an overall completion status
    - more detailed feedback (a downloadable log file)

- don't create duplicate is_constituent_of relationships if one already exists

__Stretch Goals__:

- use dor-services-app instead of dor-services for any functionality that doesn't live with the virtual-merge script
  - note that dor-utils script calls methods in dor-services (content_metadata_ds.add_virtual_xxx) that should likely live with virtual-merge script

__Out of Scope__:

- new UI for async bulk actions
- touching sync bulk action UI

## Risks / Threats

None identified

## Open Questions

- how much validation should be done first (parent and child object pre-reqs)
- any dor-services functionality that is already in dor-services-app could/should be used from there
- any dor-services functionality for virtual-merge that should be moved to dor-services-app
- any dor-services functionality that is ONLY used by virtual-merge and should be moved there

## Contributors (Team)

- Naomi Dushay
- Justin Littman

## Time Spent

2.5 person hours

## Confidence Level

75%

## Estimate Range

3 days 2 devs - min
1 week 2 devs - best guess
2 weeks 2 devs - if difficult

## Results

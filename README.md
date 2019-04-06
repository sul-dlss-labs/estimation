# Records

- [WER-0000](0000-work-estimation-record.md) - Lightweight work estimation record.
- [WER-0001](0001-cloud-resource-deployment.md) - Deploying lambdas and containers in AWS.

## Process

Requests for work estimation should be written up as new pull requests, based on the [estimation template](template.md). Please follow these two practices in your pull requests:

1. Name new WER files with the `nnnn-brief-summary-of-work.md` format; and
1. Add a link to the new WER to `README.md`

If you feel your PR needs more than one review, include that information in the description section. (And, obviously, assign reviewers if you want particular reviewers.)

Once your pull request has been reviewed, approved, and merged into the `master` branch, GitHub will automatically trigger a Jekyll build and redeploy the site. You should see your changes within 1-2 minutes of the merge.

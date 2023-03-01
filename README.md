# hackmd-meeting-notes-action

An experiment with Github Actions and HackMD.

It contains two reusable workflows:

- [Create](.github/workflows/create-meeting-notes-pr.yml): Opens a PR with a rendered version of your meeting notes template and pushes a copy to your HackMD team.
- [Sync](.github/workflows/sync-meeting-notes-pr.yml): Updates the PR document with the latest contents in HackMD.

You will need to [issue a HackMD team token](https://hackmd.io/@hackmd-api/how-to-issue-an-api-token) and store it as a secret.

Check the `inputs` and `secrets` fields in the `workflow_call` trigger for the [Create](.github/workflows/create-meeting-notes-pr.yml) and [Sync](.github/workflows/sync-meeting-notes-pr.yml)
workflows for more details.

## Setup

You need to create a workflow out of the two actions here: Create and Sync.
In this example:

- The Create workflow is triggered manually via `workflow_dispatch`, but you could have it on a cronjob as well.
- The Sync workflow is triggered by adding a label to the PR, but you could use a PR comment trigger with some authentication, if you want.

See `.github/workflows/use-action.yml` for more details.

## How to use this example

1. Go to "Actions> Create PR for meeting notes" and run a `workflow_dispatch` job.
2. A PR will be created containing the link to the freshly created HackMD document.
3. Edit the HackMD document as much as you want.
4. When you are done, go back to the PR and add the `sync-hackmd-notes` label.
5. Merge!



# Shared workflow library for GCP integration
Reference repo for OIDC authentication

# USAGE

These workflows are meant to be called as a job in a GitHub Actions workflow. Example:

in .github/workflows/<your_workflow>.yml

```yaml
on:
  push:
jobs:
  call-gcp-auth:
    uses: defendable/workflow-library/.github/workflows/google-auth-terraform.yml@main
    with:
      tf_workdir: environments/develop
      environment: develop
    secrets: inherit
```

## Required secrets

The workflow depends on a few setting which are repo / project specific:
- GCP_PROJECT_ID: the project_id of your Google Cloud project to authenticate with
- GCP_SERVICEACCOUNT: the email alias of the Google IAM service account to impersonate as
- GCP_WI_PROVIDER: the full ID of the workload identity provider against which to authenticate to
- GITHUB_PAT: a GitHub token valid for pulling from private repositories in your organization. Used to download Terraform modules.

You can set these as GitHub Actions secrets, either directly at the repository level or as Environment Secrets.

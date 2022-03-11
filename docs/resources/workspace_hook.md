---
layout: "bitbucket"
page_title: "Bitbucket: bitbucket_workspace_hook"
sidebar_current: "docs-bitbucket-resource-workspace-hook"
description: |-
  Provides a Bitbucket Workspace Webhook
---

# bitbucket\_workspace\_hook

Provides a Bitbucket workspace hook resource.

This allows you to manage your webhooks on a workspace.

## Example Usage

```hcl
resource "bitbucket_hook" "deploy_on_push" {
  workspace   = "myteam"
  url         = "https://mywebhookservice.mycompany.com/deploy-on-push"
  description = "Deploy the code via my webhook"

  events = [
    "repo:push",
  ]
}
```

## Argument Reference

The following arguments are supported:

* `workspace` - (Required) The workspace of this repository. Can be you or any team you
  have write access to.
* `url` - (Required) Where to POST to.
* `description` - (Required) The name / description to show in the UI.
* `events` - (Required) The events this webhook is subscribed to. Valid values can be found at [Bitbucket Webhhok Docs](https://developer.atlassian.com/cloud/bitbucket/rest/api-group-repositories/#api-repositories-workspace-repo-slug-hooks-post).

## Import

Hooks can be imported using their `workspace/hook-id` ID, e.g.

```sh
terraform import bitbucket_workspace_hook.hook my-account/hook-id
```
# gitlabci-golang Plugin

This plugin creates Golang GitLab CI workflow.

## Usage

_This plugin depends on an environment variable "GITLAB_TOKEN", which is your GitLab personal access token._

TL;DR: if you are using gitlab.com (instead of a self-hosted GitLab), [click here](https://gitlab.com/-/profile/personal_access_tokens?name=DevStream+Access+token&scopes=api) to create a token for DevStream (the scope contains API only.)

If you are using self-hosted GitLab, refer to the [official doc here](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) for more info.

_Note: when creating the token, make sure you select "API" in the "scopes" section, as DevStream uses GitLab API to add CI workflow files._

Plugin config example:

```yaml
tools:
- name: go-hello-world
  # name of the plugin
  plugin: gitlabci-golang
  # optional; if specified, dtm will make sure the dependency is applied first before handling this tool.
  dependsOn: [ "TOOL1_NAME.TOOL1_PLUGIN", "TOOL2_NAME.TOOL2_PLUGIN" ]
  # options for the plugin
  options:
    # owner/repo; "path with namespace" is only GitLab API's way of saying the same thing; please change the values below.
    pathWithNamespace: YOUR_GITLAB_USERNAME/YOUR_GITLAB_REPO_NAME
    # main branch of the repo (to which branch the plugin will submit the workflows)
    branch: main
```

All parameters are mandatory.

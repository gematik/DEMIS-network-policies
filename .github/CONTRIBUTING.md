# Welcome to the gematik contributing guide 
 
Thank you for investing your time in contributing to our projects!

Read our [Code of Conduct](CODE_OF_CONDUCT.md) to keep our community approachable and respectable.
 
In this guide you will get an overview how you can contribute to our projects by opening an issue, creating, reviewing and merging a pull request.
 
## Reporting a security vulnerability
 
Please do not report vulnerabilities and security incidents as GitHub issues. Please contact us by sending an E-Mail to  [Open Source Program Office](mailto:ospo@gematik.de?subject=[GitHub]%20istio-network-rules) or report them using the contact form at https://fachportal.gematik.de/kontaktformular.
 
## New contributor guide
 
To get an overview of the project, read the [README](./README.md).
 
## Getting started
 
### Issues
 
#### Create a new issue
 
If you spot a problem with the docs, search if an issue already exists.
If a related issue doesn't exist, you can open a new issue.
 
#### Solve an issue
 
Scan through our existing issues to find one that interests you. If you find an issue to work on, you are welcome to open a PR with a fix.
 
### Coding Style
 
gematik projects follow the [google style guide](https://github.com/google/styleguide) conventions. Please follow them when working on your contributions.

### Contributing Guide

New authorization policies for new namespaces, where the new services from the new module are running, should be created by copying the [ekm-template](deployment\helm\policies-authorizations-istio\templates\ekm-template) directory and rename it to the target namespace. 
The included [service-demo Authorization Policy](deployment\helm\policies-authorizations-istio\templates\ekm-template\service-demo-allow-access-from-ingress.yaml) can be used as an example to allow a GET request from the Ingress Gateway to the service.

Rules are defined in form of "<service|namespace>-allow-access-from-<namespace>", indicating that a service or namespace is accessed from other namespaces, such as:

- ingress, the Istio Gateway which allows the incoming traffic from external sources
- idm, the namespace containing all the specific Identity Management Services
- demis, the namespace containing the DEMIS Core Services
- internal, the same namespace where the service that allows traffic is deployed

A new authorization policy **MUST** include the following:

- selector: The selector must target exacly one specific service. For every new service, there should be at least one dedicated authorization policy. 
- methods: For HTTP requests, include the supported HTTP methods.
- paths: For HTTP requests, include the API endpoints for the supported methods.
- role-claims: If the selected service is an outbound service, include a role claim: "request.auth.claims[realm_access][roles]"

The "From-Section" in the Authorization Policies must include the principals of the specific services that initiate the connection. IP addresses or similar mechanisms are deprecated and will no longer be supported.

### Commit your update

Commit the changes once you are happy with them.

### Pull Request Process

- When you're finished with the changes, create a pull request, also known as a PR.
- Fill the pull request template so that we can review your PR. This template helps reviewers to understand your changes as well as the purpose of your pull request.
- Don't forget to [link the PR to the issue](https://docs.github.com/en/issues/tracking-your-work-with-issues/linking-a-pull-request-to-an-issue) if you are solving one.
- Update the [README.md](../README.md), the documentation and the [ReleaseNotes.md](../ReleaseNotes.md) with all details to document the changes made by this PR.
- Increase the version numbers in any necessary files and the [readme](../README.md) to the new version that this
  Pull Request would represent. The versioning scheme we use is [SemVer](http://semver.org/).
- Once you submit your PR, a project team member will review your proposal. We may ask questions or request additional information.
- We may ask for changes to be made before a PR can be merged, either using [suggested changes](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/incorporating-feedback-in-your-pull-request) or pull request comments. You can apply suggested changes directly through the UI. You can make any other changes in your fork, then commit them to your branch.
- As you update your PR and apply changes, mark each conversation as [resolved](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/commenting-on-a-pull-request#resolving-conversations).
- You may merge the Pull Request in once you have the sign-off of two other developers, or if you do not have permission to do that, you may request the second reviewer to merge it for you.

### Your PR is merged!

Congratulations :tada: :tada: The gematik team thanks you :sparkles:.

Once your PR is merged, your contributions will be publicly visible on the [gematik github page](https://github.com/gematik/). 

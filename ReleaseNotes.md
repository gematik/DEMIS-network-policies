<div style="text-align:right"><img src="https://raw.githubusercontent.com/gematik/gematik.github.io/master/Gematik_Logo_Flag_With_Background.png" width="250" height="47" alt="gematik GmbH Logo"/> <br/> </div> <br/> 
 
# Release notes
## Release 2.5.0
- removed kubernetes version constraints from chart
- added otlp gateway resources to mesh rules
- added SNI configuration for S3 destination rule
- fixed link to DEMIS-Wissensdatenbank

## Release 2.4.0
- reomved permissive mTLS for pgbouncer, postgres and redis

## Release 2.3.0
- added support for custom header tags definition for telemetry data
- default header tags are: `content-type`, `x-fhir-package-version`, `x-fhir-package`, `x-api-version`

## Release 2.2.1
- update jira-function in release pipeline
- remove feature flag 'newApiEndpoints'

## Release 2.2.0
- add Support for New API Endpoints, change redirect Portal requests 

## Release 2.1.1
- added new EnvoyFilter for serving an informational html page on test stage with multiple demis instances on different context paths
- added making peerAuthentication for Postgres and PgBouncer controllable

## Release 1.1.0
- new structure for modalisation 

## Release 1.0.3
- added new root redirect
- changed TLS/mTLS Certificates for ISTIO

## Release 1.0.2
- removed previously added IP Filter

## Release 1.0.1
- added New Domains for demis-gateway
- changed TLS/mTLS Certificates for ISTIO
- removed secrets from Helm Chart

## Release 1.0.0
- Initial Release

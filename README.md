<div style="text-align:right"><img src="https://raw.githubusercontent.com/gematik/gematik.github.io/master/Gematik_Logo_Flag_With_Background.png" width="250" height="47" alt="gematik GmbH Logo"/> <br/> </div> <br/>

# istio-network-rules

## About The Project
Helm Chart defining the Istio Network rules to services in a DEMIS cluster.

The Helm Chart supports the definition of network rules and creates the following Kubernetes resources:

- An `Gateway` defines the demis-gateway for managing incoming traffic; Selector: Uses the Istio ingress controller; Servers: Configures HTTPS on port 443 with TLS settings and optional HTTP on port 80, specifying associated hosts.
- A `EnvoyFilter` configures a filter for the ingress gateway (ingressgateway) in the Istio system; Workload Selector: Targets the ingress gateway by label; Config Patches: Inserts a Lua script into the HTTP filter chain, which processes requests to a specific endpoint and manages authentication via Keycloak.
- A `PeerAuthentication` defines the request authentication methods supported by a workload and configures mutual TLS (mTLS) settings for workloads across the mesh.
- A `VirtualService`Specifies the gateway (demis-gateway) handling incoming traffic; Hosts: Lists applicable domains for routing rules; HTTP Rules: Match conditions check if the gateway-request header is false and match specific URIs, while redirect actions send requests to /portal/ based on those URIs.
- A `AuthorizationPolicy` defines rules that control access to workloads by specifying allowed source IPs for requests, enhancing security by permitting only requests from specific clients to the ingress gateway.

### Release Notes
See [ReleaseNotes](ReleaseNotes.md) for all information regarding the (newest) releases.


## Getting Started
### Required Tools
If you want to use this chart directly from sources (for development purposese), you need the following tools:

* git
* helm (3.11+)

### Working with Helm
You can inspect the Helm Chart by issuing the command `helm template` as follows:

```sh
helm template istio-network-rules ./deployment/helm/network-rules-istio
```

It will print out the Helm Chart with the default values.

### Using the Chart
It can also be deployed on Kubernetes by using the Helm Chart defined in the folder ./deployment/helm:

```sh
helm upgrade --install network-rules-istio ./deployment/helm/network-rules-istio
```

## Security Policy
If you want to see the security policy, please check our [SECURITY.md](.github/SECURITY.md).

## Contributing
If you want to contribute, please check our [CONTRIBUTING.md](.github/CONTRIBUTING.md).

## License
Copyright 2024-2025 gematik GmbH

EUROPEAN UNION PUBLIC LICENCE v. 1.2

EUPL © the European Union 2007, 2016

See the [LICENSE](./LICENSE.md) for the specific language governing permissions and limitations under the License

## Additional Notes and Disclaimer from gematik GmbH

1. Copyright notice: Each published work result is accompanied by an explicit statement of the license conditions for use. These are regularly typical conditions in connection with open source or free software. Programs described/provided/linked here are free software, unless otherwise stated.
2. Permission notice: Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
    1. The copyright notice (Item 1) and the permission notice (Item 2) shall be included in all copies or substantial portions of the Software.
    2. The software is provided "as is" without warranty of any kind, either express or implied, including, but not limited to, the warranties of fitness for a particular purpose, merchantability, and/or non-infringement. The authors or copyright holders shall not be liable in any manner whatsoever for any damages or other claims arising from, out of or in connection with the software or the use or other dealings with the software, whether in an action of contract, tort, or otherwise.
    3. We take open source license compliance very seriously. We are always striving to achieve compliance at all times and to improve our processes. If you find any issues or have any suggestions or comments, or if you see any other ways in which we can improve, please reach out to: ospo@gematik.de
3. Please note: Parts of this code may have been generated using AI-supported technology. Please take this into account, especially when troubleshooting, for security analyses and possible adjustments.

## Contact
E-Mail to [DEMIS Entwicklung](mailto:demis-entwicklung@gematik.de?subject=[GitHub]%20Istio-Network-Rules)
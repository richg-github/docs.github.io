# Istio Support for Containers

Alert Logic supports Istio for containers, which can virtually tap Istio-encrypted container-to-container traffic.

The Alert Logic Agent Container now includes an Istio detector to inspect the traffic between your containers. If you already have the agent container installed, no further action is necessary. If you do not have the agent container installed yet, go to  [Install the Alert Logic Agent Container](../../prepare/alert-logic-agent-container.md)

If you have a container environment but do not use Istio, the detector does not affect your environments.

## Requirements

Alert Logic supports detection for Istio versions 1.4 and above.

## Technical description

The IDS agent detects Kubernetes pods running Istio 1.4 and above in mutual TLS mode, and tries to capture a clear-text (rather than encrypted) copy of the application and control-plane traffic where possible.

## Configure Istio for optimal performance

The automatic update to the agent allows Alert Logic to see traffic and generate incidents. These incidents are limited with only the Kubernetes pod IP address in them. This helps you pinpoint the specific container but not the attack source.

To address these limits, configure Istio to provide Alert Logic with an X-Forwarded-For header with a meaningful originator address.

Istio’s Envoy proxies and the load balancers (such as AWS ELB) in front of the ingress gateway must be configured to run in HTTP(S) mode and provide X-Forwarded-For headers for HTTP traffic. This configuration allows  meaningful events/incidents to be generated from Istio pods.

For example, run the commands below on an AWS deployment:

| 1 | $ istioctl manifest <apply|generate> -f <(echo 'apiVersion: install.istio.io/v1alpha2 |
| 2 | kind: IstioControlPlane |
| 3 | spec: |
| 4 | values: |
| 5 | gateways: |
| 6 | istio-ingressgateway: |
| 7 | serviceAnnotations: |
| 8 | "service.beta.kubernetes.io/aws-load-balancer-backend-protocol": <http|https> |
| 9 | pilot: |
| 10 | env: |
| 11 | PILOT_SIDECAR_USE_REMOTE_ADDRESS: true |
| 12 | ') |

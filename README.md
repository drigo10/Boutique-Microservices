
# Working with Google Kubernetes Engine (Autopilot)

This is a follow along step-by-step guide to:
1. Create a GKE Autopilot - Cluster
2. Deploy the Google Microservices Project [Online Boutique](https://github.com/GoogleCloudPlatform/microservices-demo/tree/main#readme)
3. Deploy the Datadog Agent via Helm.


## Pre-Requisites:
1. Have access to the [Google Cloud Platform](https://console.cloud.google.com/)
2. Install [Google Cloud CLI](https://cloud.google.com/sdk/docs/install-sdk)

## Create a GKE Autopilot Cluster

First we will create a VPC in order to provide network fucntionality to our cluster
```console
gcloud compute networks create NETWORK \
    --subnet-mode=auto \
    --bgp-routing-mode=DYNAMIC_ROUTING_MODE \
    --mtu=MTU
```
Now we can continue by creating our cluster
```console
gcloud container --project "PROJECT_NAME" \
clusters create-auto "CLUSTER_NAME" --region "REGION" \
--release-channel "RELEASE_CHANNEL" \
--network "VPC" \
--subnetwork "SUBNET" \
--cluster-ipv4-cidr "/17"
```

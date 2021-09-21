# Alloy

To make bare metals managed and work together

We will walk you through the steps to create a production grade GPU cluster for scientific computing placed in data center with all the open source tools from ground up.

We assume you have an server room or a data center rental, with some empty racks. External network, electricity and cooling are ready.

## Target

- For a group of AI researchers:
  - should be easy to experiment their ides, model training/tuning.
  - resource should be fairly distributed.
  - data should be safely stored
  - performance (IO, computing)
- For maintainer
  - should be able to have a over look of the whole cluster
  - need to be notified when there is any hardware issue
  - should be able to resolve most of the issue remotely
  - automation
  - extensible
- For Management
  - low cost
  - no exception

## Metrics

- Capacity
- Speed
- Redundancy
- Cost

## Design

### Physical

[Physical-Design](Physical-Design.md)

### Cluster Roles and Topo

### Software Stack Selection

## Experiment

## Deployment

## Benchmarking

## Migration

## References

- [Kubespray](https://github.com/kubernetes-sigs/kubespray) A production grade k8s deployment tool, works with ansible
- [Kubernetes Cluster Deployment on InfiniBand Fabric with RDMA Shared Device Plugin. ](https://docs.mellanox.com/pages/releaseview.action?pageId=18481842)


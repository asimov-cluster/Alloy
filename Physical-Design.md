## Floor Planing

## Network

Network is much more fundamental then other components, and it's usually not changed for a long period of time. So the network's performance, robustness, redundancy, and future-proofness is super important.

### Topo

spine-leaf is pretty popular, the down side is it requires a lots of wires, maybe an issue when the cluster is getting a lots of nodes.

### Device Selection

- Networks for different purpose

  - East-west high speed data exchange
    used for server to server, server to storage communication, which focus on:

    - high speed (100G and above)
    - low latency
    - protocol support (ethernet, rdma)
  
  - In band manage network
    this is for ssh management/internet access/other network util of the nodes.

  - out of band manage network
    this is usually for IPMI, PDU network.

#### East-west high speed data exchange network

  - IB or ethernet?
    IB feels phasing out these days, especially when ethernet is getting 400G speed.
    But choosing between them is still not easy, several questions to be answered:

    1. RDMA
        - Researchers are not big fans of RDMA. Usually RDMA not organically supported by popular DL frameworks(tensorflow, pyTorch, etc.), they have to work with a lot of customized operators and libs, like [tf netowrk](https://github.com/tensorflow/networking). So, eth is not really a blocker for now.
        - RDMA can be supported via eth. Ethernet's RDMA mode is called RoCE. So, eth is not a blocker theoretically.
        - gRPC (which is used by tensorflow as data communication tool) is still using socket as transport layer interface, it would be ideal if RDMA is supported at gRPC layer.
        - For storage solution, Beegfs natively supports IB and RoCE as transportation layer. so Ethernet is not a blocker in here.
    1. Since IB is part of Nvidia, are dgx series servers be able to work well with eth? 
      
        turned out dgx server can be configured with eth 200G NIC, so, to support dgx is not an issue.
    1. How about our legacy 56G IB switches?
      
        TBD
  - Speed grade
    
    The fastest eth switch now goes to 400G (Cisco, Nvidia), main stream are not faster than 200G.

    IB switch's speed can also come to 400G of port speed (Nvidia NDR 400G)

    On the other hand, PCIe 4.0 x 16 tops at 31.5G, PCIe 6.0 x 16 tops at 126G, so for leaf node, 200G is good enough.


  - Spine switch model
    
    TBD

  - Leaf switch model
    
    TBD
## Rack planing

## Node
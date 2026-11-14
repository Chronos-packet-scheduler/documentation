# documentation

This repository holds official documentation for Chronos - dynamic load balancer and firewall based on eBPF/XDP for QUIC transport in IBN (Intent Based Networking) manner

## Literature & Reference Materials (eBPF/XDP + QUIC + IBN + LDT)

### 1. QUIC, eBPF/XDP, and Connection ID Load Balancing
* [The eXpress Data Path: Fast Programmable Packet Processing in the Operating System Kernel (ACM CoNEXT 2018)](https://dl.acm.org/doi/10.1145/3281411.3281443) — the foundational academic paper describing XDP architecture inside the Linux kernel.
* [eQUIC Gateway: Maximizing QUIC Throughput using a Gateway Service based on eBPF + XDP (IEEE / ResearchGate)](https://www.researchgate.net/publication/356488321_eQUIC_Gateway_Maximizing_QUIC_Throughput_using_a_Gateway_Service_based_on_eBPF_XDP) — user-space offloading and QUIC traffic management at the XDP layer.
* [Open-sourcing Katran, a scalable network load balancer (Meta Engineering Blog)](https://engineering.fb.com/2018/05/22/open-source/open-sourcing-katran-a-scalable-network-load-balancer/) — architectural overview of Meta's L4 load balancer.
* [Meta Katran – QUIC_VIP Documentation (GitHub)](https://github.com/facebookincubator/katran/blob/main/QUIC_VIP.md) — concrete mechanism for routing QUIC traffic via unencrypted Connection IDs without TLS termination.
* [The Road to QUIC (Cloudflare Blog)](https://blog.cloudflare.com/the-road-to-quic/) — practical engineering challenges with connection migration and amplification/DDoS protection.
* [Cilium: BPF and XDP Reference Guide (Isovalent/Cilium Docs)](https://docs.cilium.io/en/stable/reference-guides/bpf/index.html) — official reference guide covering XDP, eBPF maps, and EDT/BBR pacing at the `tc` layer.

### 2. Intent-Based Networking (IBN) + LLM & Intent Validation
* [Intent-Based Management of Next-Generation Networks: an LLM-centric Approach (IEEE, 2024)](https://ieeexplore.ieee.org/document/10574896) — LLM-driven intent life-cycle management featuring structural validation and a *Human-in-the-Loop* approval workflow.
* [LLM-enabled Intent-driven Service Configuration for Next-Generation Networks (arXiv / EURECOM, 2025)](https://arxiv.org/abs/2501.14361) — three-stage validation pipeline (syntactic, semantic, and correlational) for LLM outputs prior to network deployment.
* [RFC 9315: Intent-Based Networking – Concepts and Definitions (IETF)](https://datatracker.ietf.org/doc/html/rfc9315) — official IETF standard defining IBN terminology (*Closed-Loop Assurance*, intent vs. policy).

### 3. Large Deviations Theory (LDT) in Network Queues
* [Effective Bandwidths of General Markovian Traffic Sources and Admission Control of High Speed Networks (IEEE/ACM Transactions on Networking)](https://ieeexplore.ieee.org/document/251892) — seminal paper underlying buffer overflow probability estimation $P(Q > B) \approx \kappa \cdot e^{-\theta B}$.
* [Large Deviations for Performance Analysis: Queues, Communication and Computing (Shwartz & Weiss – Springer / Google Books)](https://link.springer.com/book/9780412063114) — comprehensive mathematical reference on applying LDT to queueing networks (justifying in-kernel Look-Up Tables).

### 4. IETF Standards for QUIC Manageability & Load Balancing
* [RFC 9312: Manageability of the QUIC Transport Protocol (IETF)](https://datatracker.ietf.org/doc/html/rfc9312) — details what middleboxes (firewalls, load balancers) can observe in QUIC traffic and how CID-based tracking operates.
* [draft-ietf-quic-load-balancers: QUIC-LB – Generating Routable QUIC Connection IDs (IETF)](https://datatracker.ietf.org/doc/draft-ietf-quic-load-balancers/) — specification for encoding server/node routing identifiers directly within Connection ID bits for stateless L4 load balancing.
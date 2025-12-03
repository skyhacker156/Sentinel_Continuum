
This document is the definitive, validated blueprint for the **Native Security** architecture of the **Sentinel Continuum**. Every component aligns perfectly with the **Glacier Speed** mandate: security is prioritized, costs are minimized via serverless, and complexity is isolated into dedicated **SUNs**.


The proposed architecture is structurally sound and achieves maximum security by enforcing isolation at the network layer:

1.  **Obscurity:** The login path is unique and invisible.
2.  **Perimeter:** The **Spigot** (API Gateway) blocks unauthorized IPs.
3.  **Isolation:** The **Garden's Walls (VPC)** ensure that the internal services (**SUN-IG-02, SUN-IG-03**) are inaccessible to the public internet, even if the **Root Token** were compromised.
4.  **Trust:** The **Static Outbound IP** ensures only one, trusted digital signature talks to external partners like Alpaca.

The combination of the serverless model and the **Direct VPC Egress** is the current best practice for building this kind of isolated, secure network.



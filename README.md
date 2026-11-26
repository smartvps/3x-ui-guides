
# 3x-ui Guides — Xray Core, VLESS, WireGuard & Ubuntu VPS

**Practical documentation for installing, configuring, and managing 3x-ui on Ubuntu VPS and Linux servers.**

This repository covers 3x-ui fundamentals, Xray Core, VLESS with REALITY, WireGuard configuration, subscription links, security practices, and comparisons with other server management panels.

Maintained as part of the [SmartVDS](https://smartvds.org/) technical knowledge base.

📖 **[Complete 3x-ui Documentation on GitBook](https://smartvds.gitbook.io/smartvds-docs/3x-ui-guide)**

---

## What Is 3x-ui?

3x-ui is an open-source web management panel for Xray Core.

It provides a graphical interface for configuring network connections, managing clients, monitoring traffic, and administering supported Xray protocols.

Instead of manually editing complex Xray configuration files, administrators can perform many common management tasks through a browser.

### Main Features

- Web-based Xray Core management
- VLESS, VMess, Trojan, and Shadowsocks configuration
- Supported WireGuard configuration options
- Client and inbound management
- Traffic limits and expiration settings
- Connection links and QR codes
- Subscription link generation
- Routing and transport configuration
- Traffic statistics and logging
- Backup and restore capabilities

Available features depend on the installed 3x-ui and Xray Core versions.

**Detailed overview:**  
[What Is 3x-ui? Features, Protocols, and Use Cases](https://smartvds.org/hosting-basics/3x-ui-panel/)

---

## 3x-ui Installation and Configuration Guides

### 1. Install 3x-ui on Ubuntu Server

Deploying 3x-ui starts with a Linux VPS or dedicated server running a compatible Ubuntu version.

The installation process typically includes preparing the operating system, obtaining the installer from the project's official repository, configuring the management panel, and securing administrative access.

Important considerations:

- Ubuntu system requirements
- SSH and administrator access
- Panel installation and initial configuration
- Firewall and network settings
- Administrative credentials
- HTTPS and management-panel security
- Service management and troubleshooting

**Step-by-step tutorial:**  
[How to Install 3x-ui on Ubuntu Server](https://smartvds.org/software-setup-guides/install-3x-ui-ubuntu-server/)

### 2. Configure VLESS with REALITY

VLESS is a proxy protocol supported by Xray Core.

It can be combined with different transports and security configurations, including REALITY.

A common deployment involves:

- Creating a VLESS inbound
- Configuring the listening port
- Selecting a compatible transport
- Configuring REALITY security settings
- Adding client identifiers
- Generating connection details
- Testing connectivity with a compatible client

VLESS, the transport layer, and REALITY serve different functions. They must be configured consistently on the server and client.

**Configuration tutorial:**  
[How to Configure VLESS in 3x-ui on Ubuntu Server](https://smartvds.org/software-setup-guides/configure-vless-3x-ui-ubuntu-server/)

### 3. Configure WireGuard with 3x-ui

3x-ui also provides WireGuard-related configuration capabilities.

WireGuard is a modern encrypted VPN protocol using public-key cryptography and UDP.

Administrators can explore the panel's supported WireGuard configuration workflow and generate connection settings for compatible clients.

Keep in mind that WireGuard through Xray/3x-ui is not necessarily the same deployment model as a standalone Linux WireGuard interface.

**Configuration tutorial:**  
[How to Configure WireGuard in 3x-ui on Ubuntu Server](https://smartvds.org/software-setup-guides/configure-wireguard-3x-ui-ubuntu-server/)

For native WireGuard installation methods, see the [SmartVDS WireGuard Guide](https://smartvds.gitbook.io/smartvds-docs/wireguard-guide).

### 4. Configure Subscription Links

Subscription links allow compatible client applications to retrieve connection configurations from a managed endpoint.

They are especially useful when maintaining multiple client profiles.

The configuration involves:

- Enabling subscription functionality
- Configuring the subscription endpoint
- Setting the correct public address and port
- Securing the connection with HTTPS
- Managing supported subscription formats
- Verifying client compatibility
- Testing updates and connectivity

Subscription URLs may provide access to connection credentials and should be treated as sensitive information.

**Configuration tutorial:**  
[How to Configure 3x-ui Subscription Links for VLESS, VMess and Trojan](https://smartvds.org/software-setup-guides/configure-3x-ui-subscription-links/)

---

## Understanding Protocols, Transports, and Security

3x-ui is a management panel, not a VPN protocol.

It is important to distinguish the different components used in a connection.

| Component | Examples | Purpose |
|---|---|---|
| Management panel | 3x-ui, Marzban | Configure and administer services |
| Server core | Xray Core | Process connections and routing |
| Proxy protocol | VLESS, VMess, Trojan | Define compatible proxy connections |
| Transport | TCP, WebSocket, gRPC | Carry connection traffic |
| Security layer | TLS, REALITY | Provide connection security |
| VPN protocol | WireGuard, OpenVPN | Establish encrypted network tunnels |

For example, a VLESS + TCP + REALITY configuration combines a proxy protocol, a transport, and a security layer.

The management panel helps configure these components but does not replace them.

---

## 3x-ui vs Marzban

3x-ui and Marzban are both management solutions associated with Xray Core.

However, they emphasize different administration workflows.

| Feature | 3x-ui | Marzban |
|---|---|---|
| Primary role | Xray configuration and client management | Centralized Xray user management |
| Web dashboard | Yes | Yes |
| Client management | Yes | Yes |
| Subscription support | Yes | Yes |
| Traffic and expiration controls | Yes | Yes |
| Xray configuration | Flexible inbound and routing controls | Managed through its own configuration model |
| Common use case | Managing varied Xray configurations | Managing users, subscriptions, and supported multi-node deployments |

Neither panel is universally better.

3x-ui can be convenient for administrators who want direct control over varied Xray configurations.

Marzban may be more suitable for workflows focused on user accounts, subscriptions, and supported node management.

The right choice depends on current features, deployment requirements, and maintenance preferences.

**Detailed comparison:**  
[Marzban vs 3x-ui: Which Xray Panel Should You Choose?](https://smartvds.org/hosting-basics/marzban-vs-3x-ui/)

For additional Marzban documentation, visit the [Marzban Guide](https://smartvds.gitbook.io/smartvds-docs/marzban-guide).

---

## Choosing a VPN Protocol or Server Panel

Not every private networking solution requires an Xray management panel.

Some users need a traditional VPN tunnel, while others require a proxy-based connection with flexible transports.

Common options include:

**WireGuard**  
A lightweight VPN protocol suitable for personal VPNs, remote access, and private networking.

**OpenVPN**  
A mature VPN solution offering flexible authentication and UDP/TCP transport options.

**VLESS**  
An Xray-compatible proxy protocol supporting different transports and security configurations.

**Trojan**  
A proxy protocol commonly deployed with TLS-based connections.

**Shadowsocks**  
An encrypted proxy solution suitable for supported applications and client configurations.

**3x-ui and Marzban**  
Management panels for administering compatible Xray-based services.

These technologies are not interchangeable. They solve different networking and management problems.

**Detailed comparison:**  
[Best VPN Protocols and Server Panels Compared](https://smartvds.org/hosting-basics/best-vpn-protocols-server-panels/)

---

## Security Recommendations

A 3x-ui server should be secured before being used in production.

Recommended practices include:

- [ ] Keep Ubuntu and Xray Core updated.
- [ ] Use strong administrative credentials.
- [ ] Protect the management panel with HTTPS.
- [ ] Restrict administrative access where possible.
- [ ] Configure firewall rules carefully.
- [ ] Avoid exposing unnecessary services.
- [ ] Keep private keys and connection credentials secure.
- [ ] Protect subscription URLs from unauthorized access.
- [ ] Maintain configuration backups.
- [ ] Review connected clients and remove unused access.
- [ ] Monitor logs and unexpected traffic.
- [ ] Test configuration changes before distributing updated profiles.

Never publish private keys, administrative passwords, or sensitive subscription URLs in a public repository.

---

## Common Configuration Problems

### Cannot Access the 3x-ui Dashboard

Check whether the panel service is running, the correct management port is configured, and firewall rules permit access.

Also verify HTTPS settings and the configured access path.

### VLESS Client Cannot Connect

Review the server endpoint, client UUID, inbound port, transport settings, REALITY or TLS parameters, and client compatibility.

### Subscription Link Does Not Work

Verify the subscription endpoint, URL path, HTTPS certificate, and supported client subscription format.

### Connection Works but Websites Do Not Open

Investigate DNS, routing, outbound configuration, and the client application's proxy or TUN settings.

### WireGuard Connection Has No Traffic

Check peer configuration, AllowedIPs, UDP connectivity, forwarding, and the specific behavior of the selected WireGuard implementation.

---

## All SmartVDS 3x-ui Tutorials

| Topic | Guide |
|---|---|
| 3x-ui fundamentals | [What Is 3x-ui?](https://smartvds.org/hosting-basics/3x-ui-panel/) |
| Installation | [Install 3x-ui on Ubuntu](https://smartvds.org/software-setup-guides/install-3x-ui-ubuntu-server/) |
| VLESS configuration | [Configure VLESS in 3x-ui](https://smartvds.org/software-setup-guides/configure-vless-3x-ui-ubuntu-server/) |
| WireGuard | [Configure WireGuard with 3x-ui](https://smartvds.org/software-setup-guides/configure-wireguard-3x-ui-ubuntu-server/) |
| Subscription links | [Configure Subscription Links](https://smartvds.org/software-setup-guides/configure-3x-ui-subscription-links/) |
| Panel comparison | [Marzban vs 3x-ui](https://smartvds.org/hosting-basics/marzban-vs-3x-ui/) |
| VPN technologies | [Best VPN Protocols and Server Panels](https://smartvds.org/hosting-basics/best-vpn-protocols-server-panels/) |

### Complete Documentation

All seven tutorials are also organized in the dedicated:

**[SmartVDS 3x-ui Guide on GitBook](https://smartvds.gitbook.io/smartvds-docs/3x-ui-guide)**

---

## About SmartVDS

[SmartVDS.org](https://smartvds.org/) is an independent hosting catalog and technical knowledge base covering:

- VPS and VDS hosting
- Dedicated servers
- GPU hosting
- VPN infrastructure
- Linux and Windows administration
- Docker and self-hosted software
- Network security and virtualization

The project publishes practical tutorials and comparisons to help users understand server technologies and choose suitable hosting configurations.

**Website:** https://smartvds.org/  
**Documentation:** https://smartvds.gitbook.io/smartvds-docs/  
**3x-ui Guide:** https://smartvds.gitbook.io/smartvds-docs/3x-ui-guide

---

*Educational documentation maintained by the SmartVDS project.*

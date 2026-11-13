# Networking Labs

Practical networking notes and repeatable lab exercises for building skills in network support and infrastructure.

> **Status:** Learning lab guide. The configurations below are example exercises; only mark an exercise as completed after you have run it and saved your own verification evidence.

## Lab roadmap

| Area | Exercise | Evidence to save |
|---|---|---|
| Switching | Create VLANs and configure access ports | `show vlan brief` |
| Trunking | Configure and verify an 802.1Q trunk | `show interfaces trunk` |
| DHCP | Configure a DHCP pool and exclusions | Client lease and `show ip dhcp binding` |
| DNS | Configure or inspect DNS resolution | `nslookup` output |
| Routing | Configure static routes between networks | `show ip route` and successful ping |
| Dynamic routing | Explore OSPF in a multi-router topology | `show ip ospf neighbor` |

## Example Cisco IOS practice

### 1. Create VLANs

```text
enable
configure terminal
vlan 10
 name ADMIN
vlan 20
 name USERS
interface gigabitEthernet 0/1
 switchport mode access
 switchport access vlan 10
interface gigabitEthernet 0/2
 switchport mode access
 switchport access vlan 20
end
show vlan brief
```

Interface names and available commands vary by switch model and simulator.

### 2. Configure a trunk

```text
configure terminal
interface gigabitEthernet 0/24
 switchport mode trunk
end
show interfaces trunk
```

Some platforms require an explicit trunk encapsulation command; many modern access switches support only 802.1Q.

### 3. Verify DHCP and DNS from a client

```text
ipconfig /all
ipconfig /release
ipconfig /renew
nslookup example.com
```

Use a domain you are permitted to query in your lab. Record the assigned address, subnet mask, default gateway, and DNS server.

## Verification checklist

- [ ] Record the topology, device models, software versions, and IP addressing plan.
- [ ] Save the relevant configuration snippets with passwords and secrets removed.
- [ ] Capture command output before and after each change.
- [ ] Test connectivity between the intended networks.
- [ ] Explain the result, any issue encountered, and how it was resolved.

## Lab environment

Exercises can be completed in a network simulator such as Cisco Packet Tracer, or on equipment you own or are authorized to administer. Do not test configurations on production networks without approval.

## Suggested folder structure

```text
labs/
  networking/
    README.md
    vlan-trunking/
    dhcp-dns/
    static-routing/
    ospf/
```

Add a separate folder for each lab and include a topology image, sanitized configurations, verification output, and a short explanation of what you learned.

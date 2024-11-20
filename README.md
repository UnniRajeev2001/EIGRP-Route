Here’s how you can configure EIGRP on Router 0 and Router 1 using the provided IP addresses in Cisco Packet Tracer. 

### Router 0 Configuration
1. Assign IP addresses to interfaces.
2. Enable EIGRP and advertise the networks.

```plaintext
Router> enable
Router# configure terminal
Router(config)# interface gig0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface serial0/0
Router(config-if)# ip address 10.0.0.2 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# router eigrp 1
Router(config-router)# network 192.168.1.0 
Router(config-router)# network 192.168.11.0
Router(config-router)# exit
Router(config)# end
Router# write memory
```

---

### Router 1 Configuration
1. Assign IP addresses to interfaces.
2. Enable EIGRP and advertise the networks.

```plaintext
Router> enable
Router# configure terminal
Router(config)# interface gig0/0
Router(config-if)# ip address 192.168.11.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface serial0/0
Router(config-if)# ip address 10.0.0.3 255.255.255.252
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# router eigrp 1
Router(config-router)# network 192.168.11.0
Router(config-router)# network 1192.168.1.0
Router(config-router)# exit
Router(config)# end
Router# write memory
```

---

### Verifying the Configuration

To check the EIGRP neighbor relationship and routing table, use the following commands:

1. **Check EIGRP neighbors:**
   ```plaintext
   Router# show ip eigrp neighbors
   ```

2. **Check the routing table:**
   ```plaintext
   Router# show ip route
   ```

This configuration establishes EIGRP between Router 0 and Router 1, allowing them to exchange routing information for the specified networks.

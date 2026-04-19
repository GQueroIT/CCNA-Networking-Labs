# Commands Used

---

## VLAN Configuration

vlan 10
name SALES

vlan 20
name IT

---

## Access Port Assignment

interface fastEthernet 0/1
switchport mode access
switchport access vlan 10

interface fastEthernet 0/2
switchport mode access
switchport access vlan 20

---

## Trunk Configuration

interface gigabitEthernet 0/1
switchport mode trunk
switchport trunk encapsulation dot1q
switchport trunk native vlan 99

---

## Verification Commands

show vlan brief
show interfaces trunk
show interfaces status

---

## Connectivity Testing

ping <destination-ip>

# RSTP-Ansible
Rapid Spanning Tree Protocol (RSTP) Configuration with Ansible

This Ansible playbook automates the configuration of Cisco switches for Rapid Spanning Tree Protocol (RSTP), VLANs, trunk/access ports, and associated spanning-tree enhancements.
📌 Prerequisites

    Ansible installed on your control node.

    Cisco IOS switches (SPINE-1, SPINE-2, LEAF-1, LEAF-2) reachable via SSH.

    Proper inventory file (hosts) with IP addresses or hostnames defined.
    ⚙️ Playbook Tasks

This playbook performs the following configuration tasks:

    Verify Switch Connectivity

        Executes a simple command (show version) to test connectivity.

    Set Hostnames

        Sets appropriate hostnames based on device role.

    Create VLANs

        VLAN 20: Management

        VLAN 30: AES67

        VLAN 40: Dante

    Configure Interfaces

        Trunk Ports (GigabitEthernet1/0/1-2): Allow VLANs 20,30,40

        Access Ports (GigabitEthernet1/0/3-5): Assigned VLANs as per topology.

    Configure RSTP

        Enable RSTP (rapid-pvst) globally.

        Set pathcost method to long.

    Set Bridge Priorities

        SPINE-1: Primary Root (priority 0)

        SPINE-2: Secondary Root (priority 4096)

    Enhance Spanning Tree

        Apply Root Guard on SPINE trunk ports.

        Enable Portfast and BPDU Guard on LEAF access ports.

        Execute the playbook using:

ansible-playbook -i hosts rstp_configuration.yml
You will be prompted for Cisco credentials (username/password) upon execution.

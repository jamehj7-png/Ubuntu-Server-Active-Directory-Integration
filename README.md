# Ubuntu-Server-Active-Directory-Integration
This step integrates the Ubuntu Server into the domain managed by Active Directory running on Windows Server.

The objective is to allow Linux systems to authenticate using domain credentials and to centralize identity management within the lab infrastructure.

1. Network Configuration

The Ubuntu server was configured using Netplan with a static IP address.

Example configuration:

IP Address: 192.168.20.10
Gateway: 192.168.20.1 (pfSense)
DNS Server: 192.168.10.10 (Domain Controller)

This configuration allows the Ubuntu server to communicate with the domain controller through the firewall.

The network routing is handled by pfSense.

2. Domain Discovery

To verify that the server can detect the Active Directory domain, the following command was executed:

realm discover lab.lan

The output confirmed that the domain is reachable and that the domain controller is running Active Directory services.

3. Kerberos Authentication Test

Kerberos authentication was tested using the following command:

kinit Administrateur@LAB.LAN

This command requests a Kerberos ticket from the domain controller.

The ticket can be verified with:

klist

This confirms that the Linux server can authenticate with the Active Directory domain.

4. Domain Join

After verifying connectivity and authentication, the Ubuntu server was joined to the domain using:

realm join lab.lan -U Administrateur

Once completed, the server becomes a member of the domain and can authenticate users from Active Directory.

5. Verification

The following command confirms that the system successfully joined the domain:

realm list

The output displays the domain configuration and confirms the system is a domain member.

Result

The Ubuntu server is now integrated into the Active Directory infrastructure and can communicate with the domain controller. This setup simulates a hybrid environment where both Windows and Linux systems are centrally managed.

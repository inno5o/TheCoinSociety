# Active Directory Implementation

## Lab environment

I implemented Active Directory for the fictional **TheCoinSociety** network in GNS3 VM and VMware. The domain controller ran Windows Server 2019 at `172.16.1.6`, with a Windows 10 virtual machine used to test domain membership.

## Configuration

1. Assigned the Windows Server a static IP address and installed the **Active Directory Domain Services (AD DS)** and DNS roles.
2. Promoted the server to a domain controller and created a new domain.
3. Created domain user accounts and configured basic Group Policy settings.
4. Set the Windows 10 workstation’s DNS server to `172.16.1.6`, then joined it to the domain.
5. Configured a DNS forwarder on the domain controller after finding that the joined workstation could resolve internal names but not external ones.

## Validation

| Check | Result |
|---|---|
| AD DS installation and domain controller promotion | Completed |
| Domain user accounts | Created |
| Windows 10 domain join | Successful |
| Domain account sign-in | Successful |
| External name resolution after DNS forwarding | Restored |

## Evidence

Add a small selection of screenshots from the original lab report here:

1. AD DS role installation and domain controller promotion.
2. Domain users in Active Directory Users and Computers.
3. Windows 10 joined to the domain.
4. DNS forwarder configuration or a successful external DNS lookup.

The source report uses both `thecoinsociety.local` and `lab.local` for the domain. Use the name shown in the actual domain join and domain controller screenshots when adding the evidence.

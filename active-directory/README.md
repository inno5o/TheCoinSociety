# Active Directory Lab

## Overview

I deployed Active Directory in **TheCoinSociety**, an imaginary company network built in GNS3 VM and VMware. A Windows Server 2019 virtual machine served as the domain controller, providing centralised user authentication and DNS for a Windows 10 workstation.

## What I implemented

- Installed Active Directory Domain Services (AD DS) and promoted the server to a domain controller.
- Configured DNS for the domain and created user accounts.
- Joined a Windows 10 workstation to the domain.
- Configured basic Group Policy settings.
- Tested domain sign-in, name resolution and policy application.

## Outcome

The Windows 10 workstation joined the domain and could sign in with a domain account. I also investigated an external DNS resolution issue after the domain join and configured DNS forwarding on the domain controller.

## Documentation

- [Implementation](Implementation/README.md) — configuration, validation and selected screenshots.
- Security testing — separate exercises will be documented here as they are completed.

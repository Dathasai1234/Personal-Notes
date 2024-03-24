---
title: VPN's
date: 2023-11-20
resources: https://www.goodaccess.com/blog/vpn-gateway-everything-you-need-to-know
tags:
  - networking
---

# Table of Contents

- [[#Functionalities provided|Functionalities provided]]
- [[#Requirements to create P2S|Requirements to create P2S]]
- [[#Self Signed root certificate|Self Signed root certificate]]
- [[#Generate a Client Certificate|Generate a Client Certificate]]
- [[#copy paste root cert in portal|copy paste root cert in portal]]
- [[#Save it and Download VPN client|Save it and Download VPN client]]
- [[#important resources|important resources]]

# Functionalities provided

- creating a secure channel.
- Authenticating users
- Providing an IP address (static IP address).
- [DNS resolution](https://www.goodaccess.com/blog/vpn-gateway-everything-you-need-to-know#:~:text=VPN%20gateways%20also%20carry%20out%20DNS%20resolution%20to%20route%20traffic%20over%20the%20internet%2C%20and%20more%20advanced%20gateways%20also%20offer%20DNS%20filtering%20as%20a%20protective%20measure%20against%20phishing%20and%20malware%20attacks.)
- [access control](https://www.goodaccess.com/blog/vpn-gateway-everything-you-need-to-know#:~:text=Last%20but%20not%20least%2C%20VPN%20gateways%20can%20also%20handle%20access%20control%2C%20which%20consists%20of%20assigning%20access%20rights%20to%20users.%20This%20can%20be%20a%20powerful%20security%20tool%20of%20limiting%20access%20to%20applications%20and%20thus%20significantly%20reducing%20the%20risk%20of%20cyber%20threats%20and%20their%20impact.)

---

- ! Creating secure channels between users, networks, or systems over the internet.
- The way tunnel is established and secured depends on the selected **VPN protocol**, such as openVPN, IPsec, or IKEv2.
	- ? secure access to local systems for remote users would often be encrypted via the **IKEv2 protocol**.
	- ? site-to-site connections connecting two branches would rely on the **IPsec protocol**.
	- ? modern protocols, like OpenVPN or Wireguard are equally suited for all VPN use cases.

- Another task of VPN gateway is authenticating users. 
- [authentication process](https://www.goodaccess.com/blog/vpn-gateway-everything-you-need-to-know#:~:text=When%20a%20user,for%20better%20security.)

---
# Requirements to Create P2S

- **VPN gateway** - need to attach to the Vnet where the VM exists.
- whenever we connect Gateway with a Vnet. **we require a *GatewaySubnet*** subnet
- connecting between Gateway with the Gateway Subnet.

- Need to give an **IP pool** (IP range) to the VPN gateway, one IP is assigned to the Local machine.
	- Then both VPN gateway and Local machine will be in the same network.
	- Connection established
- Need an **Authentication process** to connect the VPN gateway. 
	- In youtube (self Signed Root Certificate - authentication process) inside the VPN gateway.
	- Create a **Client Certificate** - deployed in the local machine.
- Need a **VPN client** (software) installed in the Local machine to initiate the VPN connection.

- now VPN gateway is a gateway to enter inside the Vnet.

![[Pasted image 20231120120302.png | 700]]

---


# Example - 1 PowerShell Console Session Still Open

- ! The #Root-Certificate and #Client-Certificate much be executed in the same powershell console session.
- The root certificate is used exported to Azure VPN Gateway.
- And the Client certificate is used in the client server.

## Self Signed Root Certificate

#Self-Signed-root-certificate

- #root-certificate/powershell-script
```powershell
$params = @{
    Type = 'Custom'
    Subject = 'CN=P2SRootCert'
    KeySpec = 'Signature'
    KeyExportPolicy = 'Exportable'
    KeyUsage = 'CertSign'
    KeyUsageProperty = 'Sign'
    KeyLength = 2048
    HashAlgorithm = 'sha256'
    NotAfter = (Get-Date).AddMonths(24)
    CertStoreLocation = 'Cert:\CurrentUser\My'
}
$cert = New-SelfSignedCertificate @params
```

- Locating the certificate - **certmgr.msc**, console to manage your certificates
- **Personal** > **Certificates**
- P2SRootCert file is created (valid for 1 year)
- Exporting - right-click > All tasks > Export > NExt > Next > Base-64 encoded, 509 (.CER)

---
## Generate a Client Certificate

- #client-certificate/powershell-script
```powershell
$params = @{
       Type = 'Custom'
       Subject = 'CN=P2SChildCert'
       DnsName = 'P2SChildCert'
       KeySpec = 'Signature'
       KeyExportPolicy = 'Exportable'
       KeyLength = 2048
       HashAlgorithm = 'sha256'
       NotAfter = (Get-Date).AddMonths(18)
       CertStoreLocation = 'Cert:\CurrentUser\My'
       Signer = $cert
       TextExtension = @(
        '2.5.29.37={text}1.3.6.1.5.5.7.3.2')
   }
   New-SelfSignedCertificate @params
```

- Exporting - **Export the private key** > create a password > and save it.
- extension - **.pfx**

---
# Example 2 - New PowerShell Console Session

If you're creating additional client certificates, or aren't using the same PowerShell session that you used to create your self-signed root certificate, use the following steps:

1. This cmdlet returns a list of certificates that are installed on your computer.

```powershell
Get-ChildItem -Path "Cert:\CurrentUser\My"
```

2. copy the thumbprint that is located next to it to a text file.

	Replace THUMBPRINT with the thumbprint of the root certificate from which you want to generate a child certificate.

```powershell
$cert = Get-ChildItem -Path "Cert:\CurrentUser\My\<THUMBPRINT>"
```

3. run the cmdlet to generate the Client cert.

```powershell
$params = @{
    Type = 'Custom'
    Subject = 'CN=P2SChildCert'
    DnsName = 'P2SChildCert1'
    KeySpec = 'Signature'
    KeyExportPolicy = 'Exportable'
    KeyLength = 2048
    HashAlgorithm = 'sha256'
    NotAfter = (Get-Date).AddMonths(18)
    CertStoreLocation = 'Cert:\CurrentUser\My'
    Signer = $cert
    TextExtension = @(
     '2.5.29.37={text}1.3.6.1.5.5.7.3.2')
}
New-SelfSignedCertificate @params
```

---
# Copy Paste Root Cert in Portal

![[Pasted image 20240103121500.png | 500]]

---
# Save it and Download VPN Client

- unzip it.
- run the exe as administrator

---

# Important Resources

[About Azure VPN Gateway | Microsoft Learn](https://learn.microsoft.com/en-us/azure/vpn-gateway/vpn-gateway-about-vpngateways)
[VPN protocols compared](https://www.goodaccess.com/blog/vpn-protocols-compared)
[IP Whitelisting](https://www.goodaccess.com/ip-whitelisting)
[active-active, actice-standby](https://learn.microsoft.com/en-us/azure/vpn-gateway/design#:~:text=VPN%20Gateway%20can,experience%20higher%20throughputs.)

---

# Other Resources

[[Introduction to VPN gateways]]
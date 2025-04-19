## About
Guide for replacing the Data Domain System Manager self-signed SSL certificate for HTTPS access without security warnings. DDOS has a built-in tool to generate a CSR, a Windows AD CS can be used to sign this CSR

## Requirements
- Admin access to the Data Domain CLI
- Write access to the Data Domain file system __/ddvar__
- Windows AD CS

## Create system passphrase
`system passphrase set`

![image](https://github.com/iamfabo/dell_emc/assets/60046736/be7e87f2-2c36-47ae-99cb-30f8e0aca8aa)

## Create new CSR
`adminaccess certificate cert-signing-request generate key-strength 2048bit country <two letter country code e.g. US> state <state> City <city> org-name <"org_name"> org-unit <org_unit> common-name <FQDN> subject-alt-name "IP:xxx.xxx.xxx.xxx, DNS:dns_short_name, DNS:FQDN"`

![image](https://github.com/iamfabo/dell/assets/60046736/4d6323f9-d9ed-4b56-9195-91b5159e649e)

## Show current CSR
`adminaccess certificate cert-signing-request show`

![image](https://github.com/iamfabo/dell/assets/60046736/6f9547f2-b2a8-4526-b9c4-df67880e9687)

## Access the CSR from the ddvar directory
This can be achieved by setting up a CIFS share of the ddvar directory

DD System Manager -> Protocols -> CIFS

![image](https://github.com/user-attachments/assets/bf394035-2fee-47ff-8806-ea31230d6343)


## Import signed certificate
Sign the CSR by your CA

![image](https://github.com/iamfabo/dell/assets/60046736/f75968d1-11b4-4ec8-9e73-22c6211f91cf)

and upload the signed certificate to the directory __/ddvar/certifciates__

![image](https://github.com/iamfabo/dell/assets/60046736/f7dccb2a-5fb3-45ac-9744-df9b6ed585c8)

Run the following command:\
`adminaccess certificate import host application https file <name_of_signed_cert.cer>`

![image](https://github.com/iamfabo/dell/assets/60046736/6da78edf-813c-4e42-badd-97feba568b34)

## Show current https certificate
`adminaccess certificate show imported-host`

![image](https://github.com/iamfabo/dell/assets/60046736/3bf06951-a8b1-41b5-8d4c-dd88daaccba0)

## Result
##### FQDN
![image](https://github.com/iamfabo/dell/assets/60046736/fc50cd3d-a826-46f6-99e7-3db6e96e10e2)

##### DNS short name
![image](https://github.com/iamfabo/dell/assets/60046736/0741c08b-44b6-49b2-b2c0-199bcc0dd656)

##### IPv4
![image](https://github.com/iamfabo/dell/assets/60046736/ba3a6ab9-4da4-42f2-9406-281cd08fd646)

## Clean up

##### Delete current imported https certificate
`adminaccess certificate delete imported-host application https`

> ⚠️ **Warning:**\
> Only run this command if you intend to replace the current CA-signed certificate; if this certificate gets deleted, DDOS will fall back to its self-signed certificate

##### Delete current CSR
`adminaccess certificate cert-signing-request delete`

![image](https://github.com/iamfabo/dell/assets/60046736/ad413cb4-77f2-4835-a6ac-caef82d74616)

# Converting pem to pfx Using OpenSSL Windows
Converting pem to pfx Using OpenSSL (Windows)
Converting .pem to .pfx Using OpenSSL (Windows)

 1. Purpose

This document describes the step-by-step process to convert SSL/TLS certificates in PEM format (.pem) to PFX format (.pfx) using OpenSSL on Windows.

 Why convert?

.pem files are commonly used in Linux/Apache/Nginx.

.pfx files are needed for Windows IIS, Azure, or applications that require PKCS#12 format.

 2. Prerequisites

OpenSSL for Windows installed

Example path:


```
C:\Program Files\OpenSSL-Win64\bin
```


Certificate files:

privkey.pem → Private key

cert.pem → Public certificate

chain.pem → Intermediate/CA certificate chain

A destination folder to save the .pfx file

Example: D:\ayk\

3. Command to Run

Open Command Prompt as Administrator → navigate to the OpenSSL directory:
```
cd "C:\Program Files\OpenSSL-Win64\bin"
```

Run the following command:
```

openssl pkcs12 -export -out D:\ayk\ayk.pfx -inkey D:\ayk\privkey.pem -in D:\ayk\cert.pem -certfile D:\ayk\chain.pem
```


4. Explanation of Command

openssl pkcs12 -export → Create a PFX file

-out D:\ayk\ayk.pfx → Output file path

-inkey D:\ayk\privkey.pem → Private key file

-in D:\ayk\cert.pem → Certificate file

-certfile D:\ayk\chain.pem → Intermediate CA certificates

5. Expected Output

OpenSSL will prompt for an Export Password:
```
Enter Export Password:
Verifying - Enter Export Password:
```

his password protects the .pfx file.
(You’ll need it when importing into IIS, Azure, or other apps.)

After successful execution, the file:
```
D:\ayk\ayk.pfx
```
will be created.

6. Validation

To check if the .pfx was created properly:
```
openssl pkcs12 -info -in D:\ayk\ayk.pfx
```
(OpenSSL will ask for the export password you set earlier.)

7. Notes

Always keep privkey.pem secure (do not share).

.pfx files can now be imported into:

Windows IIS Manager

Azure App Service

Microsoft Management Console (MMC)




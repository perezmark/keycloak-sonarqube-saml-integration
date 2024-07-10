1. Extract the Private Key (PKCS8):

Bash
openssl pkcs12 -in keystore.p12 -nocerts -out private_key.pem -nodes
Use code with caution.
content_copy
keystore.p12: The path to your PKCS#12 keystore file.
-nocerts: Tells OpenSSL to exclude certificates from the output.
-out private_key.pem: Specifies the file name for the extracted private key.
-nodes: Prevents OpenSSL from encrypting the output private key (important for PKCS8 format).
2. Extract the Certificate (X.509):

Bash
openssl pkcs12 -in keystore.p12 -clcerts -nokeys -out certificate.pem
Use code with caution.
content_copy
-clcerts: Includes only the certificate chain in the output.
-nokeys: Excludes private keys from the output.
-out certificate.pem: Specifies the file name for the extracted certificate.
Important Considerations:

Password: You'll be prompted to enter the password you used to protect the keystore.p12 file.
Key Format: The private_key.pem file you extract will be in PKCS#8 format by default, which is what you need for signing requests.
Security: Always handle your private keys with extreme care. Store them securely and avoid sharing them.
Alternative Method (KeyStore Explorer):

If you prefer a graphical user interface, you can use KeyStore Explorer (KSE):

Open the keystore.p12 file in KSE.
Right-click on the private key entry.
Select Export -> Private Key as PKCS #8.
Choose the export options (e.g., unencrypted or encrypted).
Save the private key as a .pem file.
To export the certificate, right-click on the certificate entry and select Export -> Certificate as X.509.
Key Points:

PKCS#8 vs. PKCS#1: PKCS#8 is a newer format for storing private keys. It includes additional information like the algorithm type, making it more versatile.
OpenSSL Availability: OpenSSL is pre-installed on most Linux and macOS systems. If you're using Windows, you can install it (e.g., using Git Bash).
Tool Choice: If you're comfortable with the command line, OpenSSL is often faster and more efficient. KeyStore Explorer provides a user-friendly alternative.
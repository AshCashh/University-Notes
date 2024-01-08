#networks 
[[Network Security]] policies help provide a direction on which control framework can be built. They are documents that define a set of rules describing what is and isn't allowed on a network and will help secure the organisations data/assets against external and internal threads. These documents also mention ways of enforcing these rules and steps taken if the rules are breached.
## Determining Elements of a Network Security Policy:
- **Access Control Policy**: Specifies how and when a user can access some network resource
- **Privacy Policy**: Describes what staff, customers and business partners can expect for monitoring and reporting network use
- **Acceptable use Policy**: Describes what purposes network resources can be used and what constitutes proper or improper use of network resources
- **Auditing Policy**: Explains the manner in which security compliance or violations can be verified and the consequences of non-compliance
# CIA Triad
The CIA triad is a set of three principles that are used to describe the security of an organisation, these are:
1. Confidentiality: Ensuring that the protection of information assets and networks from unauthorised users.
2. Integrity: Ensuring that the modification of information assets is managed in an authorised manner
3. Availability: Ensuring continuous access to information assets and networks by authorised users 
# Types of Security Control
- **Administrative Control**: Relates to policies / procedures / guidelines that define personnel or business practices based on the organisations security goals.
- **Physical Control**: Relates to any tangible that is used to prevent/detect unauthorised access to physical areas/systems/assets
- **Technical Control**: Includes hardware and software mechanisms used to protect assets.

# Security Mechanisms 
## Authentication
Authentication is the process of verifying the identity of a user or device. Multi-factor authentication requires a user to supply two more types of authentication draw from the following categories:
- Knowledge: What the user knows, e.g. passwords, username, pin
- Possession: What the user has, e.g. smart card, token
- Inherence: What the user is, e.g. fingerprint, retina scan
## Auditing
Auditing is the process of monitoring and recording the use of a system to ensure it is being used in accordance with the organisations security policy. It can be used to determine abnormal behaviour and potentially detect system or network intrusion attacks.
## Encryption 
Encryption is the process of encoding and decoding data to make it unreachable to anyone without the correct key. It is used to protect data in transit and at rest. Encryption mechanisms can be used to achieve data confidentiality and integrity against attack such as:
- Forgery
- Repudiation
- Eavesdropping
## Cryptography
Cryptography is a technique of encryption and can be broken into the following categories:
- Symmetric Cryptography: Using the same key to encrypt and decrypt data
- Asymmetric (public key) Cryptography: Two keys are used, where one is used for encryption, the other for decryption.
To ensure confidentiality, the sender encrypts the messages with the receiver's public key and then the receiver decrypts the received message with its own private key.
![[Pasted image 20230916152623.png|centre|400]]
## Digital Signatures
A digital signature is a way to verify the authenticity and integrity of a message. Digital signatures are achieved using public key cryptographic techniques in addition to cryptographic hash functions:
#### Digital Signature Generation
1. The document is placed to a hash function to generate a MAC
2. The MAC is then encoded with the signer's private key to become the digital signature
3. The document, digital signature and the signers public key are sent to the recipient.
![[Pasted image 20230916152943.png|centre|400]]
# Public Key Infrastructure (PKI) and Certificate Authorities (CA)
PKI is a framework that allows organisations to manage the creation, distribution and revocation of public key certificates

A certification authority is a trusted third party that issues digital certificates to users and organisations

## Digital Certificates
A digital certificate is a document that binds a public key to an entity. It contains information such as:
- The key owners identity and public key
- Information affixed by the CA (issuer, validity, serial number, etc)
- CA's signature


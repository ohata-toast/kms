## Security > Secure Key Manager > Overview
Secure Key Manager is provided to securely save user's important data and control access authority. Users may save confidential data, symmetric keys, and asymmetric keys at Secure Key Manager.

### Main Features
* Data Management
    * Register, manage, and query confidential data
    * Create, manage, and rotate symmetric keys, or encrypt/decrypt data 
    * Create, manage, and rotate asymmetric keys, or sign/verify data
* Data Access Control
    * Control data access by using client's IPv4 address
    * Control data access by using client's MAC address
    * Control data access by using client's certificate

### Description
Secure Key Manager is provided to securely save user's important data and control access authority. Confidential data, symmetric keys, and asymmetric keys can be managed by Secure Key Manager.

#### Confidential Data Management
Manages data, such as database access data, or appkey for API calls, which may be exposed to security threats if they are under client's direct management. Users may register 32KB or smaller text data as confidential data. Only those clients who are authenticated by user-configured method can access registered confidential data. Regarding the means of confidential data management, see "For Reference- Managing Database Access Information with Confidential Data Management of Secure Key Manager".

#### Symmetric Key Management
Manages user symmetric keys that are available to encrypt/decrypt data. Users can create and save symmetric keys at Secure Key Manager. Clients who are authenticated by user-configured method can encrypt or decrypt 32KB or smaller text data by using user symmetric keys saved at Secure Key Manager. User symmetric keys can never be directly exposed to clients, but are available only for indirect use through APIs. In other words, user symmetric keys can be protected without being exposed to outside. In addition, by using the key rotation feature of Secure Key Manager, user symmetric key values can be updated without changing clients. Regarding the means of symmetric key management, see -"For Reference- Encrypting Envelopes with Symmetric Key Management of Secure Key Manager".

#### Asymmetric Key Management
Manages user's asymmetric keys which are available to sign/verify data. Users can create and save user asymmetric keys at Secure Key Manager. Clients authenticated by user-configured method can sign/verify 245 Byte or smaller text data by using user asymmetric keys saved at Secure Key Manager. User asymmetric keys can never be directly exposed to clients, but are available only for indirect use through APIs. In other words, user asymmetric keys can be protected without being exposed to outside. In addition, by using the key rotation feature of Secure Key Manager, user asymmetric key values can be updated without changing clients.

#### Access Control
Secure Key Manager provides a variety of authentication methods to protect user data. Only those clients who are authenticated can access data saved at Secure Key manager. The methods are categorized into 'IPv4 Address Authentication', which checks client's IPv4 address; 'MAC Address Authentication', which checks client's MAC address; and 'Client Certificate Authentication', which checks client's certificate used for communication.

### Structure of Service
Secure Key Manager applies two encryption keys, such as Root Key and System Key, internally, so as to securely save user data. Root Key is used to protect the System Key, while System Key is to protect user data. System Key is encrypted with Root Key and saved at the system key management server of Secure Key Manager. The Secure Key Manager server goes through authentication and imports encrypted system key from the system key management server of Secure Key Manager. When it is decrypted by using the root key, the system key processing module becomes enabled for the system key. In order to access user data saved at Secure Key Manager abnormally, three physically separated systems must acquire all of root key, system key, and user data.  

Users can manage Secure Key Manager on the NHN Cloud web console. Web console provides creating/managing user data, and creating/managing client authentication data. All user data generated at Secure Key Manager are encrypted with system key and saved at user's data storage. Client authentication data encrypt a part of important data with system key and save them at a client's storage for authentication data.

Secure Key Manager provides a variety of APIs to be available for a client server. The client server can request of querying confidential data, encrypting/decrypting with symmetric keys, and signing/verifying with asymmetric keys. Client authentication module determines whether to allow client's request by using client authentication data. If a client's request is allowed, the user data processing module decrypts encrypted user data by using system key processing module to enable service.

![overview-01](http://static.toastoven.net/prod_kms/2019-12-24/overview-01.png)

### For Reference

#### Managing Database Access Information with Confidential Data Management of Secure Key Manager
An application based on database saves database access information in the configuration file. With the rise of servers executing the application, an increasing number of servers save database access information, raising the risk of exposure of such data. Plus, it also entails the nuisance of editing configuration and redeploying it to the entire server, when there is a change in the access data.
However, with the confidential data management feature of Secure Key Manager, database access information can be safely managed at the center. Any application requiring database access can import database access information, at the start of a service, from Secure Key Manager. With Secure Key Manager, users can  manage application servers which need to allow database access. Even with a change in the access data, there is no need to edit application: you just update information at Secure Key Manager.  

#### Encrypting Envelops with Symmetric Key Management of Secure Key Manager
Secure Key Manager provides symmetric key management to enable data encryption/decryption. Applications can encrypt/decrypt data by using the Secure Key Manager API. However, encrypting/decrypting all data with Secure Key Manager API may cause performance or cost issues.  That is when Envelope Encryption comes in, as one of the most common solutions. Envelope Encryption refers to a method in which only the encryption key, which is applied to encrypt data for encryption, is protected by another encryption key from outside. In other words, data is encrypted by a local encryption key which is managed within an application, while the local encryption is encrypted with Secure Key Manager API, and then saved. When the data needs to be decrypted, the local encryption key gets decrypted by using the Secure Key Manager API.

#### Glossary
| Term | Description |
|---|---|
| Key Store | The unit of saving user data and setting authentication method |
| Key | User data managed by Secure Key Manager (e.g. confidential data, symmetric key, or asymmetric key) |
| Authentication Method | A method of decision whether user data saved at Secure Key Manager can be accessed by clients |
| Authentication Data | Client information allowing access to user data saved at Secure Key Manager |
| Key Rotation | Updating keys only, under the same key ID for symmetric and asymmetric keys |
| Key Version | Value of increase at every key rotation of symmetric or asymmetric keys |

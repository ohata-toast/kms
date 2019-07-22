## Security > Secure Key Manager > Solution Guide
Below describes the solutions for main issues that may arise while using Secure Key Manager.

### API call failure returns Invalid Appkey.
* Occurs when API is called with invalid appkey.
    * Check if appkey was correctly applied as displayed on the URL & Appkey on the Secure Key Manager page.

### API call failure returns Invalid Key ID.
* Occurs when Key ID for an API call is invalid.
    * Check if your key ID was correct.
    * See if key is currently enabled.

### API call failure returns Invalid Key Version.
* Occurs when API is called with invalid key version.
    * If it comes from Decrypt Symmetric Keys API, check if the key version applied for encryption still exists.
    * If it comes from Verify Asymmetric Keys API, check if the key version applied for signature still exists.

### API call failure returns Invalid User Data.
* Occurs when API is called with invalid user data.
    * If it comes from Decrypt Symmetric Keys API, check if the data for decryption is correct.  
    * If it comes from Verify Asymmetric Keys API, check if the signature value is correct.

### API call failure returns Invalid Key Status.
* Occurs when API is called with invalid key.
    * If it comes from Decrypt Asymmetric Keys API, check if the key for encryption is 'In Service'.
    * If it comes from Verify Asymmetric Keys API, check if the key for signature is 'In Service'.

### API call failure returns Invalid Key Version Status.
* Occurs when API is called with invalid key version.
    * If it comes from Decrypt Asymmetric Keys API, check if the key version for encryption is 'In Service'.
    * If it comes from Verify Asymmetric Keys API, check if the key version for signature is 'In Service'.

### API call failure returns IPv4 Auth Failure.
* Occurs when it fails to certify IPv4 address.
    * Check if the IPv4 address of API caller client has been registered at Secure Key Manager.
    * Check if the client IPv4 address registered at Secure Key Manager is 'In Service'.

### API call failure returns MAC Auth Failure.
* Occurs when it fails to certify MAC address.
    * Check if the MAC address of API caller client has been registered at Secure Key Manager.
    * Check if the MAC address registered at Secure Key Manager is 'In Service'.
    * Check if the client's MAC address has been added to the request header of X-TOAST-CLIENT-MAC-ADDR to call API.

### API call failure returns Certificate Auth Failure.
* Occurs when it fails to certify client's certificate.
    * Check if the certificate has been issued by Secure Key Manager.
    * Check if the certificate registered at Secure Key Manager is 'In Service'.

### API call failure returns certificate-related error messages. 
* Occurs when certificate is not correct.
    * Check if the certificate has been issued by Secure Key Manager.
    * Check valid period of the certificate.

##### For any other errors occurred during an API request, contact Customer Center ([support@toast.com](mailto:support@toast.com)).

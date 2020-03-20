## Security > Secure Key Manager > Console User Guide

Console User Guide describes basics for the use of Secure Key Manager: 
- **Create Keystores** 
- **Create Keys**
- **Register Authentication Information**
- **Manage User Data**

### Create Keystores 
At Secure Key Manager, authentication information and keys are managed by each key store. If a keystore is unavailable, you can find a page like follows:

![console-guide-01](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-01.png)

Click **Add Keystores** and a window shows to create a keystore. 

![console-guide-02](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-02.png)

Enter name and description, select more than one authentication method, and then click **Add**, and a keystore is created. The newly created keystore shows on the list of keystores like below: 

![console-guide-03](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-03.png)

Click Keystore from the list, and you can find menu as below to manage keystores: 

![console-guide-04](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-04.png)

### Create Keys 
Keys are categorized into three types at Secure Key Manager: Confidential Data saves and queries data in character strings by using APIs; Symmetric Keys provides data encryption/decryption by using APIs; and Asymmetric Keys provides data signature/verification by using APIs. Users are allowed to select a key type appropriate for usage and create keys.     

Click **Key Management** and a page shows like below to manage keys: 

![console-guide-05](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-05.png)

On the key management page, click **Add Keys** and a window pops up to create a key. Depending on the selected key type, you may enter data as needed. 

![console-guide-06](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-06.png)


![console-guide-07](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-07.png)


![console-guide-08](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-08.png)


Select Confidential Data, and you can enter name, description, and data; with Symmetric/Asymmetric Key, enter name, description, and rotation cycle. With the input of required data, click **Add** and a key is created. Then, the created key is added on the key management page as below: 

![console-guide-09](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-09.png)

### Register Authentication Information 
Keys that are created at Secure Key Manager are available only for succesfully authenticated clients. You may register authentication information for client authentication from the menu of **IPv4 Address Management**, **MAC Address Management**, and **Certificate Management**. 

#### Register IPv4 Address
Click **IPv4 Address Management**, and a page shows to manage IPv4 address for client authentication. 

![console-guide-10](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-10.png)

Click **Add IPv4 Addresses** and a page shows to add one: 

![console-guide-11](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-11.png)

Enter client IPv4 address and description, click **Add**, and the IPv4 address is added. Note that, such IPv4 address must be same as the address for client's accessing Secure Key Manager. The newly added address is displayed on the IPv4 address management page.    

![console-guide-12](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-12.png)

#### Register MAC Address
Click **MAC Address Management** and find the management page for MAC address for client authentication. 
![console-guide-13](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-13.png)

Click **Add MAC Addresses** and a window shows to add MAC address. 

![console-guide-14](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-14.png)

Enter Client MAC Address and description, and click **Add**, and the MAC address is added. The newly added MAC address shows on the management page. 

![console-guide-15](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-15.png)

#### Register Client Certificates
Click **Certificate Management**, and the certificate management page shows for client authentication. 

![console-guide-16](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-16.png)

Click **Add Certificates** and a window comes up to create a certificate. 

![console-guide-17](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-17.png)

Enter certificate name, password, and description, select usage period, and click **Add**; then, a certificate is created. The newly created certificate shows on the certificate management page like below. Click **Download**, and the certificate file can be downloaded.

![console-guide-18](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-18.png)

### Manage User Data
Secure Key Manager provides detail information on user-created data (e.g. key or authentication information). Click **Detail Key Information** on the list of user data, and details show like below: 

![console-guide-19](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-19.png)

#### Delete User Data

By default, user-created data is **Enabled**. In order to delete unnecessary data, click **Request for Deletion** on the **Detail Information** page. 

![console-guide-20](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-20.png)

Once requested for deletion, data status is changed to **Scheduled to be Deleted**. **Scheduled to be Deleted** data becomes unavailable, to be completely deleted in 7 days. 

![console-guide-21](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-21.png)

You may click **Immediately Delete** such data without having to wait until it is scheduled to be deleted, or click **Cancel Deletion** to revert the status to **Enabled**. 

![console-guide-22](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-22.png)

#### Rotate Symmetric/Asymmetric Keys 

At Secure Key Manager, symmetric/asymmetric keys can be rotated. Like below, auto rotation cycle can be set from the detail page of Symmetric/Asymmetric Key. With '0' setting for the rotation cycle, rotation cycle is not enabled.  

![console-guide-23](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-23.png)By setting more than 30 for the cycle, the next rotation date shows, and key is automatically rotated at every rotation cycle. 

![console-guide-24](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-24.png)

On the Detail Key Information page for Symmetric/Asymmetric Key, click **Immediately Rotate** to immediately rotate the key. 

![console-guide-25](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-25.png)

When a key is rotated, a new version is added to the list of key versions, like below: 

![console-guide-26](http://static.toastoven.net/prod_kms/2020-03-24/console-guide-26.png)

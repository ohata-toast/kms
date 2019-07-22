## Security > Secure Key Manager > Console User Guide

Below describes basic requirements to use Secure Key Manager.
* Creating Key Stores
* Registering Authentication Information
* Creating Keys
* Managing User Data

### Creating Key Stores
Secure Key Manager manages authentication information and keys by each key store. If there is no key store created, the page shows like Figure 1.

![console-guide-01-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-01-001.png)

Click **Add Key Store** and a window shows to **Add Key Store** like in Figure 2.

![console-guide-01-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-01-002.png)

Enter name and description, select one or more methods of certification, and click **Add**, and a key store is created. Once a key store is created, you can find the list of key stores like Figure 3.

![console-guide-01-003](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-01-003.png)

Use **+** on the list of key stores to add new key stores. Click a newly created key store, and the page shows, like Figure 4, where selected key stores can be managed.

![console-guide-01-004](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-01-004.png)

### Registering Authentication Information
Keys managed at Secure Key Manager are available only for clients who are authenticated. To register authentication information for client authentication, go to the **Authentication Management** and follow each method of authentication. 

#### IPv4 Address
Go to **Authentication Management** and click **IPv4 Address Management**, and a window show for IPv4 address management, like Figure 5.

![console-guide-02-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-02-001.png)

Click **Add IPv4 Address**를and a window shows to **Add IPv4 Address**, like Figure 6.

![console-guide-02-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-02-002.png)

Enter IPv4 address and description of a client, and click **Add** to register authentication information. The IPv4 address must be the one to access the Secure Key Manager server. You may check registered authentication information on the page of **IPv4 Address Management** like Figure 7.

![console-guide-02-003](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-02-003.png)

#### MAC Address
Go to **Authentication Management** and click **MAC Address Management** and a window shows for MAC address management, like Figure 8.

![console-guide-03-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-03-001.png)

Click **Add MAC Address** and a window shows to **Add MAC Address** like Figure 9.

![console-guide-03-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-03-002.png)

Enter MAC address and description of a client and click **Add** to register authentication information. You may check registered authentication information on the page of **MAC Address Management** like Figure 10.

![console-guide-03-003](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-03-003.png)

#### Client Certificate
Go to **Authentication Management** and click **Certificate Management** and a window shows for certificate management like Figure 11.

![console-guide-04-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-04-001.png)

Click **Add Certificate** and a window shows to **Add Certificate** like Figure 12.

![console-guide-04-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-04-002.png)

Enter name, password, and description of a certificate, select usage period, and click **Add**, and a client certificate can be created. Certificates that are created can be found on the Certificate Management page like Figure 13. Click an icon on the **Download** row on the page to download file of each certificate.

![console-guide-04-003](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-04-003.png)

### Creating Keys 
Secure Key Manager provides three types of keys: Confidential data allows to save character string data and query by using APIs; Symmetric keys allow data encryption/decryption by using APIs; and, Asymmetric keys allow data signing/verification by using APIs. Each user can select a key type for their own purpose and create a key.

Click **Key Management** and you can find a screen like Figure 14.

![console-guide-05-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-05-001.png)

Click **Add Key** to pop up a window. Depending on the type of your selection, the screen requires to enter data to create a key, like in Figure 15, 16, and 17.

![console-guide-05-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-05-002.png)
![console-guide-05-003](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-05-003.png)
![console-guide-05-004](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-05-004.png)

For confidential data, it requires to enter name, description, and data, while for symmetric/asymmetric keys, name, description, cycle of rotation are required. When all required data are filled out, click **Add** to create a key. You can check created keys on the **Key Management** page like in Figure 18.

![console-guide-05-005](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-05-005.png)

### Managing User Data
Detail information of data (e.g. authentication, or key) registered by user can be found on **Authentication Management** or **Key Management**. Click magnifier icon on the **Detail Information** row from the list of same data like Figure 19, and a window for **Detail Information** shows up like Figure 20.

![console-guide-06-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-06-001.png)

![console-guide-06-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-06-002.png)

You may edit or delete data on the **Detail Information** window.

#### Delete User Data

User-registered data at Secure Key Manager is changed to 'In Service'. To delete unnecessary data, click **Request for Deletion** on the **Detail Information** window, like Figure 21.

![console-guide-07-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-07-001.png)

Data requested for deletion are changed into 'Scheduled for Deletion' like Figure 22 and hence becomes not in service immediately. It is expected to be deleted at midnight 7 days later, after which it is to be automatically deleted.

![console-guide-07-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-07-002.png)

You may click **Immediately Delete** to immediately delete data which is scheduled to be deleted without waiting until time, or click **Cancel Deletion** to change its status into 'In Service'.

#### Set Cycle for Automatic Rotation of Symmetric/Asymmetric Keys

Secure Key Manager provides automatic key rotation for symmetric/asymmetric keys. Like Figure 23, you may set cycle for automatic key rotation on the window of detail information for symmetric keys/asymmetric keys.

![console-guide-08-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-08-001.png)

Set a larger value than 0 and display the next day of rotation, like Figure 24, and the key is automatically rotated at every rotation cycle.

![console-guide-08-002](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-08-002.png)

#### Immediate Rotation of Symmetric/Asymmetric Keys

Secure Key Manager also allows for manual rotation for symmetric/asymmetric keys. Click **Immediate Rotation** on the window of detail information for symmetric/asymmetric keys, like Figure 25, and the key is to be immediately rotated.

![console-guide-09-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-09-001.png)

Figure 26 shows that, when a key is rotated, you can find a new version is added to the list of key versions.

![console-guide-09-001](http://static.toastoven.net/prod_kms/2019-05-13/console-guide-09-001.png)

## Security > Secure Key Manager > Console User Guide

Console User Guide describes basic information required to use Secure Key Manager.
- **Creating Keystores**
- **Creating Keys**
- **Registering Authentication Information**
- **Managing User Data**

### Creating Keystores
Secure Key manager manages authentication information and keys at each keystore. Without a keystore, the page shows like Figure 1.  

![console-guide-01](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-01.png)

Click **Add Keystores** and a window shows to create a keystore like Figure 2.

![console-guide-02](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-02.png)

Enter name and description, select more than one authentication method, and click **Add**, then a keystore is created. The newly created keystore is displayed on the list of keystores like in Figure 3.  

![console-guide-03](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-03.png)

Click a keystore from the list and the menu shows to manage keystores like Figure 4.

![console-guide-04](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-04.png)

### Creating Keys
Secure Key Manager has three types of keys:
Confidential Data allows to save character string data and query via API; Symmetric Keys provide data encryption/decryption via API; and, Asymmetric Keys provide data signature/verification via API. User can select a key type for his own purpose and create keys.

Click **Manage Keys** and the page shows to manage keys, like Figure 5.  

![console-guide-05](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-05.png)

On the key management page, click **Add Keys**, and a window shows to create one. Depending on the selected key type, enter data as required by Figure 6, Figure 7, or Figure 8, respectively.  

![console-guide-06](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-06.png)

![console-guide-07](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-07.png)

![console-guide-08](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-08.png)

For Confidential Data, enter name, description and data, while for Symmetric/Asymmetric Keys, enter name, description, and rotation cycle. Enter required data and click **Add**, then a key is created. The newly created key is displayed on the key management page.  

![console-guide-09](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-09.png)

### Registering Authentication Information
Keys created by Secure Key Manager are available only to those clients who are successfully authenticated. Authentication information for client authentication can be registered on **Manage IPv4 Addresses, Manage MAC Addresses, and *Manage Certificates**.  

#### Register IPv4 Addresses
Click **Manage IPv4 Addresses** and the IPv4 address management page for client authentication shows, like Figure 10.

![console-guide-10](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-10.png)

Click **Add IPv4 Addresses** and the window shows to add one, like Figure 11.

![console-guide-11](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-11.png)

To add an IPv4 address, enter client's Ipv4 address and description and click **Add**. The IPv4 address must be the same address required for client's access to Secure Key manager. The added IPv4 address is displayed on the IPv4 address management page.

![console-guide-12](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-12.png)

#### Register MAC Addresses
Click **Manage MAC Addresses** and the MAC address management page shows for client authentication.  

![console-guide-13](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-13.png)

Click **Add MAC Addresses** and the window shows to add one, like Figure 14.

![console-guide-14](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-14.png)

To add an MAC address, enter client's MAC address and description and click **Add**. The newly added MAC address is displayed on the MAC address management page like Figure 15.

![console-guide-15](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-15.png)

#### Register Client Certificates
Click **Manage Certificates** and the certificate management page shows for client authentication, like Figure 16.

![console-guide-16](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-16.png)

Click **Add Certificates** and the window shows to create one, like Figure 17.
![console-guide-17](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-17.png)

Enter certificate name, password, and description, select usage period, and click **Add**, then a certificate is created. The newly created certificate is displayed on the certificate management page, like Figure 18. Click **Download Icon** from the page to download certificate files.

![console-guide-18](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-18.png)

### Managing User Data
Secure Key Manager provides details of user-created data (e.g. key, or authentication information). From the list of user data, like Figure 19, click **Detail Information Icon** and detail information shows like Figure 20.

![console-guide-19](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-19.png)

![console-guide-20](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-20.png)

#### Delete User Data

User-created data is **Enabled** by default. To delete unnecessary data, click **Request for Deleting** from the **Detail Information** page, like Figure 21.

![console-guide-21](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-21.png)

Once requested for deleting, data status is changed to **To be Deleted**, like Figure 22. **To-be-deleted** data become unavailable, and shall be completely deleted in 7 days.

![console-guide-22](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-22.png)

You may click **Immediately Delete** to delete **To-be-deleted** data, instead of waiting until scheduled time, or click **Undo Deletion** to revert the status to **Enabled**.

#### Rotate Symmetric/Asymmetric Keys

Secure Key manager provides rotation of symmetric/asymmetric keys. Like Figure 23, the auto rotation cycle can be configured on the detail page of symmetric/asymmetric keys. If the cycle is 0, automatic rotation becomes disabled.  

![console-guide-23](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-23.png)

Like Figure 24, if a value higher than 30 is set for the rotation cycle, key is automatically rotated at every rotation cycle, showing the next rotation date.  

![console-guide-24](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-24.png)

Click **Rotate Immediately** on the detail page of symmetric/asymmetric keys, like Figure 25, and rotate keys immediately.

![console-guide-25](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-25.png)

By rotating the key, a new version is added to the list of key versions.

![console-guide-26](http://static.toastoven.net/prod_kms/2019-12-24/console-guide-26.png)

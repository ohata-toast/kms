## Security > Secure Key Manager > Release Notes

### July 26, 2022
#### Added Approval Feature
* Added a feature to approve major changes such as key creation, modification, deletion, and changes to access control for key store
#### Added a new version of Symmetric Key Query Feature
* Added a feature to query the symmetric key for each key version

### November 23, 2021
#### Added a Symmetric Key Query Feature
* Added a feature to query the symmetric key

### October 26, 2021
#### Added a Key Import Feature
* Added a symmetric key import feature
#### Updated the Confidential Data Query Feature
* Modified the feature so that, when the user queries confidential data in the web console, the data is provided after masking the fields
#### Bug Fixes
* Fixed an issue where non-payment users could use the service normally

### September 28, 2021
#### Bug Fixes
* Fixed an issue where permissions granted using permission groups were not recognized properly
* Fixed an issue where the Reset button in Usage History did not work properly

### March 24, 2020
* The tasks performed by a user in Secure Key Manager console are logged in Cloud Trail
* Added authentication data (IPv4 address/MAC address) bulk registration feature using CSV files
* Added authentication data (IPv4 address/MAC address) download feature using CSV files

### December 24, 2019

#### Key Store Page Updates
* Changed the display method for the list of key stores
* Changed the sub-menu of a key store
* Added the quick menu to the key store

#### History Page Updates
* Changed UI so that the user can query API usage history per project

#### Statistics Page
* Added the page to query API usage statistics of each project

### July 23, 2019

#### UI Improvement
* Fixed the overlapped display of texts and buttons
* Fixed line wrapping issue when the screen is displayed in Japanese

### May 28, 2019

#### Release of New Service
* Secure Key Manager is a service to let you centrally and securely manage data that can be exposed to security risks when stored in the application server, such as confidential data (database access information, appkey, password, etc.), symmetric key, and asymmetric key. In addition, it controls access so that only the clients that pass authentication can access the data.

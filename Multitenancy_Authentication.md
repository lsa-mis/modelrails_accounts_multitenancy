### [Home](./README.md)

## Authentication:

ModelRails supports three modes of authentication; Shibboleth , GoogleOAuth and Active Directory. Utilizing these methods allows us to provide authentication without storing passwords in our applications.

>  **Important:** *Never store passwords in the application database unless it cannot be avoided. Utilize OAuth or Shibbolith instead. **Encrypt all the things!!!***

These methods of authentication can be used individually or in conjunction with one another, depending on the use case.


### GoogleOAuth
  == link to GoogleOAuth documentation
  GoogleOAuth can be used as a Single Sign On option, and logins can be restricted to the umich.edu domain. 

  This option is the easiest to impliment since it does not require coordination with other teams. (Developers can set this method up without engaging a human.)

### Shibboleth 
  == link to shibboleth documenation

### Active Directory
  == link to Active Directory documentation 
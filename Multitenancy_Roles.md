### [Home](./README.md)

### AccountRole:

Each account has a role. Roles are used to deliniate what actions are allowed on resources. Here are the default roles that are available within our syswtems by default (or configuration?). They are broken down by category.

  #### Application

  Roles for application level management tasks. These include:
  
    - adding super-users, departments and roles (if enabled?). 
    - editing content on application itself (landing page, about us, etc...) (if enabled).
  
  By default, the admins will be W&ADS Rails team. The tasks will generally be done using the console? (**Initially?)
  
  > MCommunity Method
    When creating a new application, create a MCommunity group folloing the pattern ```appname-admins``` and add the ```lsa-was-rails-admins``` group to it. 


  |   Role                    |  Permissions                       | scope                                              |Description |
  |---------------------------|------------------------------------|---------------------------------------------------|----------|
  |   **admin:****              |   [create, read, update, destroy]  | application wide                                  | All resources |
  |   **super-user:**         |   [create, read, update, destroy**]| application wide                                  | All resources |
  |   **department-admin:**   |   [create, read, update, destroy**]| department resources and accounts                 | All resources within department |
 
 #### Invitations
  |   Role                    |  Permissions                       | scope                                             | Description |
  |---------------------------|------------------------------------|---------------------------------------------------|--|
  |   **admin:**              |   [create, read, update, destroy]  | application wide                                  | All users  |
  |   **super-user:**         |   [create, read, update, destroy***]| application wide                                  | All users? (should this role be scoped narrower?) |
  |   **department-admin:**   |   [create, read, update, destroy***]| department resources and accounts                 | All user within department |
  |   **owner:**              |   [create, read, update, destroy***]| resources created by owner ****     |  All users within organization ? do we allow sharing outside? How?

  #### Resources
  |   Role                    |  Permissions                       | scope                                             |
  |---------------------------|------------------------------------|---------------------------------------------------|
  |   **owner:**              |   [create, read, update, destroy***]| resources created by or shared with by creator    |
  |   **editor:**             |   [read, update]                   | resources shared  by an owner                     |
  |   **recorder:**           |   [create, read, update]           | resources created by recorder or assigned by owner|
  |   **viewer:**             |   [read]                           | resources shared by owner                         |

  ** ***The role of 'admin' is assigned to a MCommunity group to encourage transparency and redundency.***
  *** ***Destroy may be implimented as 'archive' for certain roles and resources.***
  **** ***If application allows users to invite external users?.***
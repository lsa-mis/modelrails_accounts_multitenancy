# Model Rails Accounts & Multitenancy

## Users, accounts, roles, permissions and more

ModelRails is set up to support multi-tenancy by default. 

### [Authentication:](./Multitenancy_Authentication.md)
ModelRails supports three modes of authentication; Shibollith, GoogleOAuth and Active Directory. 

## User:
A ***User*** represents the authorization information for a particular individual. Do the credentials match the credentials for an individual? 


## Account:
***Account*** represents the entity that is interacting with the system. Each ***Account*** has_one ***AccountType***. Each ***Account*** has at least one ***account owner*** (as defined by AccountRole). ( Each ***Account*** has at least one ***AccountRole*** that is an owner. )

#### Resources are scoped to accounts by default. 
```(account:references)```

### [AccountType:](./Multitenancy_Accounts.md)

### [AccountRole:](./Multitenancy_Roles.md) (Permissions?)

### [MCommunity:](./MCommunity.md) (Memberships?)

### [Invitations:](./Multitenancy_Invitations.md)

### [Routing scheme:](./Multitenancy_Routes.md)


___ 
User.create 
  -> Create 'personal' account when user is created
  Account.create(user_id, name, email, AccountType(personal))

  AccountType.create(name)
  [personal, department, domain, team]

  AccountRole.create(:name, allowable_actions([:create, :read, :update, :destroy]))


  Account.create(name, AccountType, email)

Account.create(name: "dschmura", acount_type: (AccountType(owner)))

___

# Questions:

- Sharable? (can a user delegate the ability to share a resource to other users?)
- Do we want to build a dynamic permisions builder? Can we support it? Or is this it? 
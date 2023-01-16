### [Home](./README.md)

## AccountType:

***Account*** represents the entity that is interacting with the system. Each ***Account*** has_one ***AccountType***. Each ***Account*** has at least one ***AccountOwner***. ( Each ***Account*** has at least one ***AccountRole*** that is an owner. )

#### Resources are scoped to accounts by default. 
```(account:references)```

There are four default ***AccountTypes***  **[*personal*, *department*, *domain*, *team*]**. 

Every person who uses appname signs into a personal account. An organization account enhances collaboration between multiple personal accounts, and an enterprise account allows central management of multiple organizations.

| **AccountType**         | **Pattern**                                                                      |
|-------------------------|----------------------------------------------------------------------------------|
| **Personal Account:**   | ***required*** for each user. Set by default when the user initially signs up.   |
| **Department Account:** | A collection of personal accounts and/or team accounts and/or domain accounts. A **Department Account** has one or more **AccountOwners**. |
| **Domain Account:**     | A collection of personal accounts and/or team accounts and/or department accounts). A **Domain Account** has one or more **AccountOwners**. |
| **Team Account:**       | A collection of personal accounts (team has_many accounts as members) and/or domain accounts). A **Team Account** has one or more **AccountOwners**. A team account can have other teams as members.|

## Personal Account: 
Every user signs into a personal account. The personal account represents the identity of the user on the system. It has the user's username and profile information.

### [Home](./README.md)

## AccountType:

***Account*** represents the entity that is interacting with the system. Each ***Account*** has_one ***AccountType***. Each ***Account*** has at least one ***AccountOwner***. ( Each ***Account*** has at least one ***AccountRole*** that is an owner. )

#### Resources are scoped to accounts by default. 
```(account:references)```

There are four default ***AccountTypes***  **[*personal*, *department*, *domain*, *team*]**. 

Every person who uses appname signs into a personal account. An organization account enhances collaboration between multiple personal accounts, and an enterprise account allows central management of multiple organizations.

AccountType defines one of several types of accounts. Different types of accounts have different AccountRoles. 


| **AccountType**         | **Pattern**                                                                      |
|-------------------------|----------------------------------------------------------------------------------|
| **Personal Account:**   | ***required*** for each user. Set by default when the user initially signs up.   |
| **Department Account:** | A collection of personal accounts and/or team accounts and/or domain accounts. A **Department Account** has one or more **AccountOwners**. |
| **Domain Account:**     | A collection of personal accounts and/or team accounts and/or department accounts). A **Domain Account** has one or more **AccountOwners**. |
| **Team Account:**       | A collection of personal accounts (team has_many accounts as members) and/or domain accounts). A **Team Account** has one or more **AccountOwners**. A team account can have other teams as members.|
| **MCommunity Account:**       | An account that is tied to an MCommunity group.  > **Cannot be tied to an idividual account. Must be an MCommunity Group created for the application. |

## Personal Account: 
Every user signs into a personal account. The personal account represents the identity of the user on the system. It has the user's username and profile information.

Personal accounts within an organization can be given different roles in the organization, which grant different levels of access to the organization and its data. All members can collaborate with each other in resources and projects, but only organization owners and application managers can manage the settings for the organization and control access to the organization's data. 


## Team Account:
Team accounts are a type of shared account that allow an unlimited number of people (or teams) to collaborate. Similar to Department Accounts, personal accounts within a team can be given different roles within that team. 

Team-level roles are roles that give permissions to manage a team. 

## [MCommunity Account](MCommunity.md): 

MCommunity accounts are a kind of pointer account. They point to groups defined in MCommunity to delegate access and membership tracking (*sort of) to MCommunity. [* Due to performance considerations, it is a little more complicated than simple delegation. ] 

## Department Account:
Department accounts are a special kind of MCommunity account that is tied to a MCommunity group for that department. Only owners of that MCommunity group can modify a department's landing page?  ** I am not confident here. 


A MCommunity Account can be thought of a Team account that leverages [MCommunity](https://mcommunity.umich.edu), the University of Michigan's identity management system to manage membership. 

## Organization Account

Organizations are shared accounts where an unlimited number of people (or teams) can collaborate across many projects at once.

Like personal accounts, organizations can own resources. However, users cannot sign into an organization. Instead, each user signs into their own personal account, and any actions the person takes on organization resources are attributed to their personal account. Each personal account can be a member of multiple organizations.


```mermaid

graph TD
    APP[Application] --> |MCommunity|MAIN(fa:fa-cloud ds)

    MAIN[Application] --> SCH(fa:fa-school Schools) 
    MAIN[Maintainers] --> COL(fa:fa-graduation-cap Colleges) 
    
    
    SCH --> |MCommunity| MAINT(fa:fa-cloud Maintainers)
    SCH --> SCHTEAMS(fa:fa-users Teams)
    SCH --> C(fa:fa-sitemap Departments)
    C --> D(fa:fa-users Teams)
    C --> E(fa:fa-user Accounts)
    C --> |MCommunity|F(fa:fa-cloud Maintainers)

    COL --> COLD(fa:fa-users Teams)
    COL --> COLE(fa:fa-user Accounts)
    COL --> |MCommunity|COLEF(fa:fa-cloud Maintainers)


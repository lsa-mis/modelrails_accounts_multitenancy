### [Home](./README.md)

## MCommunity:

We leverage MCommunity to allow our users to manage access to our apps. 

When a user logs in to the application, it triggers a background job that queries MCommunity for the user's groups (both owned and members). The user's groups are stored in an array in the user table to perserve performance of the application. 

> Privacy Concern: The groups array should be stored in an encrypted field.

When a new application is created, MCommunity groups need to be created to support it. Every application has the following groups at a minimum;

appname_staging
appname_production
appname_project_leads


```mermaid

graph TD
   
    A(OAuth Login) --> |Yes| USER_EXISTS    
    USER_EXISTS(Authenticated User)

    USER_EXISTS --> GROUPS_UPDATED(Are groups updated)

    GROUPS_UPDATED --> |Yes| USER_AUTHORIZED(Groups Updated)
    GROUPS_UPDATED --> |No| NO_MCOMMUNITY_GROUPS(Query MCommunity and update groups)

    USER_AUTHORIZED(Is the user authorized?) --> |Yes| LOGGED_IN_USER(fa:fa-user current_user)
    USER_AUTHORIZED --> |No| NOT_LOGGED_IN(MCommunity Groups)

    NO_MCOMMUNITY_GROUPS --> |retry| GROUPS_UPDATED
    A(OAuth Login) --> |NO| NOT_LOGGED_IN(Return to Login Page)    
    NOT_LOGGED_IN(fa:fa-ban Return to Login Page)  
   
    LOGGED_IN_USER


  style NOT_LOGGED_IN stroke:red,stroke-width:2px,color:red,fill:white;
  style NO_MCOMMUNITY_GROUPS stroke:red,stroke-width:2px,color:red,fill:white;
  style USER_EXISTS stroke:green,stroke-width:2px,color:green,fill:white;
  style LOGGED_IN_USER stroke:green,stroke-width:2px,color:green,fill:white;
    



```


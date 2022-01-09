# SNOW-Domain-Separation

Domain separation is a way to separate data into (and optionally to separate administration by) logically-defined domains. Domain separation is best for those customers who need to:
Enforce absolute data segregation between business entities (data separation).
Customize business process definitions and user interfaces for each domain (delegated administration).
Maintain some global processes and global reporting in a single instance of ServiceNow.
Domain separation is extremely well-suited for Managed Service Providers (MSPs) and global enterprises with unique business requirements in various areas of the world.

Warning: Before activating domain separation, consult your ServiceNow representative to verify that it is suitable for your environment. Domain separation adds a level of administration overhead. Although it can be disabled, it cannot be removed from an instance.

Data: Bottom to Top
Process: Top to Bottom
![image](https://user-images.githubusercontent.com/12488769/148668327-cbb5a281-e2cc-4201-b581-f6b567c360b1.png)

![image](https://user-images.githubusercontent.com/12488769/148668321-bf136fa5-c56f-4d7f-8bd5-a76d1f3cbae3.png)

Some global properties, data and processes are shared across all domains.


![image](https://user-images.githubusercontent.com/12488769/148668348-724e91d3-6e01-46de-81da-6fff472f7e6d.png)

![image](https://user-images.githubusercontent.com/12488769/148668358-543b0b8d-f142-439f-b5b1-abf6a56f0881.png)

## Data Separation
Members of a domain only see the data contained within their domain or the child domains that are lower in the domain hierarchy. By default, all users and all records are members of the global domain unless an administrator assigns them to a particular domain. Once you assign a user or a record to a domain, the instance compares the user's domain to the record's domain to determine whether the user can view the record. For example, consider the following domain hierarchy: !

![image](https://user-images.githubusercontent.com/12488769/148668380-479e16c9-0112-4177-917d-5b528e92917c.png)

Bow Ruggeri can see any records in the Database Atlanta or the global domain.
Don Goodliffe can see any records in the Database San Diego or the global domain.
David Loo can see any records in the NY DB or the global domain.
Fred Luddy, ITIL User, Beth Anglin can see any records in the Database, Database Atlanta, Database San Diego, NY DB, or the global domain.
![image](https://user-images.githubusercontent.com/12488769/148668391-5e90ae89-d694-4aa1-b8ea-e5d9d1cbc757.png)

Note: Users in the global domain can see all records, regardless of the record's domain settings.
Warning: Guest users must be part of the global domain.
![image](https://user-images.githubusercontent.com/12488769/148668397-8bd6dfa9-f90a-4c34-88f9-a61f90f5f1ed.png)

## Domain Visibility
 Domain visibility determines whether users from one domain can access records from another domain.
For example, if Don Goodliffe is in the Database domain, and Bow Ruggeri is in the Network domain, and no incidents are in the global domain, then Don Goodliffe cannot access Bow Ruggeri's incidents since data separation prevents this. 


Note: While visibility is one method to allow users to access records, it is recommended that you use Contains for more robust control.


Solution: You can add the Database domain as a Visibility Domain to the Bow Ruggeri's user record (Visibility Domains is a related list on the user record). Then, Bow Ruggeri can access Don Goodliffe's incidents since he now has visibility to the Database domain. If you remove the visibility domain, then Bow Ruggeri can no longer access incidents in the Database domain.

## Contains Domain
Normally parent-child relationships define the domain hierarchy. A Contains domain allows you to relate domains on an as-needed basis, independent of parent-child relationships.

However, contains domains only grant visibility to domain data. Processes remain unaffected by contains relationships.

Note: Visibility controls what a particular user can see, while Contains controls what an entire domain of users can see.

## Contains vs Visibioity
Contains domains and visibility domains differ in several respects.

A contains domain: 
Is a many-to-many, domain-to-domain relationship.
Is hierarchical. When a domain is selected, you can see the data from that domain and its children.
Is controlled by the selection in the domain picker.

A visibility domain:
Is a user-to-domain relationship and is explicitly granted.
Is not hierarchical.
Is not controlled by the selection in the domain picker. Once the user is granted access to a visibility domain, they always see data in that domain and its children.

For example, there is a user who has access to domain A (the user's home domain) and is granted visibility to domains B and C. The user selects domain A in the domain picker. In this case, the user has access to domains A, B, and C. If the user changes the domain picker to domain B, B and C are visible. C is still visible because the user still has visibility to it. A is not visible, because it is not selected in the domain picker and it is not a visibility domain.

Using visibility domains excessively is not recommended.


## Domain Separation Plugin
All domain support features are consolidated into one plugin called Domain Support - Domain Extensions Installer.

The plugin combines the features of the previous plugins:

Domain Support (version 1.0)
Domain Support - Common
Domain Support - Partitioning (Data separation)
Domain Support - Delegated Administration
Domain Number Support
![image](https://user-images.githubusercontent.com/12488769/148668448-0498d2d3-03c4-436d-a946-283caa3be7b7.png)







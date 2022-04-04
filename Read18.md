# Read 18 - Web App Security

## Introduction

---

We have many ways to make many-to-many relationship. In this quick tutorial, we'll have a quick look at how the @ManyToMany annotation can be used for specifying this type of relationships in Hibernate.

## A Typical Example

---

![](https://i.ibb.co/ryR1KF6/Screenshot-from-2022-04-04-12-40-28.png)

- In the figure above, employee can be assigned to multiple projects and project may have multiple employees working for it.

- We have an employee table with employee_id as its primary key and a project table with project_id as its primary key. A join table employee_project is required here to connect both sides.

## Database Setup

---

- If we have an exist database and it has three tables: employee, project, and employee project which is a join table.

## The Model Classes

---

The model classes Employee and Project need to be created with JPA annotations using `@ManytoMany`, `@JoinTable`, and `@Table(mappedBy)`

-both the Employee class and Project classes refer to one another, which means that the association between them is bidirectional.

-This association has two sides for example the owning side and the inverse side. the owning side is Employee so the join table is specified on the owning side by using the `@JoinTable` annotation in Employee class. The `@JoinTable` is used to define the join/link table. In this case, it is Employee_Project.

- The `@JoinColumn` annotation is used to specify the join/linking column with the main table. Here, the join column is employee_id and project_id is the inverse join column since Project is on the inverse side of the relationship.

- In the Project class, the mappedBy attribute is used in the `@ManyToMany` annotation to indicate that the employees collection is mapped by the projects collection of the owner side.

## Execution

We can use Junit to see many-to-many annotation in action: 

![Junit](https://i.ibb.co/JQWkwJ1/Screenshot-from-2022-04-04-14-34-49.png)

![Junit2](https://i.ibb.co/Nshm5DY/Screenshot-from-2022-04-04-14-35-57.png)

## Security - Overview

In general, security researchers prefer to be everything is private. It's not clear what else there is to do with computers besides click on things and run applications. But if the security people are correct, then the only provably safe activity is nothing.

Something like working on passwords, It's like, you are so close, and yet so far. You almost get it, but that's worse than not getting it at all. This is uncivilized and I demand more from life.

Example of some threat and the solution for this threats

![](https://i.ibb.co/hKcpM7r/Screenshot-from-2022-04-04-14-45-31.png)

There are  a variety of misdirections and soothing words to obscure the ultimate nature of reality for example "assume that a public key cryptosystem exists"   Building a public key infrastructure is incredibly difficult in practice. For example, you could enlist a well-known technology company to do it.

Alternatively, the infrastructure could use a decentralized "web-of-trust" model. In this architecture, individuals make their own keys and certify the keys of trusted associates. This creates chains of attestation that eventually lead to fractals and H.P. Lovecraft-style madness.

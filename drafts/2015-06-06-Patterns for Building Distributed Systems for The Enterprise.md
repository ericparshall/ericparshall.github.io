---
title: Patterns for Building Distributed Systems for The Enterprise
---

## CAP Theorem

You can have 2 of the following 3:

* Consistency
> Node will not return stale data.
* Availability
> Node will provide a response in a reasonable amount of time. Not timeout or return error
* Partition Tolerance
> Nodes will continue to function in the event of a network failure


## Fallacies of Distributed Computing
* The network is reliable
* Latency is zero
* Bandwidth is inifite
* The network is secure
* Topology doesn't change
* There is one administrator
* Transport cost is zero
* The network is homogeneous
  * Different tech stacks
  * Different versions running

## Domain Driven Design

### Ubiquitous Language
* Agree on meaning of terms

### Bounded Contexts
* Assign specific semantic meanings
  * Under different contexts, certain words have different meanings
* Dialect of the ubiquitous language
  * Each context has a different dialect
* Each is optimized to solve a specific problem

> Each context solves a different problem. Better than creating one enterprise data model.

#### Enterprise data model
> Prefers consistency over availability. As demand increases, availability goes down. Solution has to be to scale up.

#### Bounded context
> More, but smaller, clusters.

### Domain model
* Entity
  * Identiy
  * Mutable
* Value object
  * no identity
  * immutable
* Aggregate
  * Composed of objects
  * Supports business operations
  
### Aggregate Rules

#### Identity
* The root is an entity
* Root has global identity
* Act on one entity without modifying another
* Child within a root entity is not globally identitifiable within the aggregate root   

#### Reference
* Outsiders can only reference a root
* Children can reference each other
* Children can reference outside roots

#### Operation
* Query only roots
* Alter only one aggregate
* Deleting a root deletes all children


## CQRS

* A pattern
* Command Query Responsibility Segregation


### Command Query Separation
Command should either change state or return results

Command - change state - void
Query - Return results - type

### Command Query Responsibility Segregation

* A Pattern
* specific problem
* Not broadly applicable

Collaborative domains
* large number of people
* small set of data

users collaborate with each other, think reservation system
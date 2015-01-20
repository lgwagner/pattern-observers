# pattern-observers
This repository captures the derived Lustre and Simulink Design Verifier (SLDV) synchronous observers for the 
specification patterns work at http://patterns.projects.cis.ksu.edu/

This work only supports a subset of the patterns defined on the Specification Patterns website.

The supported scopes from the original work are:
  global
  before p
  after p
  after p until q
  between p and q
  while p (introduced in this work, it is a simplification of after p until not p)
  
The supported predicates from the original work are:
  always a
  exists a
  a precedes b
  a responds to b

Any combination of scope and predicate can be used to create a pattern. Some combinations of scope and predicate
express liveness conditions and accordingly cannot be verified using k-inductive tools (such as Kind or SLDV). 
These combinations are: 

  global :: exists a
  global :: a responds to b
  after p :: exists a
  after p :: a responds to b
  after p until q :: exists a
  after p until q :: a responds to b
  while p :: exists a
  while p :: a responds to b
  
In this case we bound the time in which we expect the satisfying event to occur. For example

  global :: a responds to b 
      becomes
  global :: a respond to b within N (where N represents the number of computation steps we expect b to occur within) 

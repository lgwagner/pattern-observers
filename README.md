# pattern-observers
This repository captures the derived Lustre and Simulink Design Verifier (SLDV) synchronous observers for the 
specification patterns work at http://patterns.projects.cis.ksu.edu/ \n

This work only supports a subset of the patterns defined on the Specification Patterns website. \n

The supported scopes from the original work are: \n
  global \n
  before p \n
  after p \n
  after p until q \n
  between p and q \n
  while p (introduced in this work, it is a simplification of after p until not p) \n
  
The supported predicates from the original work are: \n
  always a \n
  exists a \n
  a precedes b \n
  a responds to b \n

Any combination of scope and predicate can be used to create a pattern. Some combinations of scope and predicate
express liveness conditions and accordingly cannot be verified using k-inductive tools (such as Kind or SLDV). 
These combinations are: \n

  global :: exists a \n
  global :: a responds to b \n
  after p :: exists a \n
  after p :: a responds to b \n
  after p until q :: exists a \n
  after p until q :: a responds to b \n
  while p :: exists a \n
  while p :: a responds to b \n
  
In this case we bound the time in which we expect the satisfying event to occur. For example \n

  global :: a responds to b \n
      becomes \n
  global :: a respond to b within N (where N represents the number of computation steps we expect b to occur within) \n
  

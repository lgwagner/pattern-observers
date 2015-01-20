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

=================================================================================
Copyright (c) 2012-2015, Rockwell Collins 
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:
    * Redistributions of source code must retain the above copyright
      notice, this list of conditions and the following disclaimer.
    * Redistributions in binary form must reproduce the above copyright
      notice, this list of conditions and the following disclaimer in the
      documentation and/or other materials provided with the distribution.
    * Neither the name of Rockwell Collins nor the names of its contributors 
      may be used to endorse or promote products derived from this software 
      without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL ROCKWELL COLLINS BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES
(INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES;
LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND
ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
(INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

THIS SOFTWARE WAS DEVELOPED WITH FUNDING BY AIRFORCE RESEARCH LABORATORIES AND 
IS APPROVED FOR PUBLIC RELEASE.  

DISTRIBUTION STATEMENT A: Approved for Public Release; 
Distribution Unlimited (Case Number: 88ABW-2015-0175)
=================================================================================

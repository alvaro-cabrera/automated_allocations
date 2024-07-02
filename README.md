# Automated Allocations Project Readme

## This repository is to work on the automated allocations project for my internship

The first step would be to generate the methodology to address this problem. It could be presented as follows: 

1. Define the problem
   - In this section, we need to decide what we need to achieve
   - Define the rules of the model
   - If needed, define a cost function
  
2. Find the data and the sources
  
3. Develop a Python Model to address the challenge
   - Tools that may help to address this challenge are Python [PuLP](https://coin-or.github.io/pulp/) and Google [OR Tools](https://github.com/google/or-tools/blob/main/examples/python/shift_scheduling_sat.py). This link for the [OR Tools](https://developers.google.com/optimization/scheduling/employee_scheduling?hl=es-419) can also be useful.
   - This would be a kind of linear programming task, and looking at workforce scheduling algorithms may be useful.
  
4. Solve the Python problem
5. Check if the solution is valid.
   - If it is valid, proceed
   - If it is not valid, look for the issue and repeat
6. Deploy

## A

1. Define de problem
   - Allocate the operators to the aircrafts in need of maintenance
   - Rules: 
      - Certifiers are usually assigned to aircrafts in that are in bays close to each other
      - Shifts are usually of 12 hours, some from 5am to 5pm, but it depends a bit (exact information in the roster?)
      - aaa

2. Find the data and the sources
   - Sources: 
      - Roster should have the personel and the corresponding certifications also (Andrea should give me access)
      - Amos is for workload (Mithu - I think is written like that- is the expert in dataplatform and Amos. I should speak with her afterwards)

3. Develop a Python Model to address the challenge
   - Link to the Python model created
   



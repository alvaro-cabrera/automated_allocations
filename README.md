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

![Image Description](/images/HoozN%20Excel%20Image.png)

1. Define de problem

   - Allocate the operators to the aircrafts in need of maintenance. At this stage we will focus just on the first column of the manpower section in the Allocations Excel, column O with the "Certifier" title. It is the most crucial manpower colum, and the hardest to fill. The other operators are easier to fill once we have the certifiers. Also, we will focus on Wide Body and Narrow Body, not with the 3rd parties

   - Rules:

      - Each certifier has certain certifications, indicated with X in the Hooz'N excel. They must be assigned to the aircrafts in which they have certifications

      - Certifiers are represented in $\color{lightskyblue}{\textsf{LIGHT BLUE}}$, Technicians are represented in $\color{gray}{\textsf{GRAY}}$, and Cat A certifiers are represented in $\color{blue}{\textsf{BLUE}}$. Ideally, they all should be assigned to planes in bays close to each other. Additionally, they all have a primary bay to which they are assigned (column G in the image, "Allocation Zone"). They should primary work on their assigned bay, but they can move to other bays if there is not enough operators or if they are the only ones with a given certification requirements. 

      - Moving from area 600 to area 200 or 700 can take approximately 20 minutes, so it is not recommended to do those movements.

      - 5 aircrafts per certifier would be the maximum, if possible.

      - Planes with long layovers usually have a lot of work to be done, so usually is not good to assign more than 1 or 2 of those per certifier. 

      - $\color{lightskyblue}{\textsf{CERTIFIERS}}$
         - Shift leaders (indicated as LE, and marked with grey in the Allocation sheet) should not be used except if we have already assigned everyone to 5 aircrafts, or if they are the only with a given needed certification. 
         - We may have an engineer coming from light and that is available to work in any bay. It is indicated as other in the Hooz'N sheet of manpower. 
         - "Regular" certifiers are indicated with the letter E

      - $\color{BLUE}{\textsf{CAT A CERTIFIERS}}$
         - Indicated with the letter T
         - They need to be both in arrival and departure, so they can't have 2 aircrafts with same arrival or departure time. If the aircrafts are close, they can be with a difference of 10 minutes in arrival and at least 20 or 30 minutes in departure, and that is ok.  They have limited approval level, so if there is a major issue, they will need to call a certifier. So, it is better not to assign them to too many aircrafts, better to assign the certifiers. They are marked in orange in the Allocation excel

      - Ideally, we should give 2 jobs per certifier per departure wave (1st departure wave is from 17 to 23, and 2nd departure wave is from 23:30 to 3:30 am). In the morning, those waves are from 5:30 to 11 and 12 to 4pm. On the day shift, on the first wave it is usually 3 aircrafts per certifier, as we tend to have a lot of aircrafts in the first morning wave. So, ideally, 2 aircrafts close to each other per wave per certifier.

      - If we have used every available certifier in a given zone already in approx. 5 aircrafts, we should get certifiers from other bays. 

      - Engineers night shift goes from 17:30 to 5:30 am and day shift goes from 5:30 to 17:30.

      - Certifiers can be assigned to more than 1 aircraft at the same time, as they are the ones that have to sign so they can sign on one aircraft and go to a close one to sign that one

      - Careful that the aircraft code (i.e, EIA) can be repeated in the same workpack allocation, as the plane can arrive more than 1 time per day. So, the unique key should be WP (column M)

   - Possible approach:

      1. "Translate" the aircraft code in the Allocation Sheet to the corresponding aircraft type. This should be done just once. 
         - BL_and BN_: 787-9
         - BM_: 787-10
         - EI_: A320 V2500
         - AE(A-J):321 V2500
         - AE(K-ONWARDS): 321 NEO
         - ET_: B777. Represented as B772 and B773 in Hooz'N. But there are not any B772 in Etihad, so actually an ET_ will always be a B773
         - DD_: B777F
         - AP_: A380
         - XW_: A350
      2. Remove any sick or leave operator from the Hooz'N Excel. Copy paste the B1 sheet of the Excel file (shown in the image), as in there we have all the information we will need: name, allocation zone, certifications, $\color{RED}{\textsf{shift?}}$ and operator type (LE, E, T). $\color{red}{\textsf{Anything else we should be looking here?}}$


$\color{RED}{\textsf{Questions}}$: 
   - What does the A/L3 in red indicate in the certifications?
   - Do we need to look at the B2 engineers at any point here?
   - What was special of the name in orange on the Hooz'N?
   - What does ADT mean in Bay? And which bay should it be?
      


      Sick leaves

2. Find the data and the sources
   - Sources: 
      - In the Roster we should have the personel and the corresponding certifications also (Andrea should give me access)
      - Amos is for workload (Mithu - I think is written like that- is the expert in dataplatform and Amos. I should speak with her afterwards)

3. Develop a Python Model to address the challenge
   - Link to the Python model created
   



# Files

###### *Your own csv* (or my External_Roster-FA22-COE_Responses.csv)

###### BLACK_BOX.ipynb
This file contains all of the functions/code to generate groups for you.

###### Group_Generator.ipynb
This file is a guide which collects the required inputs from you, then outputs a group assignment for you to vet.





# Group Generator

## Overview

#### INPUT:

CSV of students with their available meeting times and preferred partners
<br>
(and accompanying column names, keywords, and similar information).

#### BLACK BOX:.

(See Methodology, below).

#### OUTPUT:

Optimally sized groups which share a common meeting time and includes preferred partners whenever possible


### Methodology

We use an adapted version of the following:

https://stackoverflow.com/questions/67391919/algorithm-to-group-people-together-based-on-their-available-timeslots-calendar


Based on the number of students you have and the maximum number of groups you would like formed, calculate the optimal group sizes.

For each student, record which time slots are marked available and which partners are preferred.
<br>
Sort students from the least number of availabilities to the most.

For each time slot, record how many students are available at that time.
<br>
Sort time slots from the least number of availabilities to the most.

We connect students with their preferred partners; considering connections as transitive, we form connected components.
<br>
(Try to keep the connected components as large as possible, but especially try to keep the double-connections where two students both request to work with the other.)

Execute the following pseudocode:

`                                                                                                                                               `
>
while not an impossible grouping:
<br>
>>
remove 0, or 1, or 2, or... weak/single connections in order to make student groups more flexible
<br>
>>
if all weak/single connections are removed:
<br>
>>>
remove 0, or 1, or 2, or... strong/double connections in order to make student groups more flexible
<br>
>>
group the (smaller) connected components into Group 1, Group 2, ...
<br>
>>
fill Group 1, Group 2, ... with students who have few available times first, then with students who have many available times, as needed
<br>
(any student who cannot fit into an already established group goes on to establish a new group)
>>
if the number of groups exceeds the maximum number acceptable, or if a group size is too small/large:
<br>
>>>
this grouping is considered impossible and we will retry by removing even more connections than on this try
<br>
>
if that fails:
<br>
>>
randomly shuffle students/time slot and try the while loop again
<br>
>
if every attempt has still failed:
<br>
>>
accept the best recorded attempt

`                                                                                                                                               `


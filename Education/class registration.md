Required still for data science:
* Calc 3 - planned
* intro to ds - planned
* ML/DL - planned
* regression methods - planned
* applied stat learning - planned
* info visualization - planned
* principles of info data management - planned

7 cs electives:
* 198 - prin info data management - done
* 198 - systems programming - done
* 198 - data management for ds -done
* 730 - minds machines persons- planned
* 960 - reg methods - planned
* 198 - soft meth - planned
* 198 - intro ai


Spring 26:
* prin info data management
* intro ds
* info visualization
* soft meth

Summer:
* calc 3

Fall 2026:
* reg methods
* ML/DL
* 198 - intro ai

Spring 2027:
* applied stat learning
* minds machines





Veds class question:

code
```python
def ad_times():
	times = [15, 10, 20]
	max = 60
	dp = [0]*61
	dp[0] = 1
	
	for i in range(1, max+1):
		for t in times:
			if i-t >= 0:
				dp[i] += dp[i-j]
	return dp[max]
```

explanation rq:
u set an array of size 61 (first index is base case) and then you essentially compute how many ads would fit at each index. so 1-9 there wouldnt be anything. when i=10. there IS an ad that is 10 seconds. so here u do i-t. where i =10 and t=10 since there is a t in times which is 10 seconds. 10-10 = 0 which is the base case which we set to 1. and since 10-10 is >= 0 we set the 10th index of the array to be 1, meaning that there is 1 ad that can run if you were only given a 10 second interval.
Next, again, 11-14, nothing works cuz all combos of i-t give negative numbers except t=10. but you don't want the any ad to fit in the time frame. u want ads so that not a single second of the ad break is wasted. so even for the i=14, u cant fit the 10 second ad since the other 4 are wasted. this check is done by the dp array. since we set all the indices of the array to 0 except the base case, when we do i-t for i=14 and t=10, we get 4, but dp\[i-t] in this case gives dp\[4] which we set to 0 when we declared the array. 
Now continuously repeating this process, we only get sucesses at i=10, 15. now when we get to i=20, there are 2 possibilities. when we do the second for loop of t in times, for t=20, we have 1 solution wher we can have the 20 second ad run in the 20 second time frame. OR, we can have t=10, in which case it would run dp\[20] += dp\[20-10]. And as we saw in the first example, dp\[10] was set to be dp\[10] += dp\[10-10] which means dp\[10] is 1. so now in the dp\[20] iteration, you have 2 possibilities. either 1 20 second ad or 2 10 second ads. repeat this until t=60 and you get all the possible number of combos of ads you can have in 60 seconds.

recurrence is F(t) = F(t-10) + F(t-15) + F(t-20) for TOP DOWN APPROACH





One system that I use everyday that organizes and shares information is our course registration website. At Rutgers, the registration system displays available classes, professors, time slots, pre requisites, enrollment limits, and so much more. This system highlights a lot of information such as seats in the class and even scheduling conflicts, which encourages us students to ensure that our schedules made are optimal. However when doing so, it also makes some things invisible, for instance it doesn't show different professors and their teaching styles. One big tool is Rate My Professor which is useful for students and should be shown to students. Another thing is workload expectations, and student ratings of the class, which can influence student decisions. 

The viewpoint in the system is firstly administrative and institutional. It shows the priorities of the universities such as managing the enrollment capacity and preventing scheduling overlap, rather than giving the students a better experiene. Students who understand how the system works know to seek out help to advisors to optimize their schedules, but others are often left to struggle optimizing their schedule. Different users may experience the system differently because of this. A freshman student might be overwhelmed because they have no clue where anything is and have to search for everything manually which takes a lot of man hours. Whereas a experienced student like a senior will be cruising as they know where to access all information and who to contact for further assistance. Furthermore, the system doesn't favor worse cases like international students who may struggle even more navigating the new environment.

Veranex code: #### b9FsXycy
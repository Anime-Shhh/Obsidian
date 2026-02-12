aliases: [Interval Coloring]
Problem: Given a list of lectures and their start and end times, determine the least amount of lecture halls required such that all lectures can happen with the least amount of overlapping lectures. 
![[Pasted image 20251005213345.png]]

## [[Greedy Solution]]:
1. Sort all the lectures by their start times in increasing order.
2. Go through each lecture in the sorted list.
3. have a min heap which keeps the lecture with the earliest end time at the top(of all the lectures in the heap)
4. If there is no lecture hall being used, assign the lecture to a lecture hall.
5. If the current lecture's start time is after the end time of the top of the heap, remove that element/lecture and add the current lecture to that hall/heap. 
6. Once traversed through all the lectures, the depth/height of the heap is the amount of lecture halls you need
Essentially, you're keeping track of how many classes are happening simultaneously using the heap. If a class ends, that lecture hall is free and you can assign a new class to it

```pseudocode
lectures.sort(key=lambda x:x.start)
for l in lectures:
	if heap and l.start > heap[0].end:
		heap[0] = l # replace the top element with the new class
		#the heap will reorder itself by the earliest finish time at top
	else:
		heap.push(l) # a new lecture hall is needed
		
return height(heap)
```


**Proof**: If d is the depth of the heap, created by the greedy solution, then the number of lecture halls needed to minimize lecture hall usage for the given activities is d. The d'th lecture hall opened up because all the d-1 lecture halls were occupied and none of them had an 
end time <=  d'th lecture's start time. Since the list of classes was sorted by start time, we know that the d'th lecture has to start after all of the d-1 lectures. However, it does not mean that the d'th lecture also starts after one of the d-1 lecture ends. Since greedy uses a heap to keep track of the earliest finishing class among the d-1 classes, the greedy only needs to check if the d'th class starts >= d-1'th class in order to add it to that lecture hall. 

Let's say we had greedy solution which gave depth 4, while OPT, the optimal solution gave depth 3. 
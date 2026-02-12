1. Initialize dv = +infinity for each node v
2. Add all nodes v which is in V to a priority queue PQ, using dv as the key
3. Set ds = 0
4. while PQ is not empty:
	1. v = PQ.extractMin()
	2. for each u in V such that (v,u) in E:
		1. if u in PQ and dv + w(v,u) < dv:
			1. PQ.decreaseKey(u,dv + w(v,u))
			2. u.parent=v

Greedy Strategy:
Changes the for loop


dynamic:
Bellman ford algo
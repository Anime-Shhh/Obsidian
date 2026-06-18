![[image 2.png]]
1. Here is the analysis for each one:
    
    ### 1. $$\vec{r}(t) = \langle t\cos t, t\sin t, t \rangle$$
    
    - **Analysis:** We have $x = t\cos t$ and $y = t\sin t$. If we square them and add them together, we get $x^2 + y^2 = t^2\cos^2 t + t^2\sin^2 t = t^2(\cos^2 t + \sin^2 t) = t^2$.
    - Since $z = t$, we can substitute $z$ in to get **$x^2 + y^2 = z^2$**.
    - **Conclusion:** This is the equation of a **cone**. The curve is a spiral that gets wider at a constant, linear rate as it goes up the z-axis.
    - **Matches: Graph a** (the conical spiral expanding upwards).
    
    ### 2. $$\vec{r}(t) = \langle t\cos t, t\sin t, t^2 \rangle$$
    
    - **Analysis:** Just like the first one, $x = t\cos t$ and $y = t\sin t$ gives us $x^2 + y^2 = t^2$.
    - However, this time $z = t^2$. If we substitute that in, we get **$x^2 + y^2 = z$**.
    - **Conclusion:** This is a **paraboloid** (a bowl shape). It's also an expanding spiral, but because $z$ grows quadratically while the radius grows linearly, the vertical distance between the spiral loops stretches rapidly as it gets higher.
    - **Matches: Graph e** (Since we already matched the linear cone to 'a', this must be the missing graph you couldn't fit in the screenshot!).
    
    ### 
    
    3. $$\vec{r}(t) = \langle \cos t, \sin t, t \rangle$$
    
    - **Analysis:** Here, $x = \cos t$ and $y = \sin t$. Squaring and adding gives **$x^2 + y^2 = 1$**.
    - **Conclusion:** This means the curve is confined perfectly to a **cylinder** of radius 1 centered on the z-axis. Because $z = t$, the curve travels upward along the z-axis at a constant width.
    - **Matches: Graph b** (the uniform vertical helix standing upright).(1/2)
    
2. ### 
    
    4. $$\vec{r}(t) = \langle \cos t, t, \sin t \rangle$$
    
    - **Analysis:** Here, we have $x = \cos t$ and $z = \sin t$. Squaring and adding those gives **$x^2 + z^2 = 1$**.
    - **Conclusion:** This is also a cylinder of radius 1, but this one is centered on the **y-axis**. Since $y = t$, the curve travels horizontally along the y-axis.
    - **Matches: Graph c** (the uniform horizontal helix lying on its side).
    
    ### 
    
    5. $$\vec{r}(t) = \langle \cos t, \cos t, \sin t \rangle$$
    
    - **Analysis:** Look at the first two components: $x = \cos t$ and $y = \cos t$. This means **$x = y$** for all values of $t$. The entire curve must lie perfectly flat on the diagonal plane $x = y$.
    - Also, $x^2 + z^2 = \cos^2 t + \sin^2 t = 1$, which forms a closed loop. Because there isn't a variable growing infinitely (like $t$ by itself), it doesn't spiral open—it just loops back on itself.
    - **Matches: Graph d** (the single, closed, tilted elliptical loop).
    
     _**###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answer Summary:
    
    1. $\vec{r}(t) = [t\cos(t), t\sin(t), t]$ ➔**Graph a**
    
    2. $\vec{r}(t) = [t\cos(t), t\sin(t), t^2]$ ➔
    
    **Graph e**_(missing from screenshot)*
    
    3. $\vec{r}(t) = [\cos(t), \sin(t), t]$ ➔ **Graph b**
    4. $\vec{r}(t) = [\cos(t), t, \sin(t)]$ ➔ **Graph c**
    5. $\vec{r}(t) = [\cos(t), \cos(t), \sin(t)]$ ➔ **Graph d** (2/2)


## Q2 ![[image-1 2.png]]
### Step 1: Parameterize the cylinder ($x$ and $y$)

The first surface is the cylinder given by the equation: $$x^2 + y^2 = 36$$ If you look at this just in the $xy$-plane, it's the equation of a circle with a radius of $r = \sqrt{36} = 6$. The standard way to parameterize a circle of radius $r$ is using sine and cosine:

- $x(t) = r\cos(t)$
- $y(t) = r\sin(t)$

The problem specifically asks that the **$x(t)$ term contains a $\cos(t)$ term**, which perfectly matches our standard setup. So, we plug in our radius $r = 6$: $$x(t) = 6\cos(t)$$ $$y(t) = 6\sin(t)$$ _(Self-check: if we plug these back into the cylinder equation, we get $(6\cos t)^2 + (6\sin t)^2 = 36\cos^2 t + 36\sin^2 t = 36(\cos^2 t + \sin^2 t) = 36(1) = 36$. It works!)_

### Step 2: Parameterize the surface ($z$)

The second surface equation is: $$z = xy$$ Since the curve of intersection must exist on _both_ surfaces at the same time, the $x$, $y$, and $z$ values must satisfy both equations. Now that we know what $x$ and $y$ are in terms of $t$, we simply substitute them into the $z$ equation: $$z(t) = x(t) \cdot y(t)$$ $$z(t) = (6\cos(t)) \cdot (6\sin(t))$$ $$z(t) = 36\cos(t)\sin(t)$$ _(Note: Depending on your online homework platform, it might also accept the simplified version using the double-angle identity $\sin(2t) = 2\sin(t)\cos(t)$, which would make it $z(t) = 18\sin(2t)$. But $36\cos(t)\sin(t)$ is generally exactly what they are looking for directly out of the substitution)._ ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

**$x(t) =$ **`6\cos(t)`** $y(t) =$ **`6\sin(t)`** $z(t) =$** `36\cos(t)\sin(t)`


## Q3
![[image-2 2.png]]
### Step 1: Parameterize $x$ and $y$

Looking at the equation $x = e^y$, $x$ is already solved in terms of $y$. This makes $y$ the perfect candidate to just be our parameter $t$. Let's set $y$ to be exactly $t$: $$y(t) = t$$ Now, substitute $y = t$ back into the surface equation $x = e^y$ to find $x(t)$: $$x(t) = e^t$$ _(Note: We could have technically set $x = t$ which would make $y = \ln(t)$, but letting $y = t$ is much cleaner and avoids the restricted domain of the natural log!)_

### Step 2: Parameterize $z$

Now that we have $x$ and $y$ strictly in terms of $t$, we can find $z(t)$ by plugging both of them into the equation of the paraboloid: $$z = 3x^2 + y^2$$ Substitute $x(t) = e^t$ and $y(t) = t$: $$z(t) = 3(e^t)^2 + (t)^2$$ When you raise a power to a power, you multiply the exponents (so $(e^t)^2 = e^{2t}$): $$z(t) = 3e^{2t} + t^2$$ ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

**$x(t) =$ **`e^t`** $y(t) =$ **`t`** $z(t) =$** `3e^{2t} + t^2`

## Q4 ![[image-3 2.png]]
### Step 1: Analyze the $x$-component

$$x(t) = t^2$$

- **Constraint:** This is a polynomial (a parabola). You can square any real number without breaking any math rules (like dividing by zero or taking the square root of a negative).
- **Domain:** All real numbers. ($-\infty < t < \infty$)

### Step 2: Analyze the $y$-component

$$y(t) = \sqrt{t+4}$$

- **Constraint:** You cannot take the square root of a negative number. Therefore, the expression inside the square root must be greater than or equal to zero.
- $t + 4 \ge 0$
- Subtract 4 from both sides:
- **Domain:** **$t \ge -4$**

### Step 3: Analyze the $z$-component

$$z(t) = \sqrt{3-t}$$

- **Constraint:** Just like the $y$-component, the expression inside the square root must be greater than or equal to zero.
- $3 - t \ge 0$
- Add $t$ to both sides:
- $3 \ge t$ (which is the same as $t \le 3$)
- **Domain:** **$t \le 3$**

### Step 4: Find the intersection

Now we combine the constraints. The value of $t$ must satisfy all conditions simultaneously:

1. $t$ can be anything.
2. $t$ must be greater than or equal to $-4$.
3. $t$ must be less than or equal to $3$.

Putting it all together, $t$ must be between $-4$ and $3$, inclusive: $$-4 \le t \le 3$$ ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

Looking at the formatting on your screen ${ t \mid [\text{box 1}] \le t \le [\text{box 2}] }$:** Box 1: **`-4`** Box 2:** `3`

## Q5![[image-4 2.png]]
### Step 1: Multiply corresponding components

- **$\vec{i}$ components ($x$):** $(10\sin(t)) \cdot (2\sin(t)) = 20\sin^2(t)$
- **$\vec{j}$ components ($y$):** $(2\cos(t)) \cdot (10\cos(t)) = 20\cos^2(t)$
- **$\vec{k}$ components ($z$):** $(t^2) \cdot (t^3) = t^5$ _(Remember to add exponents when multiplying the same base!)_

### Step 2: Add them together

Now, set up the full dot product expression: $$\vec{r}(t) \cdot \vec{u}(t) = 20\sin^2(t) + 20\cos^2(t) + t^5$$

### Step 3: Simplify using trigonometric identities

Notice that both the $\sin^2(t)$ and $\cos^2(t)$ terms share a common factor of 20. Let's factor that out: $$= 20(\sin^2(t) + \cos^2(t)) + t^5$$ By the Pythagorean trigonometric identity, we know that $\sin^2(t) + \cos^2(t) = 1$. Substitute $1$ into the equation: $$= 20(1) + t^5$$ $$= 20 + t^5$$ _**###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answer to type in:**`20 + t^5`**_(or `t^5 + 20`, order doesn't matter!)*


## Q5![[image-5 2.png]]
### Step 1: Analyze the $x$-component

$$x(t) = t$$

- **Constraint:** This is just a linear variable $t$. There are no fractions or square roots, so any number is allowed.
- **Domain:** All real numbers. ($-\infty < t < \infty$)

### Step 2: Analyze the $y$-component

$$y(t) = \sqrt{t+3}$$

- **Constraint:** You cannot take the square root of a negative number. The expression inside the square root must be greater than or equal to zero.
- $t + 3 \ge 0$
- Subtract 3 from both sides:
- **Domain:** **$t \ge -3$**

### Step 3: Analyze the $z$-component

$$z(t) = \sqrt{2-t}$$

- **Constraint:** Again, the expression inside the square root must be greater than or equal to zero.
- $2 - t \ge 0$
- Add $t$ to both sides:
- $2 \ge t$ (which is the same as $t \le 2$)
- **Domain:** **$t \le 2$**

### Step 4: Find the intersection

Now we combine the constraints. The value of $t$ must satisfy all conditions simultaneously:

1. $t$ can be anything.
2. $t$ must be greater than or equal to $-3$.
3. $t$ must be less than or equal to $2$.

Putting it all together, $t$ must be between $-3$ and $2$, inclusive: $$-3 \le t \le 2$$ ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

Looking at the formatting on your screen ${ t \mid [\text{box 1}] \le t \le [\text{box 2}] }$:** Box 1: **`-3`** Box 2:** `2`
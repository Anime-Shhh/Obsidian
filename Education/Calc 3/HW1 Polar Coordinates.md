If given coordinates like $\frac{5\pi}{6}$ you can convert it to degrees by multiplying it by $\frac{180}{\pi}$ so an example would be $$\frac{5\pi}{6} * \frac{180}{\pi} = 150$$ which allows you to translate it into an exact degree angle

if $r$ in $(r, \theta)$ is negative, point it the other way. 

If you are given a polar coordinate$(r, \theta)$ then you are able to find 3 other polar coordinates that point to the same coordinate such as $(-r, -\theta)$   $(r, -\theta)$   $(-r, \theta)$ 

### Polar to Rectangular
To convert $(r, \theta) \rightarrow (x,y)$ you have the following
$$ x \rightarrow r\cos \theta ,   y \rightarrow r\sin \theta$$
### Rectangular to Polar

To convert $(x,y) \rightarrow (r, \theta)$ you have the following:
$$r=(\sqrt{x^2 + y^2}),\theta = \tan^{-1}(\frac{y}{x})$$
1. Based on the image provided, here is the step-by-step solution to find the correct integral for the area of the shaded region.
    
    ### 
    
    1. Identify the Formula for Polar Area
    
    The area of a region between two polar curves is given by the formula: $$Area = \int_{\alpha}^{\beta} \frac{1}{2} \left( [R_{\text{outer}}]^2 - [R_{\text{inner}}]^2 \right) d\theta$$
    
    ### 
    
2. Determine the Limits of Integration ($\alpha$ and $\beta$)
    
    We need to find the angles ($\theta$) where the shaded region begins and ends:
    
    - **Starting Angle ($\alpha$):** The region begins at the intersection of the two curves, which is point $B$. The coordinates for $B$ are given as $\left[3, \frac{\pi}{7}\right]$ (in $[r, \theta]$ format). Therefore, the starting angle is **$\frac{\pi}{7}$**.
    - **Ending Angle ($\beta$):** The region is bounded on the left by the positive vertical axis (the y-axis), where point $A$ lies. The angle for the positive y-axis is **$\frac{\pi}{2}$**.
    
    So, our limits of integration are from **$\theta = \frac{\pi}{7}$** to **$\theta = \frac{\pi}{2}$**.
    
    ### 
    
3. Identify the Outer and Inner Curves
    
    Looking at the shaded area between the angles $\frac{\pi}{7}$ and $\frac{\pi}{2}$:
    
    - The **outer curve** (further from the origin) is the solid top boundary: **$f(\theta)$**
    - The **inner curve** (closer to the origin) is the dashed bottom-right boundary: **$g(\theta)$**
    
    ### 
    
4. Construct the Integral
    
    Substitute these pieces into our polar area formula: $$Area = \int_{\frac{\pi}{7}}^{\frac{\pi}{2}} \frac{1}{2} \left( [f(\theta)]^2 - [g(\theta)]^2 \right) d\theta$$
    
    ### Conclusion
    
    Matching our derived formula with the given multiple-choice options, the correct choice is the **first option**: **☑ $\int_{\frac{\pi}{7}}^{\frac{\pi}{2}} \frac{1}{2} \left( [f(\theta)]^2 - [g(\theta)]^2 \right) d\theta$
    

![[image-4 1.png]]
1. ### Part 1: Which intervals correspond to one petal?
    
    **The Concept:** A single petal of a polar rose graph begins at the origin (where the radius $r = 0$) and ends the very next time the graph returns to the origin ($r = 0$). **Step 1: Find where $r = 0$** Set the equation to zero: $$0 = 9\sin(10\theta)$$ $$0 = \sin(10\theta)$$ We know that sine equals zero at integer multiples of $\pi$ (i.e., $0, \pi, 2\pi, 3\pi, \text{etc.}$): $$10\theta = 0, \pi, 2\pi, 3\pi, 4\pi \dots$$ **Step 2: Solve for $\theta$** Divide everything by 10 to find the exact angles where a petal starts and ends: $$\theta = 0, \frac{\pi}{10}, \frac{2\pi}{10}, \frac{3\pi}{10}, \frac{4\pi}{10} \dots$$ This tells us that **every interval of $\frac{\pi}{10}$** forms exactly one full petal. **Step 3: Evaluate the Multiple Choice Options** Let's check the size of the interval for each option:
    
    1. **$0 \le \theta \le \pi$**: This interval is length $\pi$. Since $\pi = \frac{10\pi}{10}$, this traces **10 petals**. (Do not check).
    2. **$0 \le \theta \le \frac{\pi}{10}$**: This interval is length $\frac{\pi}{10}$. This traces exactly **1 petal**. (![✅](https://discord.com/assets/43b7ead1fb91b731.svg) **CHECK THIS**)
    3. **$0 \le \theta \le 2\pi$**: This interval is length $2\pi$. This traces all **20 petals**. (Do not check).
    4. **$\frac{13\pi}{10} \le \theta \le \frac{7\pi}{5}$**: Let's find a common denominator for the second bound: $\frac{7\pi}{5} = \frac{14\pi}{10}$. So the interval is from $\frac{13\pi}{10}$ to $\frac{14\pi}{10}$. The difference between them is exactly $\frac{\pi}{10}$. Therefore, this traces exactly **1 petal**. (![✅](https://discord.com/assets/43b7ead1fb91b731.svg) **CHECK THIS**)
    
    **Answer for Part 1: Check the second and fourth boxes.** --- (1/2)
    
2. ### Part 2: Find the Area of One Petal
    
    **The Concept:** The area of a polar region is found using the integral: $\text{Area} = \int_{\alpha}^{\beta} \frac{1}{2} r^2 , d\theta$ **Step 1: Set up the integral** We can use the limits for the first petal we found above ($0$ to $\frac{\pi}{10}$) and our equation $r = 9\sin(10\theta)$: $$\text{Area} = \int_{0}^{\frac{\pi}{10}} \frac{1}{2} [9\sin(10\theta)]^2 , d\theta$$ **Step 2: Simplify and apply the power-reduction identity** First, square the $9$ and the sine: $$\text{Area} = \int_{0}^{\frac{\pi}{10}} \frac{81}{2} \sin^2(10\theta) , d\theta$$ Next, use the trigonometric identity $\sin^2(x) = \frac{1 - \cos(2x)}{2}$. Here, $x = 10\theta$, so $2x = 20\theta$: $$\text{Area} = \frac{81}{2} \int_{0}^{\frac{\pi}{10}} \frac{1 - \cos(20\theta)}{2} , d\theta$$ $$\text{Area} = \frac{81}{4} \int_{0}^{\frac{\pi}{10}} (1 - \cos(20\theta)) , d\theta$$ **Step 3: Integrate and evaluate** The integral of $1$ is $\theta$. The integral of $-\cos(20\theta)$ is $-\frac{\sin(20\theta)}{20}$. $$\text{Area} = \frac{81}{4} \left[ \theta - \frac{\sin(20\theta)}{20} \right]_{0}^{\frac{\pi}{10}}$$ Evaluate at the upper limit ($\frac{\pi}{10}$): $$\frac{\pi}{10} - \frac{\sin(20 \cdot \frac{\pi}{10})}{20} \implies \frac{\pi}{10} - \frac{\sin(2\pi)}{20} \implies \frac{\pi}{10} - 0 = \frac{\pi}{10}$$ Evaluate at the lower limit ($0$): $$0 - \frac{\sin(20 \cdot 0)}{20} \implies 0 - \frac{\sin(0)}{20} = 0$$ Subtract the lower bound result from the upper bound result: $$\text{Area} = \frac{81}{4} \left( \frac{\pi}{10} - 0 \right) = \frac{81\pi}{40}$$ **Answer for Part 2:** Type this into the box at the bottom: **`(81*pi)/40`** _(or $\frac{81\pi}{40}$ if the platform has a fraction tool)_ (2/2)

![[image-5 1.png]]

### 

1. Identify the Arc Length Formula for Polar Curves

The length $L$ of a curve $r = f(\theta)$ from $\theta = a$ to $\theta = b$ is given by the formula: $$L = \int_{a}^{b} \sqrt{r^2 + \left(\frac{dr}{d\theta}\right)^2} , d\theta$$
### 

2. Find the necessary components

We are given:

- $r = 12\theta^2$
- Limits: $a = 0$ to $b = 7$

First, find the derivative $\frac{dr}{d\theta}$: $$\frac{dr}{d\theta} = 24\theta$$ Next, square both $r$ and $\frac{dr}{d\theta}$: $$r^2 = (12\theta^2)^2 = 144\theta^4$$ $$\left(\frac{dr}{d\theta}\right)^2 = (24\theta)^2 = 576\theta^2$$

### 

3. Set up the Integral

Plug these into the formula: $$L = \int_{0}^{7} \sqrt{144\theta^4 + 576\theta^2} , d\theta$$ Factor out the common term $144\theta^2$ from inside the square root: $$L = \int_{0}^{7} \sqrt{144\theta^2(\theta^2 + 4)} , d\theta$$ Since $\theta$ is positive on the interval $[0, 7]$, we can pull $144\theta^2$ out of the square root as $12\theta$: $$L = \int_{0}^{7} 12\theta\sqrt{\theta^2 + 4} , d\theta$$

### 

4. Integrate using U-Substitution

Let $u = \theta^2 + 4$. Then $du = 2\theta , d\theta$, which means $\theta , d\theta = \frac{1}{2} du$. Now, change the limits of integration to be in terms of $u$:

- When $\theta = 0 \implies u = 0^2 + 4 = 4$
- When $\theta = 7 \implies u = 7^2 + 4 = 49 + 4 = 53$

Substitute these into the integral: $$L = \int_{4}^{53} 12 \left(\frac{1}{2}\right) \sqrt{u} , du$$ $$L = \int_{4}^{53} 6 u^{1/2} , du$$

### 

5. Evaluate the Integral

Apply the power rule for integration: $$L = \left[ 6 \cdot \frac{2}{3} u^{3/2} \right]_{4}^{53}$$ $$L = \left[ 4 u^{3/2} \right]_{4}^{53}$$ Plug in the upper and lower limits: $$L = 4(53)^{3/2} - 4(4)^{3/2}$$ Simplify the second term ($4^{3/2}$ is exactly $(\sqrt{4})^3 = 2^3 = 8$): $$L = 4(53)^{3/2} - 4(8)$$ $$L = 4(53)^{3/2} - 32$$

### Final Answer

Type exactly this into the box: **`4(53)^(3/2) - 32`** (1/2)


![[image-6 1.png]]
explanation below:
1. ### Step 1: Simplifying the fraction (Where the 1/4 came from)
    
    Before actually integrating, the expression inside the integral on Line 1 needs a little cleanup. Let's look at the third term: $$ \frac{1}{2} \cdot \frac{1 - \cos(2\theta)}{2} $$ When you multiply fractions, you multiply the numerators straight across and the denominators straight across. You can rewrite the second part as $\frac{1}{2}(1 - \cos(2\theta))$. So, you have: $$ \frac{1}{2} \cdot \frac{1}{2} (1 - \cos(2\theta)) = \frac{1}{4} (1 - \cos(2\theta)) $$ That is exactly how the $\frac{1}{2}$ turned into a $\frac{1}{4}$ for the next step! So, the full integral you are trying to solve is: $$ \int_0^{2\pi} \left( 2 + 2\sin(\theta) + \frac{1}{4}(1 - \cos(2\theta)) \right) d\theta $$
    
    ### Step 2: Performing the Integration (Moving to Line 2)
    
    Now, we integrate each of the three pieces individually with respect to $\theta$:
    
    1. **First term ($2$):** The integral of a constant $2$ is just $2\theta$.
    2. **Second term ($2\sin\theta$):** The integral of $\sin\theta$ is $-\cos\theta$. So, the integral of $2\sin\theta$ is $-2\cos\theta$.
    3. **Third term ($\frac{1}{4}(1 - \cos(2\theta))$):**
        
        - Leave the constant $\frac{1}{4}$ on the outside.
        - Inside the parentheses, integrate $1$ to get $\theta$.
        - Integrate $\cos(2\theta)$. Because of the $2$ inside, you use a mini u-substitution (or reverse chain rule), dividing by the derivative of $2\theta$. The integral of $\cos(2\theta)$ becomes $\frac{\sin(2\theta)}{2}$.
        - Putting this piece together gives: $\frac{1}{4} \left( \theta - \frac{\sin(2\theta)}{2} \right)$.
        -to integrate the expression $(1 - \cos(2\theta))$, we break it into two separate, smaller integrals: $$ \int 1 , d\theta \quad - \quad \int \cos(2\theta) , d\theta $$ The first part is easy: the integral of $1$ is just $\theta$. For the second part, $\int \cos(2\theta) , d\theta$, we must use **u-substitution** because the inside of the cosine function is $2\theta$, not just $\theta$. Here is the exact step-by-step for that u-substitution: **Step 1: Pick your "$u$".** You always pick the "inside" function. Here, it's the $2\theta$ inside the cosine. Let $u = 2\theta$ **Step 2: Find the derivative, "$du$".** Take the derivative of $u$ with respect to $\theta$. $\frac{du}{d\theta} = 2$ **Step 3: Solve for $d\theta$.** We need to swap out the $d\theta$ in our original integral, so we isolate it. Multiply both sides by $d\theta$: $du = 2 * d\theta$ Divide by 2: $d\theta = \frac{du}{2}$ **Step 4: Substitute everything into the integral.** Now we swap out the $2\theta$ and the $d\theta$ in our original integral ($\int \cos(2\theta) , d\theta$) with our new $u$ terms: $$ \int \cos(u) \cdot \frac{du}{2} $$ **Step 5: Pull out the constant and integrate.** That divide-by-2 is just a constant multiplier ($\frac{1}{2}$), so you can pull it to the front of the integral: $$ \frac{1}{2} \int \cos(u) , du $$ Now, take the integral of cosine, which is sine: $$ \frac{1}{2} \sin(u) $$ **Step 6: Substitute the original variable back in.** Replace the $u$ with $2\theta$: $$ \frac{1}{2} \sin(2\theta) \quad \text{which is exactly the same as} \quad \frac{\sin(2\theta)}{2} $$

### Putting it back together

When we go back to our original split integral: $$ \int 1 , d\theta \quad - \quad \int \cos(2\theta) , d\theta $$ We plug in the answers we got for both parts: $$ \theta - \frac{\sin(2\theta)}{2} $$
        
    
    Putting all three integrated pieces together gives us exactly what is written on Line 2: (1/3)
    
2. $$ \left[ 2\theta - 2\cos(\theta) + \frac{1}{4}\left(\theta - \frac{\sin(2\theta)}{2}\right) \right]_0^{2\pi} $$
    
    ### Step 3: Evaluating the Bounds (Moving to Line 3)
    
    Now we apply the Fundamental Theorem of Calculus: **Plug in the upper bound ($2\pi$), plug in the lower bound ($0$), and subtract.** **Plugging in $2\pi$ (The First Half):**
    
    - $2(2\pi) = 4\pi$
    - $-2\cos(2\pi)$
    - $\frac{1}{4}\left(2\pi - \frac{\sin(4\pi)}{2}\right)$. Because $\sin(4\pi)$ is exactly $0$, the $\sin$ term just vanishes completely, leaving only $\frac{1}{4}(2\pi)$.
    
    _(This matches the first half of Line 3)._ **Plugging in $0$ (The Second Half):**
    
    - $2(0) = 0$
    - $-2\cos(0)$
    - $\frac{1}{4}\left(0 - \frac{\sin(0)}{2}\right)$. Because $\sin(0)$ is exactly $0$, this entire third term just becomes $\frac{1}{4}(0)$.
    
    _(This matches the second half of Line 3)._ Subtract the lower bound from the upper bound to get Line 3: $$ \left( 4\pi - 2\cos(2\pi) + \frac{1}{4}(2\pi) \right) - \left( 0 - 2\cos(0) + \frac{1}{4}(0) \right) $$
    
    ### Step 4: Simplifying the Trigonometry (Moving to Line 4)
    
    Now we just evaluate the basic cosine values and simplify the algebra:
    
    - We know that $\cos(2\pi) = 1$. So, $-2\cos(2\pi)$ becomes $-2(1)$.
    - We know that $\cos(0) = 1$. So, $-2\cos(0)$ becomes $-2(1) = -2$.
    - In the fractions, $\frac{1}{4}(2\pi)$ simplifies to $\frac{2\pi}{4}$, which reduces to $\frac{\pi}{2}$.
    
    Let's plug those simplified numbers into our Line 3 expression: $$ \left( 4\pi - 2(1) + \frac{\pi}{2} \right) - \left( 0 - 2(1) + 0 \right) $$ Finally, distribute the negative sign into that second group of parentheses. The $0$s drop out, and you are left subtracting a $-2$. Subtracting a negative is the same as adding a positive: $-(-2) = +2$. This brings us perfectly to the final line written in the image: $$ 4\pi - 2(1) + \frac{\pi}{2} + 2 $$
    
    ### (Bonus) The Final Answer (2/3)
    
2. If you were to finish solving the problem from that last line, the $-2(1)$ and the $+2$ would perfectly cancel each other out. You would be left with: $$ 4\pi + \frac{\pi}{2} $$ Finding a common denominator ($8\pi/2 + \pi/2$) gives the final answer: **$$ \frac{9\pi}{2} $$** (3/3)

# Homework 2
2. To find the center and radius of a sphere from an expanded equation, we need to convert it into the **standard form of a sphere**: **$(x - h)^2 + (y - k)^2 + (z - l)^2 = r^2$** Where $(h, k, l)$ is the center, and $r$ is the radius. Here is the step-by-step breakdown:
    ### Step 1: Group the terms and move the constant
    
    Start with your original equation: $x^2 - 2x + y^2 + 4y + z^2 + 8z + 17 = 0$ First, group the $x$'s, $y$'s, and $z$'s together, and subtract the constant (17) to move it to the right side of the equals sign: $(x^2 - 2x) + (y^2 + 4y) + (z^2 + 8z) = -17$
    
    ### Step 2: Complete the square for each variable
    
    To complete the square for a grouped expression like $x^2 + bx$, you take half of the coefficient $b$, square it, and add it inside the parentheses. **Remember to add that same number to the right side of the equation** to keep it balanced.
    
    - **For $x$:** The coefficient is $-2$. Half of $-2$ is $-1$. Squared is **$1$**.
    - **For $y$:** The coefficient is $4$. Half of $4$ is $2$. Squared is **$4$**.
    - **For $z$:** The coefficient is $8$. Half of $8$ is $4$. Squared is **$16$**.
    
    Add these inside their respective groups and to the right side: $(x^2 - 2x + \mathbf{1}) + (y^2 + 4y + \mathbf{4}) + (z^2 + 8z + \mathbf{16}) = -17 + \mathbf{1} + \mathbf{4} + \mathbf{16}$
    
    ### Step 3: Write the equation in standard form
    
    Now, simplify the right side ($-17 + 1 + 4 + 16 = 4$) and rewrite each of the groups on the left as a perfect square binomial (using the halved numbers from Step 2): **$(x - 1)^2 + (y + 2)^2 + (z + 4)^2 = 4$** _(This is what goes in your first input box!)_
    
    ### Step 4 & 5: Find the Center and Radius
    
    Now we just match our equation to the standard form: $(x - h)^2 + (y - k)^2 + (z - l)^2 = r^2$. Remember to flip the signs for the center! (1/2)
    
3. - **Center $(h, k, l)$:** Looking at $(x - 1), (y + 2), (z + 4)$, the center is **$(1, -2, -4)$**.
    - **Radius $(r)$:** Since $r^2 = 4$, taking the square root gives us a radius of **$2$**.
    
    ### Summary of your answers:
    
    1. **Equation:** `(x - 1)^2 + (y + 2)^2 + (z + 4)^2 = 4`
    2. **Center:** `(1, -2, -4)`
    3. **Radius:** `2`
    
    Let me know if any part of the completing-the-square process feels tricky! (2/2)

## Q1 ![[image-15 1.png]]
1. The trick for most of these is to algebraically manipulate the equation until you can make clean substitutions using those three rules. The instruction "no radicals" means you need to square things if a square root ($\sqrt{x^2+y^2}$) shows up. Here is the step-by-step for all four: ---
    
    ### **a) $r = 3\cos(\theta)$**
    
    **Goal:** We have a $\cos(\theta)$, but we need an $r\cos(\theta)$ to turn it into an $x$.
    
    1. Multiply both sides of the equation by $r$:$r \cdot r = 3 \cdot r\cos(\theta)$, $r^2 = 3r\cos(\theta)$
    2. Now substitute $r^2$ with $(x^2 + y^2)$ and $r\cos(\theta)$ with $x$:**$x^2 + y^2 = 3x$**
    
    ### **b) $r = 10$**
    
    **Goal:** We need $r^2$ to substitute it directly for $(x^2 + y^2)$.
    
    1. Square both sides of the equation:$r^2 = 10^2$$r^2 = 100$
    2. Substitute $r^2$:**$x^2 + y^2 = 100$**
    
    _(This makes sense logically: $r=10$ is a circle with a radius of 10, which matches the standard circle equation $x^2 + y^2 = r^2$)_
    
    ### **c) $r = -2(1 + \cos(\theta))$**
    
    **Goal:** This one is a bit trickier because of the "no radicals" rule.
    
    1. First, distribute the $-2$:$r = -2 - 2\cos(\theta)$
    2. Multiply the entire equation by $r$ to turn the $\cos(\theta)$ into an $x$:$r^2 = -2r - 2r\cos(\theta)$
    3. Substitute what we know ($r^2 = x^2 + y^2$ and $r\cos(\theta) = x$):$x^2 + y^2 = -2r - 2x$
    4. Move the $x$ terms to the left to isolate the $-2r$:$x^2 + y^2 + 2x = -2r$
    5. _Here is the catch:_ $r$ is technically $\sqrt{x^2 + y^2}$, which is a radical. To get rid of it, **square both sides** of the equation:$(x^2 + y^2 + 2x)^2 = (-2r)^2$$(x^2 + y^2 + 2x)^2 = 4r^2$
    6. Substitute $r^2$ one last time:**$(x^2 + y^2 + 2x)^2 = 4(x^2 + y^2)$**
    
    ### **d) $\theta = \frac{3\pi}{4}$** (1/2)
    
2. **Goal:** When you only have $\theta$, you want to introduce tangent, because $\tan(\theta) = \frac{y}{x}$.
    
    1. Take the tangent of both sides:$\tan(\theta) = \tan(\frac{3\pi}{4})$
    2. We know from the unit circle that $\tan(\frac{3\pi}{4})$ (which is in Quadrant II) equals $-1$. $\tan(\theta) = -1$
    3. Substitute $\tan(\theta)$ with $\frac{y}{x}$:$\frac{y}{x} = -1$
    4. Multiply by $x$ to clean it up:**$y = -x$** (2/2)

## Q2 ![[image-16 1.png]]
1. ### The Core Problem:
    
    Normally, to find a slope, you need $y$ and $x$ so you can find how much $y$ changes when $x$ changes ($\frac{\text{Change in } Y}{\text{Change in } X}$). But polar equations only give us $r$ (distance from center) and $\theta$ (angle). If you take the derivative of $r$, you don't get the slope of the graph—you just find out how fast the radius is growing. **The Solution:** We use our translation bridge to create $y$ and $x$ equations out of thin air!
    1. **$y = r \cdot \sin(\theta)$**
    2. **$x = r \cdot \cos(\theta)$**
    Instead of plugging in $y$ and $x$, we plug our entire equation ($r = 1 - \sin(\theta)$) into those bridges. ---
    ### **Part A) Finding the slope and the point at $\theta = \frac{\pi}{4}$**
    **
    3. Find the point first (The easy part):
    **The problem asks for the point at $\theta = \frac{\pi}{4}$. All we do is plug that angle into our equation to find $r$.
    - $r = 1 - \sin(\frac{\pi}{4})$
    - $r = 1 - \frac{\sqrt{2}}{2}$
    - **The Polar Point is:** $(r, \theta) =$ **$(1 - \frac{\sqrt{2}}{2}, \frac{\pi}{4})$**
    **
    1. Set up our $Y$ and $X$ Equations:
    **Let's plug our $r$ into the bridge equations and distribute them so they are easier to take derivatives of.
    - **$y$ equation:** $y = (1 - \sin\theta) \cdot \sin\theta \implies$ **$y = \sin\theta - \sin^2\theta$**
    - **$x$ equation:** $x = (1 - \sin\theta) \cdot \cos\theta \implies$ **$x = \cos\theta - \sin\theta\cos\theta$**
    
    **
    
    3. Build the "Slope Machine":
    
    **Slope is $\frac{\text{Derivative of } y}{\text{Derivative of } x}$. Let's take the derivatives of the two equations we just made.
    
    - **Top of fraction (Derivative of $y$):** (1/3)
    
2. The derivative of $\sin\theta$ is $\cos\theta$. For $\sin^2\theta$, we use the chain rule to get $2\sin\theta\cos\theta$. _Top =_ **$\cos\theta - 2\sin\theta\cos\theta$**
    
    - **Bottom of fraction (Derivative of $x$):** The derivative of $\cos\theta$ is $-\sin\theta$. For $\sin\theta\cos\theta$, we use the product rule to get $\cos^2\theta - \sin^2\theta$._Bottom =_ **$-\sin\theta - \cos^2\theta + \sin^2\theta$**
    
    4. Plug in $\theta = \frac{\pi}{4}$ to find the exact slope:
    
    **At $\frac{\pi}{4}$, both sine and cosine equal $\frac{\sqrt{2}}{2}$.
    
    - **Top:** $\frac{\sqrt{2}}{2} - 2(\frac{\sqrt{2}}{2})(\frac{\sqrt{2}}{2}) \implies \frac{\sqrt{2}}{2} - 1$
    - **Bottom:** $-\frac{\sqrt{2}}{2} - (\frac{\sqrt{2}}{2})^2 + (\frac{\sqrt{2}}{2})^2 \implies -\frac{\sqrt{2}}{2} - \frac{1}{2} + \frac{1}{2} \implies -\frac{\sqrt{2}}{2}$
    
    Divide the Top by the Bottom: $\text{Slope} = \frac{\frac{\sqrt{2}}{2} - 1}{-\frac{\sqrt{2}}{2}}$ _(Multiply top and bottom by 2, then by $\sqrt{2}$ to clean up the ugly fractions)_ **Final Slope = $\sqrt{2} - 1$** ---
    
    ### **Part B) Finding Horizontal and Vertical Tangent Lines**
    Think about what a fraction is.
    
    - If a line is **Horizontal**, its slope is exactly $0$. The only way a fraction equals $0$ is if the **Top is $0$**.
    - If a line is **Vertical**, its slope is infinite (like a wall). The only way a fraction becomes infinite is if you divide by zero, meaning the **Bottom is $0$**.
    
    4. Horizontal Tangents (Set the Top = 0)
    
    **Top: $\cos\theta - 2\sin\theta\cos\theta = 0$ Let's factor out the cosine: $\cos\theta \cdot (1 - 2\sin\theta) = 0$ This gives us two separate mini-equations to solve:
    
    - $\cos\theta = 0 \implies \theta =$ **$\frac{\pi}{2}, \frac{3\pi}{2}$**
    - $1 - 2\sin\theta = 0 \implies \sin\theta = \frac{1}{2} \implies \theta =$ **$\frac{\pi}{6}, \frac{5\pi}{6}$**
    
    **
    4. Vertical Tangents (Set the Bottom = 0)
    **Bottom: $-\sin\theta - \cos^2\theta + \sin^2\theta = 0$ (2/3)
1. _(Pro-tip: To solve this, change $\cos^2\theta$ into $(1 - \sin^2\theta)$ so everything in the equation is a sine!)_ $-\sin\theta - (1 - \sin^2\theta) + \sin^2\theta = 0$ $2\sin^2\theta - \sin\theta - 1 = 0$ This is just a hidden quadratic equation! Imagine $\sin\theta$ is just the letter $U$: $2U^2 - U - 1 = 0$ This factors into: $(2U + 1)(U - 1) = 0$ So, our two mini-equations are:
    - $\sin\theta = 1 \implies \theta =$ **$\frac{\pi}{2}$**
    - $\sin\theta = -\frac{1}{2} \implies \theta =$ **$\frac{7\pi}{6}, \frac{11\pi}{6}$**
    **
    3. Wait, there's a crash! ($\theta = \frac{\pi}{2}$)
    **Notice that $\theta = \frac{\pi}{2}$ made _both_ the Top and the Bottom zero at the same time ($\frac{0}{0}$). This means the graph comes to a sharp, stabbing point (called a cusp) at that spot. In calculus, if you do deeper limit math on this specific point, the tangent line actually turns out to be **vertical**, not horizontal.**
    
    4. The Final Answer (Find the points)
    **The question asks for the "points on the graph", so we just plug our winning angles back into the original equation ($r = 1 - \sin\theta$) to get the $(r, \theta)$ coordinates! **Horizontal Points:**
    - At $\theta = \frac{\pi}{6}$: $r = 1 - \frac{1}{2} = \frac{1}{2} \implies$ **$(\frac{1}{2}, \frac{\pi}{6})$**
    - At $\theta = \frac{5\pi}{6}$: $r = 1 - \frac{1}{2} = \frac{1}{2} \implies$ **$(\frac{1}{2}, \frac{5\pi}{6})$**
    - At $\theta = \frac{3\pi}{2}$: $r = 1 - (-1) = 2 \implies$ **$(2, \frac{3\pi}{2})$**
    
    **Vertical Points:**
    - At $\theta = \frac{\pi}{2}$: $r = 1 - 1 = 0 \implies$ **$(0, \frac{\pi}{2})$**
    - At $\theta = \frac{7\pi}{6}$: $r = 1 - (-\frac{1}{2}) = \frac{3}{2} \implies$ **$(\frac{3}{2}, \frac{7\pi}{6})$**
    - At $\theta = \frac{11\pi}{6}$: $r = 1 - (-\frac{1}{2}) = \frac{3}{2} \implies$ **$(\frac{3}{2}, \frac{11\pi}{6})$** (3/3)


## Q3 ![[image-17 1.png]]
1. ### The Master Formula
    
    In normal $x,y$ math, area is $\int y , dx$ (base $\times$ height). But in polar coordinates, we are sweeping an angle (like a radar sweep), so the formula for the area of a polar sector is: $$ A = \frac{1}{2} \int_{\alpha}^{\beta} r^2 , d\theta $$ To solve this problem, we need two things:
    
    1. **The Limits:** We need to find $\alpha$ and $\beta$ (the starting and ending angles of the loop).
    2. **The Integral:** Plug in our $r$ and calculate.
    
    _**### Step 1: Find the limits of integration (and explain how)
    
    The question asks you to "explain how you got them." Here is the exact logic you need: Think about drawing a single petal of a flower. Your pen starts at the center point (the origin), draws the outward loop, and returns back to the center point. At the origin, the radius is zero ($r = 0$). Therefore,** to find where a single loop begins and ends, we must find the angles ($\theta$) where $r = 0$.** Let's set our equation to 0: $$ 2\cos(3\theta) = 0 $$ $$ \cos(3\theta) = 0 $$ Now, ask yourself:_When does the cosine of an angle equal zero?* Cosine is $0$ at $\frac{\pi}{2}$ and $-\frac{\pi}{2}$. So we set the _inside_ of our cosine ($3\theta$) equal to those angles: $$ 3\theta = -\frac{\pi}{2} \quad \text{and} \quad 3\theta = \frac{\pi}{2} $$ Now, divide by 3 to solve for $\theta$: $$ \theta = -\frac{\pi}{6} \quad \text{and} \quad \theta = \frac{\pi}{6} $$ **Your exact limits of integration are $\alpha = -\frac{\pi}{6}$ and $\beta = \frac{\pi}{6}$.** ***
    
    ### Step 2: Set up the Integral
    
    Now we take our limits and our $r$ equation, and plug them into the Area formula: (1/2)
    
2. $$ A = \frac{1}{2} \int_{-\frac{\pi}{6}}^{\frac{\pi}{6}} (2\cos(3\theta))^2 , d\theta $$ Let's simplify that a little bit before putting it in a calculator. Square the $2$ and the $\cos$: $$ A = \frac{1}{2} \int_{-\frac{\pi}{6}}^{\frac{\pi}{6}} 4\cos^2(3\theta) , d\theta $$ Pull the $4$ out to the front ($\frac{1}{2} \cdot 4 = 2$): $$ A = 2 \int_{-\frac{\pi}{6}}^{\frac{\pi}{6}} \cos^2(3\theta) , d\theta $$ ***
    
    ### Step 3: "Use technology to integrate"
    
    The prompt explicitly tells you not to do the final integration by hand (which is nice, because integrating $\cos^2$ requires messy half-angle identities!). You can punch that exact simplified integral into a graphing calculator (like a TI-84) or an online tool like Desmos or WolframAlpha. *Note: Make sure your calculator is in** Radian mode**!* If you type it in correctly, the "technology" will spit out the final exact area: $$ A = \frac{\pi}{3} $$** (If you get a decimal around $1.047$, that is $\frac{\pi}{3}$!)** Does that make sense? Let me know if you want me to explain the algebra or the radar-sweep concept in more detail! (2/2)

## Q4 ![[image-18 1.png]]
1. To find the center and radius of a sphere, we need to make our messy equation look like the **Standard "Blueprint" Equation for a Sphere**. Here is the blueprint: $$ (x - h)^2 + (y - k)^2 + (z - l)^2 = r^2 $$ Once the equation looks exactly like that:
    
    - The **Center** is just the numbers inside the parentheses: $(h, k, l)$. _(Note: The signs flip! A plus becomes a minus, and a minus becomes a plus)._
    - The **Radius** is the square root of the number on the far right ($r$).
    
    Right now, your equation is fully expanded out: $$ x^2 + y^2 + z^2 + 2x - y = 0 $$ To pack it back into those nice parentheses, we use an algebra trick called **"Completing the Square."** Let's do it step-by-step. ***
    
    ### Step 1: Group the letters together
    
    First, let's rearrange the equation so the $x$'s are next to each other, the $y$'s are next to each other, and the $z$'s are together. Let's leave a little blank space after each group. $$ (x^2 + 2x + ___) + (y^2 - y + ___) + z^2 = 0 $$ _(Notice $z^2$ is all by itself because there isn't a regular $z$ term in the problem)._ ***
    
    ### Step 2: Complete the square for the $x$ group
    
    We want to figure out what magic number goes in the blank space so that $(x^2 + 2x + ___)$ collapses into a perfect parenthesis $(x + \text{something})^2$. Here is the 2-step rule for the magic number:
    
    1. Take the number attached to the regular $x$ (which is $2$) and **cut it in half**. (Half of $2$ is $1$).
    2. **Square that result.** ($1^2 = 1$).
    
    So, our magic number is $1$. We add $1$ inside the $x$-group. **Crucial Algebra Rule:** If you add a number to the left side of the equals sign, you _must_ add it to the right side to keep it balanced! $$ (x^2 + 2x + \mathbf{1}) + (y^2 - y + ___) + z^2 = 0 + \mathbf{1} $$ (1/2)
    
2. Now, that $x$-group collapses perfectly. The number inside the factored parenthesis is always that "cut-in-half" number (which was $+1$): $$ (x + 1)^2 $$_**
    
    ### Step 3: Complete the square for the $y$ group
    
    Now let's look at $(y^2 - 1y + ___)$.
    
    1. Take the number attached to the regular $y$ (which is $-1$) and
    
    **cut it in half**. (Half of $-1$ is $-\frac{1}{2}$). 2.** Square that result. **$\left(-\frac{1}{2}\right)^2 = \frac{1}{4}$. Add $\frac{1}{4}$ to the $y$-group, and add it to the right side of the equals sign! $$ (x + 1)^2 + \left(y^2 - y + \mathbf{\frac{1}{4}}\right) + z^2 = 1 + \mathbf{\frac{1}{4}} $$ Now collapse the $y$-group. Again, the number inside the parenthesis is the "cut-in-half" number ($-\frac{1}{2}$): $$ \left(y - \frac{1}{2}\right)^2 $$**_
    
    ### Step 4: Clean up the equation
    
    Let's put everything we just did together. Left side: $$ (x + 1)^2 + \left(y - \frac{1}{2}\right)^2 + z^2 $$ _(Since $z^2$ is alone, you can imagine it as $(z - 0)^2$ if that helps visualize it!)_ Right side: Add the numbers up. $1 + \frac{1}{4} = \frac{4}{4} + \frac{1}{4} = \frac{5}{4}$. Our final, beautiful Standard Equation is: $$ (x + 1)^2 + \left(y - \frac{1}{2}\right)^2 + z^2 = \frac{5}{4} $$ ***
    
    ### Step 5: Pull out the Center and Radius
    
    Now we just compare our equation to the blueprint!** The Center $(h, k, l)$: **Look inside the parentheses and flip the signs.
    
    - From $(x + 1)$, we pull out**$-1$**.
    
    - From $(y - \frac{1}{2})$, we pull out
    
    **$\frac{1}{2}$**.
    
    - From $z^2$ (which is $z - 0$), we pull out
    
    **$0$**.** Center = $\left(-1, \frac{1}{2}, 0\right)$ The Radius ($r$): **The number on the right side of the equals sign is the radius _squared_ ($r^2$). $$ r^2 = \frac{5}{4} $$ To find the actual radius $r$, just take the square root of both the top and the bottom: $$ r = \frac{\sqrt{5}}{\sqrt{4}} $$ Since the square root of $4$ is exactly $2$, we get:** Radius = $\frac{\sqrt{5}}{2}$** (2/2)


## Q5 ![[image-19 1.png]]
1. **
    
    ### Step 1: Find the Center (The Midpoint Formula)
    
    To find the middle of a line in 3D space, you just take the "average" of the $x$'s, the average of the $y$'s, and the average of the $z$'s. Here is the formula: $$ \text{Center} = \left( \frac{x_1 + x_2}{2}, \frac{y_1 + y_2}{2}, \frac{z_1 + z_2}{2} \right) $$ Let's plug in our two points, $(-5, 2, 9)$ and $(3, 6, 1)$:
    
    **The $x$-middle: **$\frac{-5 + 3}{2} = \frac{-2}{2} = \mathbf{-1}$**The $y$-middle: **$\frac{2 + 6}{2} = \frac{8}{2} = \mathbf{4}$**The $z$-middle: **$\frac{9 + 1}{2} = \frac{10}{2} = \mathbf{5}$** Our Center $(h, k, l)$ is exactly $(-1, 4, 5)$. *****
    
    ### Step 2: Find the Radius (The Distance Formula)
    
    Now we know the center is at $(-1, 4, 5)$. The radius is the distance from this center to the outside edge of the sphere. We can pick _either_ of the two original endpoints to represent the outside edge. Let's use $(3, 6, 1)$ because dealing with positive numbers is usually easier! (1/2)
    
2. To find the distance between the center $(-1, 4, 5)$ and the edge $(3, 6, 1)$, we use the 3D Distance Formula: $$ r = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (z_2 - z_1)^2} $$ Let's plug our numbers in (remember that subtracting a negative becomes adding a positive!): $$ r = \sqrt{(3 - (-1))^2 + (6 - 4)^2 + (1 - 5)^2} $$ $$ r = \sqrt{(3 + 1)^2 + (2)^2 + (-4)^2} $$ $$ r = \sqrt{(4)^2 + (2)^2 + (-4)^2} $$ Now square those numbers: $$ r = \sqrt{16 + 4 + 16} $$ $$ r = \sqrt{36} $$ **Our Radius ($r$) is exactly $6$.** ***
    
    ### Step 3: Put it into the Blueprint Equation
    
    We have our two ingredients:
    
    - Center: $(-1, 4, 5)$
    - Radius: $6$ (which means $r^2 = 36$)
    
    Let's drop them into our standard form blueprint: $$ (x - h)^2 + (y - k)^2 + (z - l)^2 = r^2 $$ $$ (x - (-1))^2 + (y - 4)^2 + (z - 5)^2 = 6^2 $$ Clean up that double negative on the $x$, and you have your final answer: $$ \mathbf{(x + 1)^2 + (y - 4)^2 + (z - 5)^2 = 36} $$ (2/2)


## Q6 ![[image-20.png]]
1. ### Step 1: Ignore 3D for a second (What happens in 2D?)
    
    If you were in a standard high school algebra class (2D space, just $x$ and $y$), you might recognize the equation: $$ x^2 + y^2 = 1 $$ That is the equation of a **circle** with a radius of $1$, sitting right at the center of the graph. It's just the outer ring, like a hula-hoop.
    
    ### Step 2: What does the inequality ($\le$) do?
    
    The problem doesn't have an equals sign; it has a $\le$ (less than or equal to). This means we don't just want the points exactly at a distance of $1$. We want the ring _and everything smaller than it_. So, $x^2 + y^2 \le 1$ in 2D is a **solid disk** (like a pancake or a coin) with a radius of 1.
    
    ### Step 3: The Calc 3 "Missing Variable" Rule (Moving to $\mathbb{R}^3$)
    
    The problem states we are in $\mathbb{R}^3$, which means we live in a 3D world with an $x$, $y$, and $z$ axis. But look closely at your inequality: **$x^2 + y^2 \le 1$**. **Notice how the letter $z$ is completely missing?** Here is the golden rule for 3D graphs: **If a variable is missing from the equation, it means that variable is completely unrestricted. It can be absolutely anything.**
    
    - At $z = 0$ (the floor), you have a solid disk of radius 1.
    - At $z = 5$ (5 feet in the air), you have that exact same solid disk.
    - At $z = -100$ (underground), you have that exact same solid disk.
    
    Because $z$ can be any number from negative infinity to positive infinity, you take that 2D flat disk and stretch it infinitely up and down along the z-axis.
    
    ### The Final Answer
    
    When you stack an infinite number of solid disks on top of each other, you get a cylinder. The region represented is a **solid, infinite cylinder** with a radius of 1, centered directly on the z-axis. (1/2)
    
1. _(Note: It is important to include the word "solid" in your answer because of the $\le$ sign! If it was just an equals sign, it would be an empty pipe/tube instead of a solid pillar)._ (2/2)


## Q8 ![[image-21.png]]
### Part a) The Component Form of $\mathbf{u}$ and $\mathbf{v}$

**The Concept:** A "point" is just a location on a map (like a city). A "vector" is the actual journey between two points (like driving from one city to another). It tells you exactly how many steps to take in the $x, y,$ and $z$ directions to get from your starting line to your finish line. "Component form" is just writing down those steps inside angled brackets, like this: $\langle x, y, z \rangle$. **The Golden Rule for Vectors:** To find the journey between two points, you always do: **Destination minus Start**. ---
### Finding Vector $\mathbf{u}$ (which is $\vec{PQ}$)

The arrow on top of $\vec{PQ}$ tells you the direction. You start at point $P$ and drive to point $Q$.

- **Start ($P$):** $(2, -1, 3)$
- **Destination ($Q$):** $(0, 5, 1)$

Let's do "Destination minus Start" for each coordinate:

- $x$ steps: $0 - 2 = \mathbf{-2}$
- $y$ steps: $5 - (-1) = 5 + 1 = \mathbf{6}$
- $z$ steps: $1 - 3 = \mathbf{-2}$

**Vector $\mathbf{u} = \langle -2, 6, -2 \rangle$** _(This literally means: to get from P to Q, walk backwards 2 steps on the x-axis, forward 6 steps on the y-axis, and down 2 steps on the z-axis)._ ---

### Finding Vector $\mathbf{v}$ (which is $\vec{PR}$)

Now we start at $P$ and drive to $R$.

- **Start ($P$):** $(2, -1, 3)$
- **Destination ($R$):** $(5, 5, 0)$

Let's do "Destination minus Start" again:

- $x$ steps: $5 - 2 = \mathbf{3}$
- $y$ steps: $5 - (-1) = 5 + 1 = \mathbf{6}$
- $z$ steps: $0 - 3 = \mathbf{-3}$

**Vector $\mathbf{v} = \langle 3, 6, -3 \rangle$**

 ### Part b) The Magnitude of $\mathbf{v}$
    
**The Concept:** We know that vector $\mathbf{v}$ is the journey from point $P$ to point $R$, and in part (a) we found it was $\mathbf{v} = \langle 3, 6, -3 \rangle$. "Magnitude" is just a fancy math word for **Length** or **Distance**. It asks: _If I walked 3 steps forward, 6 steps right, and 3 steps down, how far away am I in a straight line from where I started?_ To find the magnitude (written as $\mathbf{v}$), we just use the 3D Pythagorean Theorem: $$ \mathbf{v} = \sqrt{x^2 + y^2 + z^2} $$ **The Math:** Let's plug in our numbers for $\mathbf{v}$: $$ \mathbf{v} = \sqrt{(3)^2 + (6)^2 + (-3)^2} $$ $$ \mathbf{v} = \sqrt{9 + 36 + 9} $$ $$ \mathbf{v} = \sqrt{54} $$ To make your professor happy, we should probably simplify that square root. We know that $54$ is $9 \times 6$, and the square root of $9$ is $3$: $$ \mathbf{v} = \sqrt{9 \cdot 6} = \mathbf{3\sqrt{6}} $$ _(So the exact length of the line from P to R is $3\sqrt{6}$!)_ ***
    
### Part c) The Dot Product ($\mathbf{u} \cdot \mathbf{v}$)
    
 **The Concept: **There are two ways to "multiply" vectors in Calc 3: The** Dot Product **and the** Cross Product**. The Dot Product is the easy one. You multiply the $x$'s together, the $y$'s together, and the $z$'s together, and then you just** add those three numbers up**. _Important note: The answer to a dot product is always just a normal, single number (a scalar), NOT a vector!_** The Math:** From part (a), we have: $\mathbf{u} = \langle -2, 6, -2 \rangle$ $\mathbf{v} = \langle 3, 6, -3 \rangle$ Let's do the Dot Product ($\mathbf{u} \cdot \mathbf{v}$):

1. Multiply the $x$'s: $(-2) \times (3) = -6$
2. Multiply the $y$'s: $(6) \times (6) = 36$
3. Multiply the $z$'s: $(-2) \times (-3) = 6$

Now, add them all together: $$ -6 + 36 + 6 = \mathbf{36} $$ (1/2)
4. **The dot product $\mathbf{u} \cdot \mathbf{v}$ is exactly $36$.**

### Part d) The Cross Product ($\mathbf{u} \times \mathbf{v}$)

**The Concept:** Unlike the dot product (which just gave us a single number), the Cross Product gives us a **brand new vector**. This new vector has a very special superpower: **It is perfectly perpendicular (at a 90-degree angle) to BOTH of your original vectors.** (This will be the secret key to solving Part E). **The Math (The Matrix Method):** To find $\mathbf{u} \times \mathbf{v}$, we set up a 3x3 matrix.
    
- **Row 1** is always the letters $\mathbf{i}$, $\mathbf{j}$, and $\mathbf{k}$ (which represent the $x, y,$ and $z$ slots).
    - **Row 2** is your first vector ($\mathbf{u}$): $-2, 6, -2$
    - **Row 3** is your second vector ($\mathbf{v}$): $3, 6, -3$
    
    Here is what the matrix looks like: $$ \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \ -2 & 6 & -2 \ 3 & 6 & -3 \end{vmatrix} $$ To solve this, we use the "cover-up" method. We will find our new $\mathbf{i}$ (the x-slot), our new $\mathbf{j}$ (the y-slot), and our new $\mathbf{k}$ (the z-slot) one at a time. **Important Rule:** The middle term (the $\mathbf{j}$ term) is **always subtracted**. The pattern is always **positive, negative, positive**.**
    
    1. Find the $\mathbf{i}$ term (x-slot):
    
    **Cover up the $\mathbf{i}$ column with your finger. Look at the 4 numbers left: $\begin{vmatrix} 6 & -2 \ 6 & -3 \end{vmatrix}$ Cross-multiply them: (Top-Left $\times$ Bottom-Right) MINUS (Top-Right $\times$ Bottom-Left). $[(6) \times (-3)] - [(-2) \times (6)]$ $[-18] - [-12] = -18 + 12 = \mathbf{-6}$ So our first part is **$-6\mathbf{i}$**.**
    
    2. Find the $\mathbf{j}$ term (y-slot):
    
    **Cover up the $\mathbf{j}$ column. Look at the 4 numbers left: $\begin{vmatrix} -2 & -2 \ 3 & -3 \end{vmatrix}$ Cross-multiply them: $[(-2) \times (-3)] - [(-2) \times (3)]$ $[6] - [-6] = 6 + 6 = 12$ (1/2)
    
3. **BUT REMEMBER THE RULE:** The $\mathbf{j}$ term is always negative! We flip the sign. So our middle part is **$-12\mathbf{j}$**.**
    
    3. Find the $\mathbf{k}$ term (z-slot):
    
    **Cover up the $\mathbf{k}$ column. Look at the 4 numbers left: $\begin{vmatrix} -2 & 6 \ 3 & 6 \end{vmatrix}$ Cross-multiply them: $[(-2) \times (6)] - [(6) \times (3)]$ $[-12] - [18] = \mathbf{-30}$ So our last part is **$-30\mathbf{k}$**. **The Final Answer:** Put the three pieces together: $-6\mathbf{i} - 12\mathbf{j} - 30\mathbf{k}$ Or, written in the component brackets we used earlier: **$\mathbf{u} \times \mathbf{v} = \langle -6, -12, -30 \rangle$**

### Part e) Find the equation of the plane containing $P$, $Q$, and $R$.
    
**The Concept:** A "plane" is just a flat surface (like a piece of paper) floating in 3D space. To build the equation of a plane, you need exactly **two ingredients**:
    
   1. **A Point:** Any point that lives on the plane.
    1. **A Normal Vector ($\mathbf{n}$):** A vector that points straight out of the plane perfectly perpendicular (90 degrees) to the surface.
    
  **Ingredient 1: The Point** We need a point on the plane. The problem says the plane contains $P$, $Q$, and $R$. That means we can pick _any_ of those three points to use! Let's pick point $P$ because it was the first one listed: **$(2, -1, 3)$**. 
  **Ingredient 2: The Normal Vector ($\mathbf{n}$)** We need a vector that is perfectly perpendicular to the surface of the plane. Wait a minute... the surface of the plane is built entirely by the vectors $\mathbf{u}$ and $\mathbf{v}$ (because they connect $P, Q,$ and $R$). And in Part D, we said the superpower of the **Cross Product ($\mathbf{u} \times \mathbf{v}$)** is that it gives us a new vector that is perfectly perpendicular to both $\mathbf{u}$ and $\mathbf{v}$! That means **our cross product IS our Normal Vector!** **$\mathbf{n} = \langle -6, -12, -30 \rangle$** _(Note: We could divide all these numbers by -6 to get a simpler vector $\langle 1, 2, 5 \rangle$, and it would still point in the same direction, but let's stick to the raw numbers we found so we don't accidentally make a mistake)._ **Building the Equation:** The "blueprint" equation for a plane looks like this: $$ a(x - x_0) + b(y - y_0) + c(z - z_0) = 0 $$
    
- $a, b, c$ come from our normal vector $\mathbf{n} = \langle -6, -12, -30 \rangle$.
- $x_0, y_0, z_0$ come from our point $P = (2, -1, 3)$.
    
    Let's plug the numbers in: $$ -6(x - 2) - 12(y - (-1)) - 30(z - 3) = 0 $$ Clean up the double negative: (1/2)
    
2. **$-6(x - 2) - 12(y + 1) - 30(z - 3) = 0$** _(That is a perfectly valid final answer. Some professors might want you to distribute and simplify it like this: $-6x + 12 - 12y - 12 - 30z + 90 = 0 \implies -6x - 12y - 30z = -90$, but the first way is safer unless asked otherwise).__**
    
    ### Part f) Find a set of parametric equations for the line through $P$ and $Q$.
    
    **The Concept:** Just like a plane needed a point and a_perpendicular* vector, a line needs two ingredients:
    
    1. **A Point:** Any point on the line.
    2. **A Direction Vector:** A vector that points perfectly parallel to the line (showing you which way to drive).
    
    **Ingredient 1: The Point** The line goes through $P$ and $Q$. Let's just pick $P$ again: **$(2, -1, 3)$**. **Ingredient 2: The Direction Vector** We need a vector that shows the direction from $P$ to $Q$. Well, look at Part A! We literally already built that. Vector $\mathbf{u}$ ($\vec{PQ}$) is the exact journey from $P$ to $Q$. **Direction Vector = $\mathbf{u} = \langle -2, 6, -2 \rangle$** **Building the Parametric Equations:** A "parametric equation" just means we write a separate formula for $x$, $y$, and $z$, based on time ($t$). The blueprint is: $$ x(t) = \text{Point}_x + (\text{Direction}_x)t $$ $$ y(t) = \text{Point}_y + (\text{Direction}_y)t $$ $$ z(t) = \text{Point}_z + (\text{Direction}_z)t $$ Let's plug in our Point $(2, -1, 3)$ and our Direction Vector $\langle -2, 6, -2 \rangle$: $$ \mathbf{x = 2 - 2t} $$ $$ \mathbf{y = -1 + 6t} $$ $$ \mathbf{z = 3 - 2t} $$ *****

## Q9 ![[image-22.png]]
1. This is a classic Calc 3 problem! The great news is that you actually **already know how to do all the math for this**. It uses the exact same tools we used in the last problem: the Dot Product and the Magnitude. To find the angle ($\theta$) between any two vectors, we use the **Master Angle Formula**: $$ \cos(\theta) = \frac{\text{Dot Product}}{\text{Magnitude of 1st} \times \text{Magnitude of 2nd}} $$ Let's tackle **Part a)** first, because something really special happens here! ***
    
    ### Part a) The Angle between $\mathbf{v}$ and $\mathbf{w}$
    
    $\mathbf{v} = \langle 4, -1, 5 \rangle$ $\mathbf{w} = \langle 3, 2, -2 \rangle$ According to our formula, the very first thing we need to do is find the Dot Product ($\mathbf{v} \cdot \mathbf{w}$). Let's multiply the $x$'s, $y$'s, and $z$'s and add them up:
    
    - $x$'s: $(4) \times (3) = 12$
    - $y$'s: $(-1) \times (2) = -2$
    - $z$'s: $(5) \times (-2) = -10$
    
    Now add them up: $12 - 2 - 10 = \mathbf{0}$** STOP RIGHT THERE! **You just hit the jackpot. In Calc 3, if the dot product of two vectors is exactly $0$, it means the top of our fraction is $0$. And if the top of the fraction is $0$, the whole thing is $0$. ($\cos(\theta) = 0$). When $\cos(\theta) = 0$, the angle $\theta$ is exactly** $90^\circ$ (or $\frac{\pi}{2}$ radians)**. You don't even have to calculate the magnitudes! Whenever a dot product is 0, the vectors are perfectly perpendicular (the fancy math word for this is** "orthogonal"**).** Answer for a): $\theta = 90^\circ$ or $\frac{\pi}{2}$ *****
    
    ### Part b) The Angle between $\mathbf{a}$ and $\mathbf{b}$
    
    Before we do the math, we have to translate the problem. The problem writes the vectors using $\mathbf{i}$, $\mathbf{j}$, and $\mathbf{k}$. This is just a disguise! $\mathbf{i}$ is the x-slot, $\mathbf{j}$ is the y-slot, and $\mathbf{k}$ is the z-slot. Let's put them back into the normal brackets: (1/2)
    
2. - $\mathbf{b} = 2\mathbf{i} - 2\mathbf{j} + \mathbf{k} \implies \mathbf{b} = \langle 2, -2, 1 \rangle$
    - $\mathbf{a} = \mathbf{i} - 3\mathbf{k}$. _(Wait, where is the $\mathbf{j}$? If a letter is missing, it means it's zero!)_ $\implies \mathbf{a} = \langle 1, 0, -3 \rangle$
    
    Now let's use our Master Formula! **Step 1: The Dot Product ($\mathbf{a} \cdot \mathbf{b}$)**
    
    - $x$'s: $(1) \times (2) = 2$
    - $y$'s: $(0) \times (-2) = 0$
    - $z$'s: $(-3) \times (1) = -3$
    - Total: $2 + 0 - 3 = \mathbf{-1}$ _(Since it's not 0, we have to keep going!)_
    
    **Step 2: Magnitude of $\mathbf{a}$** $$ \mathbf{a} = \sqrt{(1)^2 + (0)^2 + (-3)^2} $$ $$ \mathbf{a} = \sqrt{1 + 0 + 9} = \mathbf{\sqrt{10}} $$ **Step 3: Magnitude of $\mathbf{b}$** $$ \mathbf{b} = \sqrt{(2)^2 + (-2)^2 + (1)^2} $$ $$ \mathbf{b} = \sqrt{4 + 4 + 1} = \sqrt{9} = \mathbf{3} $$ **Step 4: Plug it all into the Master Formula** $$ \cos(\theta) = \frac{\text{Dot Product}}{\mathbf{a} \times \mathbf{b}} $$ $$ \cos(\theta) = \frac{-1}{3\sqrt{10}} $$ To get $\theta$ all by itself, we just use the inverse cosine ($\cos^{-1}$ or $\arccos$) on our calculator: $$ \theta = \cos^{-1}\left( \frac{-1}{3\sqrt{10}} \right) $$ If you punch that into a calculator (make sure you know if your professor wants the answer in Degrees or Radians!):
    
    - **In Degrees:** $\approx \mathbf{96.06^\circ}$
    - **In Radians:** $\approx \mathbf{1.677}$
    
    And that's it! Just remember the golden rule: **Dot product of 0 means 90 degrees.** That will save you so much time on exams! (2/2)

## 10 ![[image-23.png]]
1. Let's knock out **Part a** and **Part b** first. Here are the vectors the problem gives us: $\mathbf{u} = \langle 3, -2, 1 \rangle$ $\mathbf{v} = \langle 2, -4, -3 \rangle$ $\mathbf{w} = \langle -1, 2, 2 \rangle$_**### Part a) Find $|\mathbf{u}|$ (The Magnitude of $\mathbf{u}$)
    
    You've done this before! The straight bars $|\mathbf{u}|$ (or $\mathbf{u}$) just mean** magnitude **or length. We just use the 3D Pythagorean Theorem: $$ |\mathbf{u}| = \sqrt{x^2 + y^2 + z^2} $$ Let's plug in the numbers for $\mathbf{u}$: $$ |\mathbf{u}| = \sqrt{(3)^2 + (-2)^2 + (1)^2} $$ $$ |\mathbf{u}| = \sqrt{9 + 4 + 1} $$** $|\mathbf{u}| = \sqrt{14}$ **That's it! Part a is done.**_
    
    ### Part b) Find the angle between $\mathbf{u}$ and $\mathbf{v}$
    
    We use our Master Angle Formula from the previous problem: $$ \cos(\theta) = \frac{\text{Dot Product of u and v}}{\text{Magnitude of u} \times \text{Magnitude of v}} $$ **Step 1: The Dot Product ($\mathbf{u} \cdot \mathbf{v}$)** Multiply the $x$'s, $y$'s, and $z$'s of $\mathbf{u}$ and $\mathbf{v}$, then add them up:
    
    - $x$'s: $(3) \times (2) = 6$
    - $y$'s: $(-2) \times (-4) = 8$
    - $z$'s: $(1) \times (-3) = -3$
    - Total: $6 + 8 - 3 = \mathbf{11}$
    
    **Step 2: Magnitude of $\mathbf{u}$** We literally _just_ found this in Part a! How convenient. $$ |\mathbf{u}| = \sqrt{14} $$ **Step 3: Magnitude of $\mathbf{v}$** $$ |\mathbf{v}| = \sqrt{(2)^2 + (-4)^2 + (-3)^2} $$ $$ |\mathbf{v}| = \sqrt{4 + 16 + 9} $$ $$ |\mathbf{v}| = \mathbf{\sqrt{29}} $$ **Step 4: Plug it into the formula** $$ \cos(\theta) = \frac{11}{\sqrt{14} \times \sqrt{29}} $$ You can multiply the bottoms together ($\sqrt{14 \times 29} = \sqrt{406}$): $$ \cos(\theta) = \frac{11}{\sqrt{406}} $$ (1/2)
    
2. To get the actual angle $\theta$, use the inverse cosine on your calculator: $$ \theta = \cos^{-1}\left( \frac{11}{\sqrt{406}} \right) $$
    
    - **In Degrees:** $\approx \mathbf{56.9^\circ}$
    - **In Radians:** $\approx \mathbf{0.99 \text{ rad}}$

### Part c) Show that $\mathbf{u} \cdot \mathbf{u} = |\mathbf{u}|^2$

**The Concept:** When a math problem says "Show that...", it means they are giving you a fact that is always true, and they want you to prove it works using the specific numbers they gave you. We need to calculate the left side ($\mathbf{u} \cdot \mathbf{u}$), calculate the right side ($|\mathbf{u}|^2$), and show that they equal the exact same number. **Left Side: $\mathbf{u} \cdot \mathbf{u}$ (Dotting a vector with itself)** Remember, $\mathbf{u} = \langle 3, -2, 1 \rangle$. Let's dot it with another copy of itself!

- Multiply the $x$'s: $(3) \times (3) = 9$
- Multiply the $y$'s: $(-2) \times (-2) = 4$
- Multiply the $z$'s: $(1) \times (1) = 1$
- Add them up: $9 + 4 + 1 = \mathbf{14}$

**Right Side: $|\mathbf{u}|^2$ (Squaring the magnitude)** Hey, look at Part a again! We already found the magnitude of $\mathbf{u}$. We know $|\mathbf{u}| = \sqrt{14}$. Now, what happens if we square a square root? They cancel each other out! $$ |\mathbf{u}|^2 = (\sqrt{14})^2 = \mathbf{14} $$ **The Conclusion:** Since the Left Side $= 14$ and the Right Side $= 14$, we have successfully "shown" that the rule is true! **(Just write out the steps above on your paper, and you get full credit for this part).**
1. ### Part d) Determine a unit vector perpendicular to the plane containing $\mathbf{v}$ and $\mathbf{w}$.
    
    Let's break this sentence down into two steps:
    
    1. **"perpendicular to $\mathbf{v}$ and $\mathbf{w}$"**: We know exactly how to do this! The Cross Product ($\mathbf{v} \times \mathbf{w}$) gives us a vector that is perfectly perpendicular to both.
    2. **"unit vector"**: A unit vector is simply a vector that has a length (magnitude) of exactly $1$. Once we find our cross product vector, we will shrink it down so its length is $1$.
    
    ---
    
    ### Step 1: The Cross Product ($\mathbf{v} \times \mathbf{w}$)
    
    $\mathbf{v} = \langle 2, -4, -3 \rangle$ $\mathbf{w} = \langle -1, 2, 2 \rangle$ Set up the 3x3 matrix: $$ \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \ 2 & -4 & -3 \ -1 & 2 & 2 \end{vmatrix} $$**
    
    1. The $\mathbf{i}$ term (x-slot):
    
    **Cover the $\mathbf{i}$ column. $[(-4) \times (2)] - [(-3) \times (2)]$ $[-8] - [-6] = -8 + 6 = \mathbf{-2}$ Our $\mathbf{i}$ term is **$-2\mathbf{i}$**.**
    
    2. The $\mathbf{j}$ term (y-slot):
    
    **Cover the $\mathbf{j}$ column. $[(2) \times (2)] - [(-3) \times (-1)]$ $[4] - [3] = 1$ _Remember the rule: Always flip the sign of the $\mathbf{j}$ term!_ Our $\mathbf{j}$ term is **$-1\mathbf{j}$**.**
    
    3. The $\mathbf{k}$ term (z-slot):
    
    **Cover the $\mathbf{k}$ column. $[(2) \times (2)] - [(-4) \times (-1)]$ $[4] - [4] = \mathbf{0}$ Our $\mathbf{k}$ term is **$0\mathbf{k}$**. **Our Perpendicular Vector is:** $\langle -2, -1, 0 \rangle$ ---
    
    ### Step 2: Make it a "Unit Vector"
    
    Right now, our vector $\langle -2, -1, 0 \rangle$ points in the exact right direction, but its length is probably not 1. **The Golden Rule for Unit Vectors:** To shrink any vector down to a length of 1, just divide the vector by its own magnitude. **Let's find its magnitude:** $$ \text{Magnitude} = \sqrt{(-2)^2 + (-1)^2 + (0)^2} $$ $$ \text{Magnitude} = \sqrt{4 + 1 + 0} = \mathbf{\sqrt{5}} $$ (1/2)
    
1. **Now, divide the vector by $\sqrt{5}$:** You literally just divide every single number inside the brackets by $\sqrt{5}$. **Final Answer:** $$ \mathbf{\left\langle \frac{-2}{\sqrt{5}}, \frac{-1}{\sqrt{5}}, 0 \right\rangle} $$

## Q11 ![[image-24.png]]
Let's label the three points: $A = (3, 4, -1)$ $B = (-1, 6, 9)$ $C = (5, 3, -6)$ To prove that three points are collinear (lie on the same line) using vectors, we need to create two vectors using these points (for example, $\vec{AB}$ and $\vec{AC}$) and check if they are parallel. Two vectors are parallel if one is a scalar multiple of the other ($\vec{AB} = c\vec{AC}$).

### Step 1: Find vector $\vec{AB}$

Subtract the coordinates of point $A$ from point $B$: $$ \vec{AB} = \langle -1 - 3,; 6 - 4,; 9 - (-1) \rangle $$ $$ \vec{AB} = \langle -4,; 2,; 10 \rangle $$

### Step 2: Find vector $\vec{AC}$

Subtract the coordinates of point $A$ from point $C$: $$ \vec{AC} = \langle 5 - 3,; 3 - 4,; -6 - (-1) \rangle $$ $$ \vec{AC} = \langle 2,; -1,; -5 \rangle $$

### Step 3: Check for Collinearity

Now we check if $\vec{AB}$ is a scalar multiple of $\vec{AC}$. We set up the equation: $$ \vec{AB} = c\vec{AC} $$ $$ \langle -4, 2, 10 \rangle = c \langle 2, -1, -5 \rangle $$ Let's check the scalar $c$ for each component (x, y, and z):

- **x-component:** $-4 = c(2) \implies c = -2$
- **y-component:** $2 = c(-1) \implies c = -2$
- **z-component:** $10 = c(-5) \implies c = -2$

### Conclusion

Since the scalar multiple $c = -2$ is perfectly consistent for all three components, the two vectors are parallel ($\vec{AB} = -2\vec{AC}$). Because $\vec{AB}$ and $\vec{AC}$ are parallel and share the common starting point $A$, they must lie on the exact same line.


## Q12
![[image-25.png]]
For three vectors to be coplanar (meaning they all lie in the exact same 3D plane), their **scalar triple product** must equal zero. The scalar triple product is defined as $\mathbf{a} \cdot (\mathbf{b} \times \mathbf{c}) = 0$. Geometrically, this calculates the volume of the parallelepiped formed by the three vectors; if the volume is 0, they are completely flat and thus coplanar. Given the vectors: $\mathbf{a} = \langle 2, -3, z \rangle$ $\mathbf{b} = \langle 1, 0, 1 \rangle$ $\mathbf{c} = \langle 0, -1, 1 \rangle$

### Step 1: Find the cross product $\mathbf{b} \times \mathbf{c}$

Let's calculate the cross product of $\mathbf{b}$ and $\mathbf{c}$ using the determinant method: $$ \mathbf{b} \times \mathbf{c} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \ 1 & 0 & 1 \ 0 & -1 & 1 \end{vmatrix} $$ Expanding this determinant:

- **i-component:** $(0)(1) - (1)(-1) = 0 - (-1) = 1$
- **j-component:** $- [(1)(1) - (1)(0)] = - [1 - 0] = -1$
- **k-component:** $(1)(-1) - (0)(0) = -1 - 0 = -1$

So, the cross product is: $$ \mathbf{b} \times \mathbf{c} = \langle 1, -1, -1 \rangle $$

### Step 2: Set the dot product equal to zero

Now we take the dot product of vector $\mathbf{a}$ and the result we just found, and set it to $0$: $$ \mathbf{a} \cdot (\mathbf{b} \times \mathbf{c}) = 0 $$ $$ \langle 2, -3, z \rangle \cdot \langle 1, -1, -1 \rangle = 0 $$

### Step 3: Solve for $z$

Multiply the corresponding components and add them together: $$ (2)(1) + (-3)(-1) + (z)(-1) = 0 $$ $$ 2 + 3 - z = 0 $$ $$ 5 - z = 0 $$ $$ z = 5 $$

### Conclusion

For the vectors $\mathbf{a}$, $\mathbf{b}$, and $\mathbf{c}$ to be coplanar, the value of $z$ must be **$5$**.


## Q13 ![[image-26.png]]
Here is the step-by-step solution for problem 13. We are given:

- Magnitude of $\mathbf{a}$: $|\mathbf{a}| = 3$
- Magnitude of $\mathbf{b}$: $|\mathbf{b}| = 7$
- Dot product: $\mathbf{a} \cdot \mathbf{b} = 0$

We need to compute the magnitude of the cross product, $|\mathbf{a} \times \mathbf{b}|$.

### Step 1: Use the dot product to find the angle

The geometric formula for the dot product is: $$ \mathbf{a} \cdot \mathbf{b} = |\mathbf{a}| |\mathbf{b}| \cos(\theta) $$ where $\theta$ is the angle between the two vectors. Substitute the known values into the equation: $$ 0 = (3)(7) \cos(\theta) $$ $$ 0 = 21 \cos(\theta) $$ $$ \cos(\theta) = 0 $$ Since $\cos(\theta) = 0$, the angle $\theta$ between the vectors must be $90^\circ$ (or $\frac{\pi}{2}$ radians). This tells us that the vectors $\mathbf{a}$ and $\mathbf{b}$ are **orthogonal (perpendicular)**.

### Step 2: Apply the cross product magnitude formula

The geometric formula for the magnitude of the cross product is: $$ |\mathbf{a} \times \mathbf{b}| = |\mathbf{a}| |\mathbf{b}| \sin(\theta) $$

### Step 3: Calculate the final value

Since we now know that $\theta = 90^\circ$, we can evaluate $\sin(90^\circ) = 1$. Substitute everything into the magnitude formula: $$ |\mathbf{a} \times \mathbf{b}| = (3)(7)\sin(90^\circ) $$ $$ |\mathbf{a} \times \mathbf{b}| = (21)(1) $$ $$ |\mathbf{a} \times \mathbf{b}| = 21 $$

### Conclusion

The magnitude of the cross product is **$21$**.


## Q14 ![[image-27.png]]
### Part a): Find $\mathbf{u}$ if it is perpendicular to $x - 3y + 4z = 0$ and $|\mathbf{u}| = 3$
    
**Step 1: Find the normal vector of the plane** The coefficients of $x$, $y$, and $z$ in the general equation of a plane ($ax + by + cz = d$) give us a vector that is perfectly perpendicular (normal) to the entire plane. From the plane $1x - 3y + 4z = 0$, our normal vector is: $$ \mathbf{n} = \langle 1, -3, 4 \rangle $$ Any vector perpendicular to the plane must be parallel to $\mathbf{n}$. So, $\mathbf{u}$ must be a scaled version of $\mathbf{n}$. **Step 2: Find the magnitude of $\mathbf{n}$** To force the vector to have exactly a length of 3, we first shrink it down to a "unit vector" (length 1), and then multiply it by 3. $$ |\mathbf{n}| = \sqrt{(1)^2 + (-3)^2 + (4)^2} = \sqrt{1 + 9 + 16} = \sqrt{26} $$ **Step 3: Create the unit vector and scale to 3** The unit vector is $\frac{\mathbf{n}}{|\mathbf{n}|} = \frac{1}{\sqrt{26}} \langle 1, -3, 4 \rangle$. Now multiply by the desired magnitude of 3: $$ \mathbf{u} = 3 \left( \frac{1}{\sqrt{26}} \langle 1, -3, 4 \rangle \right) = \left\langle \frac{3}{\sqrt{26}}, \frac{-9}{\sqrt{26}}, \frac{12}{\sqrt{26}} \right\rangle $$ _Note: Because a line perpendicular to a plane can point "up" or "down", there are technically two correct vectors. You can put a $\pm$ in front to represent both: $\mathbf{u} = \pm \left\langle \frac{3}{\sqrt{26}}, \frac{-9}{\sqrt{26}}, \frac{12}{\sqrt{26}} \right\rangle$_ ***
    
### Part b): Find $\mathbf{u}$ if it is a unit vector perpendicular to both given lines
    
   **Step 1: Extract the direction vectors of the lines** Parametric equations for a line are written as $x = x_0 + at$, $y = y_0 + bt$, $z = z_0 + ct$, where the coefficients of the parameter ($t$ or $s$) give the direction vector $\langle a, b, c \rangle$.
  - Line 1 (t): The direction vector is $\mathbf{v}_1 = \langle -1, 2, 5 \rangle$ (1/2)
    
2. - Line 2 (s): The direction vector is $\mathbf{v}_2 = \langle 7, 1, 2 \rangle$
    
    **Step 2: Find a vector perpendicular to both (Cross Product)** To find a single vector that is perpendicular to two different vectors, we take their cross product. $$ \mathbf{v}_1 \times \mathbf{v}_2 = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \ -1 & 2 & 5 \ 7 & 1 & 2 \end{vmatrix} $$
    
    - **i-component:** $(2)(2) - (5)(1) = 4 - 5 = -1$
    - **j-component:** $-[(-1)(2) - (5)(7)] = -[-2 - 35] = -[-37] = 37$
    - **k-component:** $(-1)(1) - (2)(7) = -1 - 14 = -15$
    
    Let's call this new perpendicular vector $\mathbf{w} = \langle -1, 37, -15 \rangle$. **Step 3: Normalize to a unit vector** The problem asks for $\mathbf{u}$ to be a _unit vector_. Let's find the magnitude of our new vector $\mathbf{w}$: $$ |\mathbf{w}| = \sqrt{(-1)^2 + (37)^2 + (-15)^2} $$ $$ |\mathbf{w}| = \sqrt{1 + 1369 + 225} = \sqrt{1595} $$ Now, divide the vector by its magnitude to make it a unit vector (length 1): $$ \mathbf{u} = \pm \frac{1}{\sqrt{1595}} \langle -1, 37, -15 \rangle $$ _(Again, the $\pm$ accounts for the fact that the unit vector could point in either of the two directions perpendicular to both lines)._ (2/2)
1. _**
    
    ### Part a: The Logic (Planes)
    
    **The Problem: **Find a vector perpendicular to the plane $x - 3y + 4z = 0$ with a length of 3.** 1. How did I know to pull out the coefficients? **This comes down to how planes are built in 3D math. Think of a flat piece of paper floating in space. How do you describe its exact tilt to a computer? Instead of trying to describe the infinite flat surface itself, mathematicians use a shortcut: they define the plane by the single arrow that points** straight up out of it **at a 90-degree angle. This is called the** Normal Vector**. Because of how the dot product works, the standard equation of_any* plane is written as $Ax + By + Cz = D$, where the numbers $A, B$, and $C$ are literally the $x, y$, and $z$ coordinates of that perpendicular Normal Vector.
    
    - **The Translation:** When the problem says "perpendicular to the plane $1x - 3y + 4z = 0$", my brain immediately translates that to: _"Oh, the plane equation is giving me the perpendicular vector for free. It's just the numbers attached to the letters: $\langle 1, -3, 4 \rangle$."_
    
    **
    
    2. How did I know the steps to resize it?
    
    **We now have a vector pointing in the correct perpendicular direction, but the problem demands it has a length of exactly $3$. Our vector $\langle 1, -3, 4 \rangle$ currently has a random length of $\sqrt{26}$ (about 5.1). You can't just easily guess what to multiply 5.1 by to get exactly 3. So, we use a standard 2-step trick:
    
    - **Step A (Shrink to 1):** Divide the vector by its own length. Anything divided by itself is 1. Now we have a "unit vector" (length 1) pointing in the right direction. (1/2)
    
2. - **Step B (Stretch to 3):** Multiply that unit vector by 3. Because $1 \times 3 = 3$, you now have a vector of exactly length 3.
    
    ***
    
    ### Part b: The Logic (Lines)
    
    **The Problem: **Find a unit vector perpendicular to two different lines given in parametric form.** 1. How did I know to extract the direction vectors? **A parametric equation like $x = 4 - 1t$ tells a story. It means: "Start at the $x$-coordinate $4$, and as time ($t$) ticks forward, move $-1$ units along the $x$-axis every second."
    
    - The isolated numbers ($4, 3, 1$) are just the starting dot. We don't care where the lines _start_, we only care which way they _point_.
    - The numbers attached to $t$ or $s$ are the "steering wheel" (the direction vector). So I immediately extract $\langle -1, 2, 5 \rangle$ and $\langle 7, 1, 2 \rangle$.**2. How did I know to use the Cross Product? **This is the most important reflex to build in Calc 3.
    
    - If a problem asks about an**angle**, you use the** Dot Product**.
    
    - If a problem asks you to find a new vector that is
    
    **perpendicular to TWO other vectors simultaneously**, you use the** Cross Product**. The Cross Product is literally a mathematical machine designed for one specific job: you feed it two vectors, and it spits out a third vector that forms a perfect 90-degree angle with both of the originals.** 3. How did I know the final step? **The problem asked for a** unit vector**. In math, "unit" means 1. The vector that the cross product machine spit out was massive (it had a length of $\sqrt{1595}$). To make it a unit vector, I just had to do the same "shrink to 1" trick from Part A: find its length, and divide the vector by that length. (2/2)

## Q15 ![[image-28.png]]
1. ### Step 1: The Square Root Constraint
    
    You cannot take the square root of a negative number in real-valued calculus. Therefore, whatever is _inside_ the square root (the radicand) must be greater than or equal to zero. $$ x^2 + y^2 - 9 \ge 0 $$ Move the 9 over: $$ x^2 + y^2 \ge 9 $$ **Geometrically:** This is the equation of a circle centered at the origin $(0,0)$ with a radius of $3$. Because it says "greater than or equal to", the allowed area is everything **on the boundary line** and **outside the circle**. The inside of the circle is restricted.
    
    ### Step 2: The Denominator Constraint
    
    You can never divide by zero. Therefore, the entire denominator cannot equal zero. $$ x \neq 0 $$ **Geometrically:** The equation $x = 0$ represents the entire **y-axis**. This means the y-axis is completely forbidden and must be cut out of our allowed region.
    
    ### Step 3: Write the Set Notation
    
    To write this in formal mathematical set notation, we combine the two rules we just found. $$ D = { (x, y) \in \mathbb{R}^2 \mid x^2 + y^2 \ge 9, \ x \neq 0 } $$ _Translation: "The Domain is the set of all 2D coordinate pairs $(x,y)$, such that $x^2 + y^2$ is greater than or equal to 9, AND $x$ does not equal zero."_
    
    ### Step 4: How to Sketch the Domain
    
    To sketch this accurately on a 2D coordinate system, you will draw three specific things:
    
    1. **The Boundary:** Draw a circle centered at $(0,0)$ with a radius of $3$. Use a **solid, dark line** because the boundary itself is included ($\ge$). (1/2)
    
2. 2. **The Shading:** Lightly shade the entire region **outside** of the circle to show where the valid coordinates live. Do _not_ shade the inside.
    3. **The Exclusion (The Trap!):** Draw the y-axis as a **dashed line** to explicitly show it is forbidden territory. Most importantly, right where the y-axis intersects your solid circle boundary at $(0, 3)$ and $(0, -3)$, you must draw **open, empty circles** ($\circ$). This proves to your professor that you know those two exact points on the circle's edge are forbidden because $x$ becomes $0$ there. (2/2)

## Q17 ![[image-29.png]]
to find para equations of tangent line of curve, you need a point P which you can get by pluggiing in t if given t, and then you need a directional vector which can be found by taking derivative of r(t) and then plugging t back in to get the vector V. then use it in the format of x=Px + Vx

## Q18 ![[image-30.png]]


## Q20 ![[image-31.png]]
**The Goal:** We have two 3D surfaces: a paraboloid (a 3D bowl shape) and a plane (a flat sheet). When a flat sheet slices through a bowl, the line where they touch forms a curve floating in space (in this case, a parabola). We need to write a **vector-valued function** $\mathbf{r}(t) = \langle x(t), y(t), z(t) \rangle$ that acts as a GPS coordinate path to trace that exact curve.

### Step 1: Look at the simplest equation (the plane)

The easiest way to combine two equations is to look at the simpler one, solve for one of the variables, and use it as a substitute. The plane equation is: $x + y = 0$ Let's solve for $y$: $$ y = -x $$

### Step 2: Substitute into the 3D bowl (the paraboloid)

Now we take the equation of our bowl: $z = x^2 + y^2$ Because we know that $y$ is exactly the same thing as $-x$ everywhere along our intersection curve, we can swap out the $y$: $$ z = x^2 + (-x)^2 $$ $$ z = x^2 + x^2 $$ $$ z = 2x^2 $$

### Step 3: Introduce the parameter ($t$)

To write a vector-valued function, we need everything to be based on a single "stopwatch" variable, usually $t$ (time). Since we managed to get both $y$ and $z$ written completely in terms of $x$, we can make the simplest possible choice: **Let $x = t$.** Now, just replace every $x$ we found with a $t$:

- $x(t) = t$
- $y(t) = -t$ _(because $y = -x$)_
- $z(t) = 2t^2$ _(because $z = 2x^2$)_

### Step 4: Write the final Vector-Valued Function

Bundle those three equations together into a single vector $\mathbf{r}(t)$: $$ \mathbf{r}(t) = \langle t, -t, 2t^2 \rangle $$ _(Or, in $\mathbf{i, j, k}$ notation: $\mathbf{r}(t) = t\mathbf{i} - t\mathbf{j} + 2t^2\mathbf{k}$)_ This is the exact GPS path that traces the slice where the plane cuts the paraboloid! ***


## Q21![[image-32.png]]


1. ### Let's look at your steps first:
    
    You correctly substituted $z=4$ into the first equation to get: $x^2 + y^2 = 4$. Then, you tried to set $x = t$. If we do that, the equation becomes: $t^2 + y^2 = 4$. If you solve that for $y$, you don't get $\pm 2$. You have to subtract $t^2$ and take the square root, which gives you $y = \pm\sqrt{4 - t^2}$. So your vector would be $\langle t, \pm\sqrt{4 - t^2}, 4 \rangle$. **Why professors hate this answer:** While technically mathematically valid, this is considered a "messy" answer.
    
    1. The $\pm$ means you actually have to write _two_ separate vector functions (one for the top half of the shape, one for the bottom half).
    2. Because of the square root, $t$ is trapped. If $t$ is bigger than 2, you get imaginary numbers.
    
    ### The Correct Way: The Sine and Cosine Trick
    
    Look at the equation you got: $x^2 + y^2 = 4$. Geometrically, this is the equation of a **circle with a radius of 2**. In Calculus 3, whenever the curve you are tracing is a circle (or involves an $x^2 + y^2$ that equals a number), you completely abandon the "$x=t$" trick. Instead, you use trigonometry to trace the circle in one smooth, continuous swoop. Here are the steps you should follow: **Step 1: Identify the radius of your circle** $x^2 + y^2 = 4$ Since the formula for a circle is $x^2 + y^2 = r^2$, our radius is **$r = 2$**. **Step 2: Parameterize $x$ and $y$ using trig** Think back to the unit circle in pre-calc! We can define the $x$ and $y$ coordinates of any circle using its radius and an angle $t$:
    
    - $x(t) = r \cos(t)$
    - $y(t) = r \sin(t)$
    
    Plug in our radius of 2:
    
    - $x(t) = 2 \cos(t)$
    - $y(t) = 2 \sin(t)$(1/2)
    
2. _(If you plug these back into $x^2 + y^2 = 4$, you get $4\cos^2(t) + 4\sin^2(t) = 4(\cos^2(t) + \sin^2(t)) = 4(1) = 4$. It works perfectly!)_ **Step 3: What about z?** The problem explicitly tells us that the plane is $z = 4$. This means $z$ never changes; it is permanently stuck at 4 for the entire curve.
    
    - $z(t) = 4$
    
    **Step 4: Write the final vector function** Put all three pieces together: $$ \mathbf{r}(t) = \langle 2\cos(t), \ 2\sin(t), \ 4 \rangle $$


## Q22 ![[image-33.png]]
1. First, the big secret about Calculus 3: **Vectors look scary, but they are actually just three tiny, normal problems wearing a trenchcoat.** When you are asked to take the limit of a vector, you do not have to do any crazy 3D math. You literally just do three completely separate, basic Calculus 1 limits: one for the $\mathbf{i}$ part, one for the $\mathbf{j}$ part, and one for the $\mathbf{k}$ part. Let's tackle them one by one. Our goal is to see what happens as $t$ becomes exactly $0$.
    
    ### 1
    
    1. The $\mathbf{i}$ component: $\lim_{t \to 0} \frac{\sin(2t)}{t}$
    
    In any limit problem, the very first thing you should always try is just plugging the number in directly. Let's plug $t = 0$ in: $$ \frac{\sin(2(0))}{0} = \frac{\sin(0)}{0} = \frac{0}{0} $$ In calculus, getting $\frac{0}{0}$ does **not** mean the answer is zero. It's an error code that means "the answer exists, but you have to do a little more work to uncover it." To fix this, we use a famous trick called **L'Hôpital's Rule**. L'Hôpital's Rule says: _If you get 0/0, take the derivative of the top, take the derivative of the bottom, and then try plugging the number in again._
    
    - **Derivative of the top:** The derivative of $\sin(2t)$ requires the Chain Rule. The outside turns to $\cos(2t)$, and we multiply by the derivative of the inside (which is 2). So the top becomes $2\cos(2t)$.
    - **Derivative of the bottom:** The derivative of $t$ is simply $1$.
    
    Now, let's look at our shiny new fraction and try plugging in $t = 0$ again: $$ \frac{2\cos(2(0))}{1} = 2\cos(0) $$ Since $\cos(0) = 1$, we get: $$ 2(1) = 2 $$ **The $\mathbf{i}$ component is $2$.** _(Note: In Calc 1, you might have memorized a shortcut rule that $\lim_{x \to 0} \frac{\sin(ax)}{x} = a$. If you remember that rule, you can skip L'Hôpital entirely and just say the answer is 2!)_ ***
    
    ### 
    
    2. The $\mathbf{j}$ component: $\lim_{t \to 0} e^{-t}$
    
    (1/2)
    
2. Let's do our first step again: try just plugging the number in directly. $$ e^{-0} $$ Negative zero is just zero, so this is $e^0$. A core rule of algebra is that **any number in the universe raised to the power of 0 is exactly 1**. So, $e^0 = 1$. Since we got a real number and not an error like 0/0, we are completely done. **The $\mathbf{j}$ component is $1$.**_**### 
    
    3. The $\mathbf{k}$ component: $\lim_{t \to 0} e^t$
    
    Same exact process. Plug in $t = 0$ directly. $$ e^0 $$ Again, anything to the power of zero is 1.** The $\mathbf{k}$ component is $1$._
    
    ### Putting it all together
    
    Now that we have solved the three separate mini-problems, we just zip up the trenchcoat and put the $\mathbf{i}$, $\mathbf{j}$, and $\mathbf{k}$ labels back on them. The final answer is: **$2\mathbf{i} + 1\mathbf{j} + 1\mathbf{k}$** _(or just $2\mathbf{i} + \mathbf{j} + \mathbf{k}$)_ If you prefer the bracket notation, you can also write it as: **$\langle 2, 1, 1 \rangle$** (2/2)
### Part B
1. Just like part A, we are going to break this into three separate, basic Calculus 1 limit problems. This time, $t$ is not going to 0; $t$ is going to **infinity ($\infty$)**. When dealing with infinity, plugging the number in doesn't work the same way. Instead, you have to think about **"what happens when this number gets unimaginably huge?"** Let's tackle the three components.
    
    ### 
    
    1. The $\mathbf{i}$ component: $\lim_{t \to \infty} \frac{t + 1}{t - 1}$
    
    If you plug a billion into this, you get $\frac{1,000,000,001}{999,999,999}$. As the numbers get bigger and bigger, that $+1$ and $-1$ matter less and less. **The Rule for Polynomials at Infinity:** When you have a fraction with polynomials going to infinity, you only look at the term with the highest exponent on the top and the bottom. You can literally cross out everything else because it becomes microscopic noise.
    
    - Highest term on top: $t$
    - Highest term on bottom: $t$
    
    So the limit simplifies to just: $$ \lim_{t \to \infty} \frac{t}{t} $$ Anything divided by itself is 1. **The $\mathbf{i}$ component is $1$.** (Alternative way: You could also use L'Hôpital's Rule here! Since you get $\frac{\infty}{\infty}$, take the derivative of the top (1) and the derivative of the bottom (1). $1/1 = 1$.) ***
    
    ### 
    
    2. The $\mathbf{j}$ component: $\lim_{t \to \infty} \left(1 + \frac{1}{t}\right)^t$ This one is actually a famous "trick" question. It looks incredibly complicated to solve algebraically, but you aren't actually supposed to calculate it—you are supposed to recognize it. In Calculus, this specific limit is the **literal, mathematical definition of the number $e$**. Just like you memorize that $\pi \approx 3.14$, you are expected to memorize that as $t$ gets infinitely large, the expression $(1 + \frac{1}{t})^t$ perfectly settles onto the number $e$ (which is about 2.718). There is no math to do here; it is pure recognition. **The $\mathbf{j}$ component is $e$.** *** (1/2)
    
2. ### 
    
    3. The $\mathbf{k}$ component: $\lim_{t \to \infty} \arctan(t)$
    
    $\arctan(t)$ (also written as $\tan^{-1}(t)$) asks a specific question: _"What angle gives me a tangent of $t$?"_ To solve this as $t$ goes to infinity, you have to picture the graph of the tangent function, or think about the unit circle.
    
    - Tangent is defined as $\frac{\sin}{\cos}$, or $\frac{y}{x}$.
    - As you move around the unit circle, you eventually reach the top, exactly at $90^\circ$ (which is $\frac{\pi}{2}$ radians).
    - At that exact top point, the $x$-coordinate is 0. So your tangent fraction becomes $\frac{1}{0}$.
    - Dividing by zero causes a massive mathematical explosion, sending the tangent graph shooting straight up into infinity.
    
    So, working backwards: if the tangent shoots to infinity precisely when the angle gets to $\frac{\pi}{2}$, then the _inverse_ tangent ($\arctan$) of infinity must be $\frac{\pi}{2}$. Like the $e$ problem above, this is something you are generally just expected to memorize the graph for: the $\arctan$ graph has a horizontal ceiling (asymptote) that it can never cross, and that ceiling is exactly at $\frac{\pi}{2}$. **The $\mathbf{k}$ component is $\frac{\pi}{2}$.** ***
    
    ### Putting it all together
    
    We have our three separate answers. Let's put the labels back on. The final answer is:** $1\mathbf{i} + e\mathbf{j} + \frac{\pi}{2}\mathbf{k}$ **Or in bracket notation:** $\left\langle 1, e, \frac{\pi}{2} \right\rangle$** (2/2)

## Q23 ![[image-34.png]]
1. The secret here is exactly the same as taking the limit of a vector: **you don't do 3D math; you just do three separate Calc 1 problems.** When you integrate a vector, you just integrate the $\mathbf{i}$ part, integrate the $\mathbf{j}$ part, and integrate the $\mathbf{k}$ part separately. Here is the integral we are solving: $$ \int \left( \frac{1}{t}\mathbf{i} + 1\mathbf{j} - t^{3/2}\mathbf{k} \right) dt $$ Let's break it down piece by piece.
    
    ### 
    
    1. The $\mathbf{i}$ component: $\int \frac{1}{t} , dt$
    
    This is a standard Calc 1 memorization rule. The integral of $\frac{1}{t}$ is the natural logarithm of the absolute value of $t$. _(Why absolute value? Because you can't take the log of a negative number, so we mathematically protect it!)_ $$ \int \frac{1}{t} , dt = \ln|t| $$ **The $\mathbf{i}$ component is $\ln|t|$.**_**### 
    
    2. The $\mathbf{j}$ component: $\int 1 , dt$
    
    Notice there is no number in front of the $\mathbf{j}$ in the problem. In math, an invisible number is always a $1$. The integral of a plain constant number is just that number multiplied by the variable ($t$). $$ \int 1 , dt = 1t = t $$** The $\mathbf{j}$ component is $t$._
    
    ### 
    
    3. The $\mathbf{k}$ component: $\int -t^{3/2} , dt$
    
    For this one, we use the standard "Power Rule" for integrals. The Power Rule says: **Add 1 to the exponent, then divide by that new exponent.**
    
    - **Step A (Add 1):** The current exponent is $\frac{3}{2}$. If we add $1$ (which is the same as adding $\frac{2}{2}$), we get a new exponent of $\frac{5}{2}$. So we have $t^{5/2}$.
    - **Step B (Divide):** Now we have to divide the whole thing by that new exponent, $\frac{5}{2}$. Dividing by a fraction is the same as flipping it upside down and multiplying. So dividing by $\frac{5}{2}$ means we multiply by $\frac{2}{5}$.
    - **Step C (Keep the minus sign):** Don't forget the minus sign that was hanging out in front!
    
    $$ \int -t^{3/2} , dt = -\frac{2}{5}t^{5/2} $$ (1/2)
    
2. **The $\mathbf{k}$ component is $-\frac{2}{5}t^{5/2}$.** ***
    
    ### Putting it all together
    
    Now we put the $\mathbf{i}, \mathbf{j}$, and $\mathbf{k}$ labels back on our three answers. But wait! Because this is an _indefinite_ integral (there are no numbers on the top and bottom of the $\int$ sign), Calc 1 rules say we have to add a "$+ C$" at the end. Since our answer is a vector, our $C$ must also be a vector, so we write it as a bold $\mathbf{C}$ (or $\vec{C}$). The final answer is:** $\ln|t|\mathbf{i} + t\mathbf{j} - \frac{2}{5}t^{5/2}\mathbf{k} + \mathbf{C}$ **Or in bracket notation:** $\left\langle \ln|t|, t, -\frac{2}{5}t^{5/2} \right\rangle + \mathbf{C}$** (2/2)

### part b
1. For part **b**, the overarching rule is the same: break it into three separate Calculus 1 problems. However, this one is a bit of a "boss fight" because it requires a famous Calc 2 technique called **Integration by Parts** for the first two components. Here is our integral: $$ \int \left( \ln(t)\mathbf{i} + t\ln(t)\mathbf{j} + \sqrt[3]{t}\mathbf{k} \right) dt $$ Let's take it piece by piece.
    
    ### 
    
    1. The $\mathbf{i}$ component: $\int \ln(t) , dt$
    
    There is no basic formula for the integral of a logarithm. To solve this, we use **Integration by Parts**, which has the formula: $\int u , dv = uv - \int v , du$. _(Think of this as the "Product Rule" for integrals in reverse)._
    
    - **Choose $u$ and $dv$:** We always pick the logarithm to be $u$ because it's easy to take the derivative of it.
        
        - $u = \ln(t)$ $\implies$ The derivative is $du = \frac{1}{t} dt$
        - $dv = 1 dt$ $\implies$ The integral of 1 is $v = t$
        
    - **Plug into the formula ($uv - \int v , du$):**$$ (\ln(t))(t) - \int (t)\left(\frac{1}{t}\right) dt $$
    - **Simplify and solve:** The $t$ and $\frac{1}{t}$ in the new integral perfectly cancel out to just 1!$$ t\ln(t) - \int 1 , dt $$ The integral of 1 is just $t$, so we get:$$ t\ln(t) - t $$
    
    **The $\mathbf{i}$ component is $t\ln(t) - t$.** ***
    
    ### 
    
    2. The $\mathbf{j}$ component: $\int t\ln(t) , dt$
    
    This requires Integration by Parts again, because we have two different types of math multiplying each other (an algebra $t$ and a logarithm $\ln(t)$).
    
    **Choose $u$ and $dv$: **Again, we always let $u$ be the logarithm.
    
    - $u = \ln(t)$ $\implies$ The derivative is $du = \frac{1}{t} dt$
        
        - $dv = t , dt$ $\implies$ The integral (using the power rule) is $v = \frac{1}{2}t^2$**Plug into the formula ($uv - \int v , du$): **$$ (\ln(t))\left(\frac{1}{2}t^2\right) - \int \left(\frac{1}{2}t^2\right)\left(\frac{1}{t}\right) dt $$**Simplify and solve:** (1/2)
    
2. Let's clean up the new integral. The $t^2$ divided by $t$ just becomes a single $t$. We can also pull the $\frac{1}{2}$ out to the front. $$ \frac{1}{2}t^2\ln(t) - \frac{1}{2} \int t , dt $$ Now just use the power rule on that last $t$ (which becomes $\frac{1}{2}t^2$): $$ \frac{1}{2}t^2\ln(t) - \frac{1}{2} \left( \frac{1}{2}t^2 \right) $$ $$ \frac{1}{2}t^2\ln(t) - \frac{1}{4}t^2 $$ **The $\mathbf{j}$ component is $\frac{1}{2}t^2\ln(t) - \frac{1}{4}t^2$.** ***
    
    ### 
    
    3. The $\mathbf{k}$ component: $\int \sqrt[3]{t} , dt$
    
    This one is much friendlier. A cube root is just a fractional exponent, so $\sqrt[3]{t}$ is exactly the same thing as $t^{1/3}$. We just use the standard Power Rule:** Add 1 to the exponent, then divide by that new exponent.Step A (Add 1): **The current exponent is $\frac{1}{3}$. If we add $1$ (which is $\frac{3}{3}$), we get a new exponent of $\frac{4}{3}$. So we have $t^{4/3}$.**Step B (Divide): **Now divide by the new exponent, $\frac{4}{3}$. Dividing by a fraction is the same as flipping it upside down and multiplying. So we multiply by $\frac{3}{4}$. $$ \int t^{1/3} , dt = \frac{3}{4}t^{4/3} $$** The $\mathbf{k}$ component is $\frac{3}{4}t^{4/3}$. *****
    
    ### Putting it all together
    
    We did all the heavy lifting! Now we just put the vector back together. Because it is an indefinite integral, we must add our vector constant, **$\mathbf{C}$**, at the very end. The final answer is: **$(t\ln(t) - t)\mathbf{i} + \left(\frac{1}{2}t^2\ln(t) - \frac{1}{4}t^2\right)\mathbf{j} + \frac{3}{4}t^{4/3}\mathbf{k} + \mathbf{C}$** Or in bracket notation: **$\left\langle t\ln(t) - t, \ \frac{1}{2}t^2\ln(t) - \frac{1}{4}t^2, \ \frac{3}{4}t^{4/3} \right\rangle + \mathbf{C}$** (2/2)
1. **Step 1: Find the direction vector of the line** The line of intersection lies on both planes, so its direction vector $\vec{v}$ must be orthogonal (perpendicular) to the normal vectors of both planes. We find this by taking the cross product of the two normal vectors, $\vec{n}_1 \times \vec{n}_2$.
    
    - Normal vector of plane 1: $\vec{n}_1 = \langle 1, -2, 1 \rangle$
    - Normal vector of plane 2: $\vec{n}_2 = \langle 1, 2, 1 \rangle$
    
    Calculate the cross product: $$ \vec{v} = \vec{n}_1 \times \vec{n}_2 = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \ 1 & -2 & 1 \ 1 & 2 & 1 \end{vmatrix} $$ $$ \vec{v} = \vec{i}[(-2)(1) - (1)(2)] - \vec{j}[(1)(1) - (1)(1)] + \vec{k}[(1)(2) - (-2)(1)] $$ $$ \vec{v} = \vec{i}(-4) - \vec{j}(0) + \vec{k}(4) = \langle -4, 0, 4 \rangle $$ _Note: Since any scalar multiple of a direction vector works for a line, we can divide by 4 to simplify it to $\vec{v} = \langle -1, 0, 1 \rangle$. (Using $\langle -4, 0, 4 \rangle$ is also perfectly correct)._ **Step 2: Find a point on the line of intersection** We need to find any point $(x, y, z)$ that satisfies both plane equations simultaneously. We can do this by eliminating one of the variables. Let's add the two equations together to eliminate $y$: $$ (x - 2y + z) + (x + 2y + z) = 4 + 2 $$ $$ 2x + 2z = 6 $$ $$ x + z = 3 $$ Let's pick an arbitrary value for one variable to find a specific point. Let's set $z = 0$: $$ x + 0 = 3 \implies x = 3 $$ Now, plug $x = 3$ and $z = 0$ back into the first plane equation to find $y$: $$ (3) - 2y + (0) = 4 $$ $$ -2y = 1 \implies y = -\frac{1}{2} $$ So, a point on the line is $P(3, -\frac{1}{2}, 0)$. **Step 3: Write the parametric equations** (1/2)
    
2. Using our point $(x_0, y_0, z_0) = (3, -\frac{1}{2}, 0)$ and our simplified direction vector $\langle a, b, c \rangle = \langle -1, 0, 1 \rangle$, we plug them into the standard parametric format: $x = x_0 + at$ $y = y_0 + bt$ $z = z_0 + ct$
    
    ### Final Answer
    
    $$ x = 3 - t $$ $$ y = -\frac{1}{2} $$ $$ z = t $$ _(Note: Depending on which point you found or if you didn't simplify the direction vector, equivalent correct answers exist, such as $x = 3 - 4t$, $y = -1/2$, $z = 4t$ or finding a different starting point like $(0, -1/2, 3)$ which would give $x = -t$, $y = -1/2$, $z = 3+t$.)_ (2/2)

## Q3 ![[image-13 1.png]]
**Step 1: Substitute the line's parametric equations into the plane equation** To find if they intersect, we replace $x$, $y$, and $z$ in the plane equation with their corresponding functions of $t$ from the line: $$ 2(1 + t) + (1 - t) - (2t) = 2 $$ **Step 2: Solve for $t$** Distribute and combine like terms: $$ 2 + 2t + 1 - t - 2t = 2 $$ $$ (2 + 1) + (2t - t - 2t) = 2 $$ $$ 3 - t = 2 $$ Subtract 3 from both sides: $$ -t = -1 $$ $$ t = 1 $$ **Step 3: Interpret the result** Because we found a single, valid real number for $t$, it means the line intersects the plane at exactly one point (specifically, when $t = 1$). _(Optional: If you plug $t = 1$ back into the line equations, you find the exact point of intersection is $(2, 0, 2)$)._

### Final Answer

**Yes**, the line intersects the plane.


## Q4 ![[image-14 1.png]]
1. **Step 1: Extract the direction vectors for both lines** The direction vector is made up of the coefficients of the parameters ($t$ and $s$) in each component.
    
    - For Line 1, the direction vector is $\vec{v}_1 = \langle 1, 1, 2 \rangle$.
    - For Line 2, the direction vector is $\vec{v}_2 = \langle 2, 1, 3 \rangle$.
    
    **Step 2: Find the normal vector of the plane** Since the plane contains both lines, its normal vector $\vec{n}$ must be orthogonal (perpendicular) to both direction vectors. We find this using the cross product $\vec{v}_1 \times \vec{v}_2$: $$ \vec{n} = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \ 1 & 1 & 2 \ 2 & 1 & 3 \end{vmatrix} $$
    
    - **$\vec{i}$ component:** $(1)(3) - (2)(1) = 3 - 2 = 1$
    - **$\vec{j}$ component:** $-[ (1)(3) - (2)(2) ] = -[ 3 - 4 ] = -[-1] = 1$
    - **$\vec{k}$ component:** $(1)(1) - (1)(2) = 1 - 2 = -1$
    
    So, the normal vector is $\vec{n} = \langle 1, 1, -1 \rangle$. **Step 3: Find a point on the plane** Since the plane contains both lines, any point on either line is also on the plane. The easiest way to find a point is to set $t = 0$ in the first line's equation: $x(0) = 2 + 0 = 2$ $y(0) = 1 + 0 = 1$ $z(0) = 2(0) = 0$ This gives us the point $P(2, 1, 0)$. _(Note: You could also use $s=0$ for the second line to get $(1, 2, 0)$, or even their intersection point, and you would get the exact same final equation)._ **Step 4: Write the equation of the plane** The scalar equation of a plane is $a(x - x_0) + b(y - y_0) + c(z - z_0) = 0$, where $\langle a, b, c \rangle$ is the normal vector and $(x_0, y_0, z_0)$ is a point on the plane. Plugging in $\vec{n} = \langle 1, 1, -1 \rangle$ and $P(2, 1, 0)$: (1/2)
    
2. $$ 1(x - 2) + 1(y - 1) - 1(z - 0) = 0 $$ Now, simplify it: $$ x - 2 + y - 1 - z = 0 $$ $$ x + y - z - 3 = 0 $$
    
    ### Final Answer
    
    $$ x + y - z = 3 $$ (2/2)
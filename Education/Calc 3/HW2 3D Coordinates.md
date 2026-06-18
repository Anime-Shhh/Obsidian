
![[image 1.png]]

### Step 1: Find the differences for each coordinate

- **$x$-difference:** $-3 - (-1) = -3 + 1 = \mathbf{-2}$
- **$y$-difference:** $-6 - (-5) = -6 + 5 = \mathbf{-1}$
- **$z$-difference:** $9 - (-9) = 9 + 9 = \mathbf{18}$

### Step 2: Square those differences

- $(-2)^2 = \mathbf{4}$
- $(-1)^2 = \mathbf{1}$
- $(18)^2 = \mathbf{324}$

### Step 3: Add them together inside the square root

$d = \sqrt{4 + 1 + 324}$ $d = \sqrt{329}$
simplify if possible, but not in this case


![[image-1 1.png]]
When a box has faces parallel to the $xy$, $xz$, and $yz$ planes, it means all of its edges are perfectly straight up/down, left/right, or forward/backward along the $x$, $y$, and $z$ axes. Because of this, **every single corner of the box must share its $x$, $y$, and $z$ coordinates with the other corners.** You can't introduce a completely new number for a coordinate because that would mean the face is slanted or sticking out!

### Step 2: Extract the valid coordinates

You are given two opposite corners: **$(1, 2, 7)$** and **$(9, 11, 12)$**. To find the remaining 6 corners, we just take every possible combination of the $x$, $y$, and $z$ values from these two points. This gives us our strict mathematical rules for a valid corner:

- The **$x$-coordinate** MUST be either **$1$** or **$9$**.
- The **$y$-coordinate** MUST be either **$2$** or **$11$**.
- The **$z$-coordinate** MUST be either **$7$** or **$12$**.

![[image-2 1.png]]
### Step 1: Set up the equation with the center

The standard equation of a sphere is $(x - h)^2 + (y - k)^2 + (z - l)^2 = r^2$. Our center $(h, k, l)$ is **$(1, -1, -4)$**. Plugging that in (and remembering to flip the signs!): $(x - 1)^2 + (y - (-1))^2 + (z - (-4))^2 = r^2$ **$(x - 1)^2 + (y + 1)^2 + (z + 4)^2 = r^2$**

### Step 2: Find the radius

The radius is just the distance from the center $(1, -1, -4)$ to the point on the sphere $(1, 2, 0)$. We'll use the 3D distance formula we practiced earlier!

- **x-difference:** $1 - 1 = \mathbf{0}$
- **y-difference:** $2 - (-1) = \mathbf{3}$
- **z-difference:** $0 - (-4) = \mathbf{4}$

Now square them and add them up: $r = \sqrt{0^2 + 3^2 + 4^2}$ $r = \sqrt{0 + 9 + 16}$ $r = \sqrt{25}$ **$r = 5$**

### Step 3: Write the final equation

Now we know the radius $r = 5$, which means **$r^2 = 25$**. Plug that into the right side of the equation from Step 1. Here is the exact answer to enter in the box: **`(x - 1)^2 + (y + 1)^2 + (z + 4)^2 = 25`**
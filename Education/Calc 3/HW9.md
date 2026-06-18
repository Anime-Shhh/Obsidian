## Q1 ![[image-6 2.png]]
### Step 1: Derivative of the $x$-component

$$x(t) = \frac{-6}{-4t + 5}$$ Instead of the quotient rule, it's easier to rewrite this with a negative exponent and use the chain rule: $$x(t) = -6(-4t + 5)^{-1}$$ Bring down the $-1$, subtract $1$ from the power, and multiply by the derivative of the inside (which is $-4$): $$x'(t) = -6 \cdot (-1)(-4t + 5)^{-2} \cdot (-4)$$ $$x'(t) = -24(-4t + 5)^{-2}$$ **$x'(t) = \frac{-24}{(-4t + 5)^2}$**

### Step 2: Derivative of the $y$-component

$$y(t) = \frac{-6t}{-5t^2 + 2}$$ Here we use the Quotient Rule.

- Top ($f$) $= -6t \implies f' = -6$
- Bottom ($g$) $= -5t^2 + 2 \implies g' = -10t$

$$y'(t) = \frac{f'g - fg'}{g^2}$$ $$y'(t) = \frac{-6(-5t^2 + 2) - (-6t)(-10t)}{(-5t^2 + 2)^2}$$ $$y'(t) = \frac{30t^2 - 12 - 60t^2}{(-5t^2 + 2)^2}$$ **$y'(t) = \frac{-30t^2 - 12}{(-5t^2 + 2)^2}$**

### Step 3: Derivative of the $z$-component

$$z(t) = \frac{7t^2}{-4t^3 + 2}$$ We use the Quotient Rule again.

- Top ($f$) $= 7t^2 \implies f' = 14t$
- Bottom ($g$) $= -4t^3 + 2 \implies g' = -12t^2$

$$z'(t) = \frac{f'g - fg'}{g^2}$$ $$z'(t) = \frac{14t(-4t^3 + 2) - (7t^2)(-12t^2)}{(-4t^3 + 2)^2}$$ $$z'(t) = \frac{-56t^4 + 28t - (-84t^4)}{(-4t^3 + 2)^2}$$ $$z'(t) = \frac{-56t^4 + 28t + 84t^4}{(-4t^3 + 2)^2}$$ **$z'(t) = \frac{28t^4 + 28t}{(-4t^3 + 2)^2}$** ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

**Box 1: **`(-24)/(-4t+5)^2`** Box 2: **`(-30t^2-12)/(-5t^2+2)^2`** Box 3:** `(28t^4+28t)/(-4t^3+2)^2`


## Q2 ![[image 3.png]]
### Step 1: Derivative of the $x$-component

$$x(t) = 3\sin(-3t - 4)$$ Here we use the **Chain Rule**. The derivative of the outside (the sine function) is cosine, and then we multiply by the derivative of the inside (the $-3t - 4$).

- Outside derivative: $3\cos(-3t - 4)$
- Inside derivative: $-3$

Multiply them together: $$x'(t) = 3\cos(-3t - 4) \cdot (-3)$$ **$x'(t) = -9\cos(-3t - 4)$**

### Step 2: Derivative of the $y$-component

$$y(t) = 5te^{-t}$$ Because we have two functions of $t$ multiplied together ($5t$ and $e^{-t}$), we must use the **Product Rule** $(f'g + fg')$.

- $f = 5t \implies f' = 5$
- $g = e^{-t} \implies g' = -e^{-t}$ _(Using the chain rule on the exponent!)_

Now plug them into the Product Rule formula: $$y'(t) = (5)(e^{-t}) + (5t)(-e^{-t})$$ **$y'(t) = 5e^{-t} - 5te^{-t}$**

### Step 3: Derivative of the $z$-component

$$z(t) = -2t\ln(-2t)$$ Again, we have two functions of $t$ being multiplied ($-2t$ and $\ln(-2t)$), so we use the **Product Rule** again.

- $f = -2t \implies f' = -2$
- $g = \ln(-2t) \implies g' = \frac{1}{-2t} \cdot (-2) = \frac{1}{t}$ _(The derivative of $\ln(u)$ is $\frac{1}{u} \cdot u'$)_

Now plug them into the Product Rule formula: $$z'(t) = (-2)(\ln(-2t)) + (-2t)\left(\frac{1}{t}\right)$$ The $t$ on the top and bottom of the second term cancel out: **$z'(t) = -2\ln(-2t) - 2$** ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

**Box 1: **`-9\cos(-3t-4)`** Box 2: **`5e^{-t} - 5te^{-t}`** Box 3:** `-2\ln(-2t) - 2`

## Q3 ![[image-1 3.png]]
### Step 1: Integrate the $x$-component

$$x(t) = \sqrt{t+4}$$ First, rewrite the square root as a fractional exponent: $(t+4)^{1/2}$. Now use the reverse power rule (add 1 to the exponent, then divide by the new exponent). Since the derivative of the inside $(t+4)$ is just 1, we don't need a complex u-substitution.

- New exponent: $\frac{1}{2} + 1 = \frac{3}{2}$
- Divide by new exponent: dividing by $\frac{3}{2}$ is the same as multiplying by $\frac{2}{3}$.

**$\int x(t) dt = \frac{2}{3}(t+4)^{3/2}$**

### Step 2: Integrate the $y$-component

$$y(t) = -4\cos(3t)$$ We know the integral of $\cos(t)$ is $\sin(t)$. Because there is a $3t$ inside, we have to divide by $3$ (this is the reverse of the chain rule).

- Leave the constant $-4$ in front.
- The integral of $\cos(3t)$ is $\frac{1}{3}\sin(3t)$.

Multiply them together: **$\int y(t) dt = -\frac{4}{3}\sin(3t)$**

### Step 3: Integrate the $z$-component

$$z(t) = \frac{-3}{t-5}$$ Pull the constant $-3$ out to the front so it looks like $-3 \cdot \frac{1}{t-5}$. The integral of $\frac{1}{u}$ is $\ln|u|$. Since the derivative of $(t-5)$ is just $1$, it's a direct integration. **$\int z(t) dt = -3\ln|t-5|$** _(Note: Most online homework systems prefer the absolute value bars `| |` for logarithms resulting from integration, but some will accept standard parentheses `()` if the domain is assumed to be positive)._ ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

**Box 1: **`(2/3)(t+4)^(3/2)`** Box 2: **`-(4/3)\sin(3t)`** Box 3:** `-3\ln|t-5|`


## Q4 ![[image-2 3.png]]
### Step 1: Evaluate the $x$-component

$$x(t) = 2e^{5t}$$

- **Antiderivative:** The integral of $e^{kt}$ is $\frac{1}{k}e^{kt}$. So the integral is $\frac{2}{5}e^{5t}$.
- **Evaluate:** plug in $13$ and subtract plugging in $5$:

$$\left[ \frac{2}{5}e^{5(13)} \right] - \left[ \frac{2}{5}e^{5(5)} \right]$$ $$= \frac{2}{5}e^{65} - \frac{2}{5}e^{25}$$ **$x$-value:** **$\frac{2}{5}(e^{65} - e^{25})$**

### Step 2: Evaluate the $y$-component

$$y(t) = \frac{1}{t-4}$$

- **Antiderivative:** The integral of $\frac{1}{u}$ is $\ln|u|$. Since the derivative of $(t-4)$ is $1$, it's a direct integration: $\ln|t-4|$.
- **Evaluate:** plug in $13$ and subtract plugging in $5$:

$$[\ln|13-4|] - [\ln|5-4|]$$ $$= \ln(9) - \ln(1)$$ Since $\ln(1) = 0$, we are left with just $\ln(9)$. **$y$-value:** **$\ln(9)$**

### Step 3: Evaluate the $z$-component

$$z(t) = \sqrt[3]{t-5}$$

- **Antiderivative:** Rewrite as a fractional exponent: $(t-5)^{1/3}$. Use the power rule (add $1$ to exponent, divide by new exponent). $\frac{1}{3} + 1 = \frac{4}{3}$. Dividing by $\frac{4}{3}$ is multiplying by $\frac{3}{4}$. The antiderivative is $\frac{3}{4}(t-5)^{4/3}$.
- **Evaluate:** plug in $13$ and subtract plugging in $5$:

$$\left[ \frac{3}{4}(13-5)^{4/3} \right] - \left[ \frac{3}{4}(5-5)^{4/3} \right]$$ $$\left[ \frac{3}{4}(8)^{4/3} \right] - \left[ \frac{3}{4}(0)^{4/3} \right]$$ To calculate $8^{4/3}$, take the cube root first ($=2$), then raise it to the 4th power ($2^4 = 16$). $$= \frac{3}{4}(16) - 0$$ $$= 3 \cdot 4 = 12$$ **$z$-value:** **$12$** ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answers to type in:

**Box 1: **`(2/5)(e^65 - e^25)`** Box 2: **`\ln(9)`** Box 3:** `12`

## Q5 
![[image-3 3.png]]
### Step 1: Evaluate the $x$-component

$$x(t) = \cos(t)$$

- **Antiderivative:** The integral of $\cos(t)$ is $\sin(t)$.
- **Evaluate:** Plug in the upper bound ($\frac{\pi}{3}$) and subtract the lower bound ($0$):

$$[\sin(\frac{\pi}{3})] - [\sin(0)]$$ From the unit circle, $\sin(\frac{\pi}{3}) = \frac{\sqrt{3}}{2}$ and $\sin(0) = 0$. $$= \frac{\sqrt{3}}{2} - 0$$ **$x$-value:** **$\frac{\sqrt{3}}{2}$**

### Step 2: Evaluate the $y$-component

$$y(t) = \sin(t)$$

- **Antiderivative:** The integral of $\sin(t)$ is $-\cos(t)$.
- **Evaluate:** Plug in the upper bound ($\frac{\pi}{3}$) and subtract the lower bound ($0$):

$$[-\cos(\frac{\pi}{3})] - [-\cos(0)]$$ From the unit circle, $\cos(\frac{\pi}{3}) = \frac{1}{2}$, so $-\cos(\frac{\pi}{3}) = -\frac{1}{2}$. Also, $\cos(0) = 1$, so $-\cos(0) = -1$. $$= \left( -\frac{1}{2} \right) - (-1)$$ $$= -\frac{1}{2} + 1 = \frac{1}{2}$$ **$y$-value:** **$\frac{1}{2}$** ***

###  ![📝](https://discord.com/assets/5f6b1b0353091184.svg) Final Answer to type in:

Since there is only one big input box for the whole vector, make sure to include the angle brackets and comma!** `< \sqrt{3}/2, 1/2 >`**
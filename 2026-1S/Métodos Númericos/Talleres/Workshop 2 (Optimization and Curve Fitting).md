# 1. Tank (Optimization)
You can check the official Presentation :D, click [[Taller 2 - Métodos Numéricos (2026-1).pdf|Workshop 2]]
For searching the maximum or minimum in this case we need to understand that the first issue is know a function $A$ with only one variable $h$ or $r$ doesn't matter which one of both is the best, we will know that the best option would be $h$ because in the V formula that the example give us $r^2$ is easier to clean.
$\dfrac{6 V}{\pi h} = h^2 + 3r^2 \xrightarrow{}{} r^2 =\dfrac{2V}{\pi h} - \dfrac{h^2}{3}$
obtaining $$A = \pi \left(h^2 + \dfrac{0.4}{\pi h} - \dfrac{h^2}{3}\right) \Rightarrow \pi \left(\dfrac{0.4}{\pi h}+\dfrac{2h^2}{3}\right)$$
We got it, the function for A in terms of h, $A(h)$ this is so easy to solve using some of the methods that we know, in this case we will use `golden_section_key` 

## Code
```python
def golden_section_search(f, a: float, b: float, opt: bool, epsilon_x: float = 1e-4, epsilon_r: float = 1e-2, n: int = 10) -> float:
    """Golden Section Search useful for searching maxima or minima in one variable functions"""
    x0 = a - 1
    xf = b + 1
    dx = 1e-2
    xold = None
    # Method
    GR = (np.sqrt(5) - 1) / 2
    d = GR * (b - a)
    x1 = a + d
    x2 = b - d
    f1 = f(x1)
    f2 = f(x2)

    for i in range(n):
        if opt:
            optimization = "maximum"
            condition = f1 > f2
            print(f"Main idea: {a} < {x2} < {x1} < {b}")
        else:
            optimization = "minimum"
            condition = f1 < f2
        if condition:
            a = x2 # Discard interval [a, x2]
            x2 = x1 # Note that new_x2 = old_x1 (golden number made that)
            f2 = f1
            d = GR * (b - a)

            x1 = a + d # only recomputes the x1 in this case
            f1 = f(x1)
            x_opt = (x1 + x2) / 2
            print(f"Estimated {optimization} at ({x_opt}, {f(x_opt)})")
            if xold is not None:
                error = np.abs((x_opt - xold) / x_opt)
                if error <= epsilon_r or (b - a) <= epsilon_x:
                    print(f"Converges in iteration {i + 1}, maximum in: ({x_opt}, {f(x_opt)}) \n interval size: {b - a} and relative approximate error: {error}")
                    break
            xold = x_opt
        else:
            b = x1 # Discard [x1, b]
            x1 = x2
            f1 = f2
            d = GR * (b - a)

            x2 = b - d
            f2 = f(x2)
            x_opt = (x1 + x2) / 2
            print(f"Estimated {optimization} at ({x_opt}, {f(x_opt)})")
            if xold is not None:
                error = np.abs((x_opt - xold) / x_opt)
                if error <= epsilon_r or (b - a) <= epsilon_x:
                    print(f"Converges in iteration {i + 1}, maximum in: ({x_opt}, {f(x_opt)}) \n interval size: {b - a} and relative approximate error: {error}")
                    break
            xold = x_opt
    x = np.arange(x0, xf + dx, dx)
    f_an = f(x)
    fig, ax = plt.subplots(1, 1, figsize=(8, 6), dpi=150)

    ax.plot(x, f_an, 'c--', linewidth=2, label="Function $A(h)$")
    ax.plot(x_opt, f(x_opt), 'ro', markersize=8, zorder=5, 
                   label=f"Critical {optimization}")
        
    ax.axvline(x=x_opt, color="gray", linestyle="--", linewidth=1, alpha=0.7)
    ax.axhline(y=f(x_opt), color="gray", linestyle="--", linewidth=1, alpha=0.7)
        
    ax.annotate(f" Optimum: ({x_opt:.2f}, {f(x_opt):.2f})", 
                    xy=(x_opt, f(x_opt)), xytext=(x_opt + 0.5, f(x_opt) + 1),
                    fontsize=10, fontweight='bold', color="darkred")
        
    ax.grid(visible=True, color="gray", linestyle=":", linewidth=0.5, alpha=0.6)
    ax.legend(fontsize=10, loc="upper center", framealpha=0.9)
    ax.set_xlim([x0, xf])
    ax.set_ylim([f(x_opt) - 5, f(x_opt) + 5])
        
    ax.set_title(f"Finding {optimization} using Golden Search Method", 
                     fontsize=14, fontweight='bold', pad=15)
    ax.set_ylabel(r"A $[m^2]$", fontsize=12)
    ax.set_xlabel(r"h $[m]$", fontsize=12, rotation=0, labelpad=15)
        
    ax.spines['top'].set_visible(False)
    ax.spines['right'].set_visible(False)


    maximum_values = (x_opt, f(x_opt)) # tuple
    return maximum_values
```
---
layout: post
title: "How to enable mathjax/latex in github pages"
description: "tested on pc/mobile in chrome"
headline: 
category: latex
tags: [mathjax, latex]
imagefeature: picture-26.jpg
comments: true
mathjax: true
---

# 1. you should have a github pages by using username.github.io or use project pages
# 2. Fork a jekyll theme that you like or just create from scratch yourself,
I forked from https://github.com/hmfaysal/hmfaysal-omega-theme
This theme already enabled the mathjax/latex
# 3. If you create a new one by yourself, you should do this:
 - in `_config.yml`, use `markdown: kramdown`
 - in `_layouts/home.html` or `_includes/head.html` add:
 ```
 {% if page.mathjax %}

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
<script>
        MathJax.Hub.Config({
            config: ["MMLorHTML.js"],
            extensions: ["tex2jax.js","TeX/AMSmath.js","TeX/AMSsymbols.js"],
            jax: ["input/TeX"],
            tex2jax: {
                inlineMath: [ ['$','$'], ["\\(","\\)"] ],
                displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
                processEscapes: false
            },
            TeX: {
                TagSide: "right",
                TagIndent: ".8em",
                MultLineWidth: "85%",
                equationNumbers: {
                   autoNumber: "AMS",
                },
                unicode: {
                   fonts: "STIXGeneral,'Arial Unicode MS'"
                }
            },
            showProcessingMessages: false
        });
</script>
{% endif %}
 ```
  - add `mathjax: true` in your post
  - test your website, it maybe not working on latex/mathjax

 # Problems and solutions

- I forked this theme and I see the origin theme support mathjax/latex, but it is nothing in my theme, all the source
code are the same, but why, why my forked jekyll theme not support mathjax/latex, why my forked jekyll not showing
like the origin.

- I notice that the chrome show that `This page is trying to load scripts from unauthenticated sources` in top right of
the address bar, when I click to load the script, the chrome show that this site is unsafe, and the site bar is become
red.

- So how to enable your github pages support   `https`,
just **replace all the http** to **https**.
- Done

See this:

**The Lorenz Equations**

$$\begin{aligned}
\dot{x} & = \sigma(y-x) \\
\dot{y} & = \rho x - y - xz \\
\dot{z} & = -\beta z + xy
\end{aligned}$$

**The Cauchy-Schwarz Inequality**

$$
\left( \sum_{k=1}^n a_k b_k \right)^{\!\!2} \leq
 \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$

**A Cross Product Formula**

$$
  \mathbf{V}_1 \times \mathbf{V}_2 =
   \begin{vmatrix}
    \mathbf{i} & \mathbf{j} & \mathbf{k} \\
    \frac{\partial X}{\partial u} & \frac{\partial Y}{\partial u} & 0 \\
    \frac{\partial X}{\partial v} & \frac{\partial Y}{\partial v} & 0 \\
   \end{vmatrix}
$$

**The probability of getting \(k\) heads when flipping \(n\) coins is:**

$$P(E) = {n \choose k} p^k (1-p)^{ n-k} $$

**An Identity of Ramanujan**

$$
   \frac{1}{(\sqrt{\phi \sqrt{5}}-\phi) e^{\frac25 \pi}} =
     1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}}
      {1+\frac{e^{-8\pi}} {1+\ldots} } } }
$$

**A Rogers-Ramanujan Identity**

$$
  1 +  \frac{q^2}{(1-q)}+\frac{q^6}{(1-q)(1-q^2)}+\cdots =
    \prod_{j=0}^{\infty}\frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
     \quad\quad \text{for $|q|<1$}.
$$

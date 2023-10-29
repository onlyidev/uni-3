---
tags: [math]
created_at: 2023-10-16, 8:47:20 am
updated_at: 2023-10-16, 9:51:05 am
---
![[Lecture 7 2023-10-16 08.47.26.excalidraw|#xx-small]]

Aukštesnės eilės diff lygtį galima išreikšti pirmos eilės diff lygčių sistema.  
$$y^{(n)}= F(x,y,y',y'',\dots,y^{(n-1)}$$
$$
\begin{align}
y_{0}'=y_{1}, \\
y_{1}'=y_{2}, \\
\vdots  \\
y_{n-2}'=y_{n-1}, \\
y_{n-1}'=F(x,y_{0},y_{1},\dots,y_{n-1}).
\end{align}
$$

Diff lygties $y^{(n)}=F(y^{(n-1)},x)$ sprendimas:
- Keitinys $z(x)=y^{(n-1)}(x)$
- Pirmos eilės diff lygties sprendimas $z'(x)=F(z(x),x)$
- Integravimas

Jei sprendžiame autonominę diff lygtį - galime sumažinti jos laipsnį per vienetą įvesdami keitinį $z=y', x\to y$ (swap and calc $\frac{d}{dx}$)

---
> [!quote] Quote of the day 2023-10-16  
Error generating daily quote
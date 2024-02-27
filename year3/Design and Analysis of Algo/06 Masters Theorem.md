17. $T(n) = 2T(\frac{n}{2})+\frac{n}{\log_n}$
a = 2 , b = 2
$\log^a_b=\log^2_2=1$
$f(n)=\frac{n}{log_n}$
$O(n^klogn logn)$
18. $T(n)=2T(\frac{n}{2})+\frac{n}{\log^2n}$
a=2, b=2
$\log^a_b=\log^2_2=1$
$f(n)=\frac{n}{log^2n}= O(n^klog^pn)$
k=1, p=-2
$p<-1$
$O(n^k)$ where k=1
$O(n)$
19. $T(n)=T(\frac{n}{2})+n^2$
a=1, b=2, k=2, p=0
$log^a_b=log^1_2<k$
since p = 0
$O(n^klog^pn)$
$O(n^2)$
20. $T(n)=2T(\frac{n}{2})+n^2$
21. $T(n)=2T(\frac{n}{2})+n^2log_n$
22. $T(n)=2T(\frac{n}{2})+n^2log_2n$
23. $T(n)=4T(\frac{n}{2})+n^3$
For the above 4 questions, the time complexity is the f(n) part
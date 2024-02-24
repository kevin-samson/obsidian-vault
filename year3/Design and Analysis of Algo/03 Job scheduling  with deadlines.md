### Problem 1
- Max Dead = 5

| Jobs | Profits | Dead Lines |
| ---- | ------- | ---------- |
| J1   | 20      | 2          |
| J2   | 15      | 2          |
| J3   | 10      | 1          |
| J4   | 5       | 3          |
| J5   | 1       | 3          | 

- Jobs have to be arranged in decreasing order of profits
- Maximization problem / Optimization problem 
- Maximum deadline = 3

```tikz
\usepackage{tikz}
\usetikzlibrary{positioning}
\tikzset{
  gray box/.style={
    fill=gray,
    draw=black,
    minimum width={2*#1ex},
    minimum height={2em},
  },
  annotation/.style={
    anchor=north,
  }
}
\begin{document}
\begin{tikzpicture}[node distance=-0.5pt]
  \node [gray box=3] (p1) {\(P_{1}\)};
  \node [gray box=3, right=of p1] (p2) {\(P_{2}\)};
  \node [gray box=3, right=of p2] (p3) {\(J_{3}\)};

  \node [annotation] at (p1.south west) {0};
  \node [annotation] at (p1.south east) {24};
  \node [annotation] at (p2.south east) {27};
  \node [annotation] at (p3.south east) {30};
\end{tikzpicture}
\end{document}
```

### Problem 2
- Max deadlines = 4

| Job | Profit | Deadline | Ranking |
| --- | ------ | -------- | ------- |
| 1   | 3      | 1        | 6       |
| 2   | 5      | 3        | 5       |
| 3   | 20     | 4        | 2       |
| 4   | 18     | 3        | 3       |
| 5   | 0      | 2        | 7       |
| 6   | 6      | 1        | 4       |
| 7   | 20     | 2        | 1       | 

```tikz
\usepackage{tikz}
\usetikzlibrary{positioning}
\tikzset{
  gray box/.style={
    fill=gray,
    draw=black,
    minimum width={2*#1ex},
    minimum height={2em},
  },
  annotation/.style={
    anchor=north,
  }
}
\begin{document}
\begin{tikzpicture}[node distance=-0.5pt]
  \node [gray box=3] (p1) {\(J_{6}\)};
  \node [gray box=3, right=of p1] (p2) {\(J_{7}\)};
  \node [gray box=3, right=of p2] (p3) {\(J_{4}\)};
  \node [gray box=3, right=of p3] (p4) {\(J_{3}\)};


  \node [annotation] at (p1.south west) {0};
  \node [annotation] at (p1.south east) {1};
  \node [annotation] at (p2.south east) {2};
  \node [annotation] at (p3.south east) {3};
  \node [annotation] at (p4.south east) {4};

\end{tikzpicture}
\end{document}
```

### Problem 3
- Rank based on decreasing amount of product
- The largest deadline will show the end of the gantt chart .

| Job | Profit | Deadline | Ranking |
| --- | ------ | -------- | ------- |
| J1  | 85     | 5        | 2       |
| J2  | 25     | 4        | 6       |
| J3  | 16     | 3        | 8       |
| J4  | 40     | 3        | 5       |
| J5  | 55     | 4        | 4       |
| J6  | 19     | 5        | 7       | 
| J7  | 92     | 2        | 1       |
| J8  | 80     | 3        | 3       |
| J9  | 15     | 7        | 9       |

```tikz
\usepackage{tikz}
\usetikzlibrary{positioning}
\tikzset{
  gray box/.style={
    fill=gray,
    draw=black,
    minimum width={2*#1ex},
    minimum height={2em},
  },
  annotation/.style={
    anchor=north,
  }
}
\begin{document}
\begin{tikzpicture}[node distance=-0.5pt]
  \node [gray box=3] (p1) {\(J_{4}\)};
  \node [gray box=3, right=of p1] (p2) {\(J_{7}\)};
  \node [gray box=3, right=of p2] (p3) {\(J_{8}\)};
  \node [gray box=3, right=of p3] (p4) {\(J_{5}\)};
  \node [gray box=3, right=of p4] (p5) {\(J_{1}\)};
  \node [gray box=3, right=of p5] (p6) {\(J_{1}\)};
  \node [gray box=3, right=of p6] (p7) {\(J_{9}\)};


  \node [annotation] at (p1.south west) {0};
  \node [annotation] at (p1.south east) {1};
  \node [annotation] at (p2.south east) {2};
  \node [annotation] at (p3.south east) {3};
  \node [annotation] at (p4.south east) {4};
  \node [annotation] at (p5.south east) {5};
  \node [annotation] at (p6.south east) {6};
  \node [annotation] at (p7.south east) {7};

\end{tikzpicture}
\end{document}
```

- Job Sequence - {J4->J7->J8->J5->J1->J9}
- Jobs not completed - 
- Total Profit

### Problem 4
| Job | profit | Ranking |
| --- | ------ | ------- |
| J1  | 100    | 5       |
| J2  | 90     | 4       |
| J3  | 80     | 2       |
| J4  | 70     | 1       |
| J5  | 60     | 3       |
| J6  | 50     | 7       |
| J7  | 40     | 2       |
| J8  | 30     | 3       |
| J9  | 20     | 7       |

Job Sequence {J4->J3->J5->J2->J1->J10->J6}
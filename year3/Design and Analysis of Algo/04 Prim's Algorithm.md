1. Algorithm used to find minimum cost spanning tree for connected weighted undirected graphics
2. Choose any arbitrary vertex
3. Chosen edge to MST should not form a cycle
4. Graph can have more than 1 spanning tree
5. G(V,E)
6. MST - G'(V',E')

- Remove loops and parallel edges
- Choose any node as root node
```mermaid
flowchart LR
A--7-->B  
A--8-->C
B--3-->C
B--6-->D
D--4-->C
D--2-->E
D--5-->F
E--2-->F
F--1-->F
```

Choose the smallest

| node | edges               |
| ---- | ------------------- |
| A    | 7,**8**             |
| B    | ~~7~~,~~3~~,6       |
| C    | 8,~~3~~,~~4~~,~~5~~ |
| E    |                     |

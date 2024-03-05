## Action
- Shift: Shift the i/p symbol to the TOS
- Reduce: $\beta$ handle A->B ; reduce $\beta$ with A

Input string: 
id*id

`E->E+T|T`
`T->T*F|F`
F->id

| stack | input  | action        |
| ----- | ------ | ------------- |
| $     | id*id$ | shift         |
| $id   | *id$   | reduce F->id  |
| $F    | *id$   | reduce T->F   |
| $T    | *id$   | shift         |
| $T*   | id$    | shift         |
| $T*id | $      | reduce F->id  |
| $T*F  | $      | reduce T->T*F |
| $T    | $      | reduce E->T   |
| $E    | $      | Accept        | 

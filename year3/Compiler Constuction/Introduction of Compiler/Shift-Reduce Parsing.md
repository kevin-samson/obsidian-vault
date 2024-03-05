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
| $T    | *id$   | shift         | -> shift reduce conflict
| $T*   | id$    | shift         |
| $T*id | $      | reduce F->id  |
| $T*F  | $      | reduce T->T*F |
| $T    | $      | reduce E->T   |
| $E    | $      | Accept        | 

## Conflicts in shift-reduce parsing
Parser after knowing the entire stack contents and the current i/p symbol it is unable to decide

1. whether  to shift or to reduce shfit reduce conflict
2. which production rule to use for reduce 

stmt -> if stmt then stmt else stmt
if stmt then stmt
other

| stack               | input       |
| ------------------- | ----------- |
| $ if stmt then stmt | else .... $ |

It is unable to decide which rule to use so it is shift reduce conflict

S->AB
A->OS|1S
B->OS1|1S

| stack | input | action |            |
| ----- | ----- | ------ | ---------- |
| $     | 0S1S$ | shift  |            |
| $0    | S1S$  | shift  |            |
| $0S   | 1S$   | reduce | -> conflict |
| $A    | 1$    | shift  |            |
| $A1   | 1S$   | shift  |            |
| $A1S  | $     | reduce |            |
| $AB   | $     | reduce |            |
| $S    | $     | accept |            |

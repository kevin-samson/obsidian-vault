G:E->E+E | E*E |(E) |id | num

$E->E*E$
$->(E)*E$
$->(E+E)*E$
$->(id+E)*E$

## Ambiguity
- For some strings there exist more than one parse tree 
	- or more than one leftmost derivation 
	- or more than one rightmost derivation
## Bottom up parsing(BUP)
- Given an i/p string, draw the CFG
- Aim is to reach the start symbol thru a series of reduction steps
### What happens at each step
- Sentential form 
- Find a substring that matches the right hand side of the production
- Replace the substring with the LHS(NT)

### Key Challenges
- What reduction rule to use?
- When to reduce?

### Expression Grammar
`E->E*T|T`
`T->T*F|F`
`F->id`

One way to solve ambiguity is to rewrite the grammar
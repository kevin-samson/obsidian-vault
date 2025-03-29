# Steps
1. Formulate goal
2. Formulate problem
3. Find solution

# Types of Search
| Type                    | Examples           |
| ----------------------- | ------------------ |
| Single-Agent            | Traveling salesman |
| Two-Agent               | Chess              |
| Constraint-satisfaction | 8-Queen            |              

# Parts of search
## Agents
| Types of agent                                 |                                                                                                               |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Intelligent problem solving or rational agents | Has goals and tries to perform a series of actions that yield the best outcome or a goal                      |
| Reflex agents                                  | Don't think about the consequences of its actions, and selects and action based on current state of the wold. | 

## Keywords
| Keyword          | Meaning                                                                        |
| ---------------- | ------------------------------------------------------------------------------ |
| Problem          | Definition of general problem as search problem                                |
| Solution         | Sequence of actions that help go from initial state to goal state              |
| Solution Cost    | Cost associated to perform solution                                            |
| Search           | Process of looking for solution                                                |
| State Space      | Set of all states that are possible and can be reached in an enviroment/system |
| State space size | Total number of states. Counted using fundamental counting principle.          |
| Search Tree      | Tree representation of search problem                                          | 

# Heuristic
A heuristic function $h(x)$ is and estimated cost from one node to another
- Heuristic are problem-specific
- Over-estimating get heuristic is better than under-estimating
- As heuristics get closer to he true cost, you will expand fewer nodes but usually do more work per not to compute the heuristic itself 
Eg: Manhattan distance, Euclidean distance

# Un-informed vs Informed search

| Uniformed search           | Informed search                         |
| -------------------------- | --------------------------------------- |
| Search without Information | Search with information                 |
| No knowledge               | Use knowledge to find steps to solution |
| Time consuming             | Quick solution                          |
| More complexity            | Less complexity                         |
| DFS,BFS etc.               | $A^*$,Heuristic DFS, Best first search  | 


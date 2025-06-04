The concept looks into collecting and presenting how the modelled system will behave if specific actions are taken.

![[GameTree.png]]
In the example above, we have node defined numerically and then action that need to be done using letters. The idea is that a move to either node will unlock a new set of moves/nodes that the system can proceed. 
	Chess analogy: If you play with a pawn, you can only move one field ahead. This is level one (2 and 2) of nodes. Once you move, it turns out that now you might have a figure within attack range. Without the first move, you wouldn't have known that. This is what the tree is trying to display

### Explicit Tree
Where you are able to model out the full tree and predict all eventualities

### Implicit tree
Where you only explore a certain region at a time and try to judge the best move from that. This means that the whole tree is not available at all times
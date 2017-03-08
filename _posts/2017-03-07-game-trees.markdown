---
layout: post
categories: AI
date:   2017-03-07 11:36:45 -0800
img: https://upload.wikimedia.org/wikipedia/commons/b/b5/ContextFree_ScragglyTree.png
---
I just learned about the isolation game, and was looking at all the [possible game states](https://s3.amazonaws.com/content.udacity-data.com/courses/ud954/images/isolation-L6_leafValues.svg), organized into a tree, where each child node can be reached from its parent node by one of the players taking their turn.  We were asked consider how to "prune" branches of this tree that lead to loosing outcomes.  I paused continuing the lesson to instead consider: can you come up with a subtree of moves that only allow us to choose "winning" moves?  That is a tree where allow paths lead to winning outcomes.  I might add that you're only allowed to prune off your own moves, since clearly you should have no control over what move your opponent makes among "legal" game moves.

The way I approached this problem was to look at all the situations that would rule out a node's subtree (the tree when considering that node as the root) as giving "control" to me over the situation.  That is a situation where my move could (b) give my opponent a chance to end the game with a next move in which I lose, or (c) be able to steer the game so that the only possible outcomes for me next time round are outcomes where the game ends and I lose.  Lastly, is situation where our opponent can make a choice such that all possible nodes on the next level are "losing" nodes, somehow how in the sense that an adversarial player can choose moves so that they win no matter what further sequence of moves I pick.

![Subtrees]({{site.url}}/assets/searchGameNodes.png)



In the following, to clarify, a "winning" node stands for a subgame (subtree) in which you win as long as you follow a winning strategy.  A "losing" node is one where no matter what sequence of further moves you pick, if you opponent follows an optimal strategy, you will lose.  

Also, keep in mind that "opponents" node's represent a game state where you've made the last move, and your opponent has yet to commit a move.  The set of  leaves branching out from this node represent the set of moves that your opponent makes, each one forming a new and different game state.  Note that you could alternatively represent the game tree [like this](https://en.wikipedia.org/wiki/Game_tree).

![Losing situations from end-of-game]({{site.url}}/assets/searchGameNodes2.png)


To label vertices further going up a level as being "winning":
 1.  for an opponent's node (triangles in the diagram), if all of your moves (that is a leaf of this node) are labeled as "winning", label their parent as "winning".
 2.  for one of your own node's (circles in the diagram), if there exists a leaf (one of your turns) that is labelled "winning", then label the parent as "winning" as well.

![How to make the recursive step]({{site.url}}/assets/searchGameNodes3.png)



 To label vertices further up the tree as having "lost control", or as being losing vertices:
  1. for edges from your turn towards your opponent, if all of your opponent's nodes are labeled "losing",
  2. for an opponent's node (triangles in the diagram), if one of your moves (that is a leaf of this node) is labeled "losing", label the parent node as "losing".


Some questions and observations I've thought of to explore later:
- Given a tree of all possible moves of a two-person deterministic adversarial game, does there always exist a winning strategy for at least one of the players?
- The set of edges from the "winning" and "losing" subtree seem to form a partition of edges of the entire game tree.

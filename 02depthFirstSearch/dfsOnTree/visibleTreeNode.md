# DFS: DFS on Tree
## Visible Tree Node | Number of Visible Nodes
```
In a binary tree, we define a node "visible" when no node on the root-to-itself path (inclusive) has a greater value
The root is always "visible" since there are no other nodes between the root and itself
Given a binary tree, count the number of "visible" nodes

Input:
    5v
   / \
  4   6v
 / \
3   8v

v = visible

Output: 3

For example:
Node 4 is not visible since 5>4, similarly Node 3 is not visible since both 5>3 and 4>3
Node 8 is visible since all 5<=8, 4<=8, and 8<=8
```
```javascript
function visibleTreeNode(root) {
  const dfs = (node, max) => {
    if (!node) return 0;
    let total = 0;
    if (node.val >= max) total++;
    total += dfs(node.left, Math.max(max, node.val));
    total += dfs(node.right, Math.max(max, node.val));
    return total;
  }
  return dfs(root, Number.NEGATIVE_INFINITY);
}
```

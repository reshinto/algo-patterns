# Backtracking pattern
## Combinatorial Search
### DFS with states
#### Ternary Tree Paths
- each node of the tree has at most three children, find all root-to-leaf paths
- use path to keep track of the nodes we have visited to reach the current node and use it to construct our solution when we reach leaf nodes
#### Javascript
```javascript
class Node {
  constructor(val, children = []) {
    this.val = val;
    this.children = children;
  }
}

function dfs(root, path, res) {
  // exit condition, reached leaf node, append paths to results
  if (root.children.length === 0) {
    path.push(root.val);
    const cur_path = path.join('->');
    res.push(cur_path);
    path.pop();
    return;
  }
  // dfs on each non-null child
  for (const child of root.children) {
    if (child) {
      path.push(root.val);
      dfs(child, path, res);
      path.pop();
    }
  }
}

function ternaryTreePaths(root) {
  let res = [];
  if (root) dfs(root, [], res);
  return res;
}

const one = new Node(1);
const two = new Node(2);
const four = new Node(4);
const six = new Node(6);
const three = new Node(3);

one.children = [two, four, six];

two.children = [three];

const result = ternaryTreePaths(one);
console.log(result);
```

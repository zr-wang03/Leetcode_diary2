# 144 Binary Tree Preorder Traversal

* Easy
* Given the `root` of a binary tree, return _the postorder traversal of its nodes' values_.
* [https://leetcode.com/problems/binary-tree-postorder-traversal/](https://leetcode.com/problems/binary-tree-postorder-traversal/)

{% content-ref url="../previous-part-1/featured/tree-questions/binary-search-tree-traversal/144-binary-tree-preorder-traversal.md" %}
[144-binary-tree-preorder-traversal.md](../previous-part-1/featured/tree-questions/binary-search-tree-traversal/144-binary-tree-preorder-traversal.md)
{% endcontent-ref %}

### Solution 1 Recursive

<figure><img src="../.gitbook/assets/image (1) (2).png" alt=""><figcaption></figcaption></figure>

```
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        vector<int> answer;
        preorder(root, answer);
        return answer;
    }
    
private: 
    void preorder(TreeNode* node, vector<int>& answer){
            if (node==NULL){
                return;
            }
            answer.push_back(node->val);
            preorder(node->left,answer);
            preorder(node->right,answer);
    }
};
```

### Solution 2 Iterative

<figure><img src="../.gitbook/assets/image (1) (2) (1).png" alt=""><figcaption></figcaption></figure>

```
class Solution {
public:
    vector<int> preorderTraversal(TreeNode* root) {
        stack<TreeNode*> regi;
        TreeNode* temp;
        vector <int> resp;
        regi.push(root);
        while (!regi.empty()){
            temp=regi.top();
            regi.pop();
            if (temp){
                resp.push_back(temp->val);
                regi.push(temp->right);
                regi.push(temp->left);
            }              
        }            
        return resp;
    }
};
```

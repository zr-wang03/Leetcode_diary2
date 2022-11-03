# 145 Binary Tree Postorder Traversal

* Easy
* Given the `root` of a binary tree, return _the postorder traversal of its nodes' values_.
* [https://leetcode.com/problems/binary-tree-postorder-traversal/](https://leetcode.com/problems/binary-tree-postorder-traversal/)
* ![](<../.gitbook/assets/image (2).png>)

{% content-ref url="../previous-part-1/featured/tree-questions/binary-search-tree-traversal/145-binary-tree-postorder-traversal.md" %}
[145-binary-tree-postorder-traversal.md](../previous-part-1/featured/tree-questions/binary-search-tree-traversal/145-binary-tree-postorder-traversal.md)
{% endcontent-ref %}

### Solution 1 Recursion

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

```
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        vector<int> answer;
        postorder(root, answer);
        return answer;
    }
    
private: 
    void postorder(TreeNode* node, vector<int>& answer){
            if (node==NULL){
                return;
            }
            postorder(node->left,answer);
            postorder(node->right,answer);
            answer.push_back(node->val);
    }
};
```

### Solution 2 Iterative

Note in the above example that by inversing the sequence we get after postorder traversal, we get \[1,3,6,5,8,7,2,4], which is a sequence that we get doing preorder traversal but instead of left before right we have right before left.&#x20;

Therefore the solution takes the right-left postorder traversal and reverse it in the end.&#x20;

<figure><img src="../.gitbook/assets/image (24).png" alt=""><figcaption></figcaption></figure>

```
class Solution {
public:
    vector<int> postorderTraversal(TreeNode* root) {
        stack<TreeNode*> regi;
        TreeNode* temp;
        vector <int> rev_resp,resp;
        regi.push(root);
        while (!regi.empty()){
            temp=regi.top();
            regi.pop();
            if (temp){
                rev_resp.push_back(temp->val);
                regi.push(temp->left);
                regi.push(temp->right);
            }              
        }
        while (!rev_resp.empty()){
            resp.push_back(rev_resp.back());
            rev_resp.pop_back();
        }                
        return resp;
    }
};
```

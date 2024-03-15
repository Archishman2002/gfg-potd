## 16. Flatten BST to sorted list
The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/flatten-bst-to-sorted-list--111950/1)

### My Approach
To flatten a BST into a sorted list, we can perform an in-order traversal of the BST. During the traversal, we keep track of the previous and next nodes to adjust the pointers accordingly. The steps are as follows:
- Initialize `head` and `tail` pointers as `NULL`.
- Perform in-order traversal of the BST.
- While traversing, adjust the pointers of the nodes to form a linked list.
- Finally, return the head of the linked list.

### Time and Auxiliary Space Complexity

- **Time Complexity**: The time complexity of the in-order traversal is `O(n)`, where n is the number of nodes in the BST.
- **Auxiliary Space Complexity**: The space complexity is `O(h)`, where h is the height of the BST.

### Code (C++)
```cpp
class Solution {
public:
    Node* head;
    Node* tail;
    void inOrder(Node* curr){
        if(!curr)
            return;
        
        inOrder(curr->left);
        if(!head)
            head = curr;
        else{
            tail->right = curr;
            curr->left = tail;
        }
        tail = curr;
        inOrder(curr->right);
    }
    Node *flattenBST(Node *root)
    {
        head = tail = NULL;
        inOrder(root);
        return head;
    }
};
```

### Contribution and Support

For discussions, questions, or doubts related to this solution, please visit our [discussion section](https://github.com/getlost01/gfg-potd/discussions). We welcome your input and aim to foster a collaborative learning environment.

If you find this solution helpful, consider supporting us by giving a `⭐ star` to the [getlost01/gfg-potd](https://github.com/getlost01/gfg-potd) repository.

I think the correct code should be (ADDING COMMENTS SO THAT CHANGES  ARE UNDERSTOOD EASILY)

class Solution
{
public:
    void inorder(Node *curr, Node *&prev)
    {
        // Base case
        if (curr == NULL)
            return;
        inorder(curr->left, prev);
        prev->left = NULL;
        prev->right = curr;
        prev = curr;
        inorder(curr->right, prev);
    }
    Node *flattenBST(Node *root)
    {
        // Dummy node
        Node *dummy = new Node(-1);

        // Pointer to previous element
        Node *prev = dummy;

        // Calling in-order traversal
        inorder(root, prev);

        prev->left = NULL;
        prev->right = NULL;
        Node *ret = dummy->right;

        // Delete dummy node
        delete dummy;
        return ret;
    }
};

# Inorder Successor of Given Node


### [Article gfg](https://www.geeksforgeeks.org/inorder-successor-in-binary-search-tree/)


## Code CPP

```

struct node* successor(struct node* root,int data){
    //for finding the reference to the data given
    struct node* current = find(root,data);

    if(current==NULL)
        return NULL;

    //If the right node is not null then the minimum value in the right subtree is the successor
    
    if(current->right != NULL){
        return FindMin(current->right);
    }
    
    //Else The deepest ancestor to the current node for which the current node in the left subtree will be the successor

    else{
        struct node* ancestor = root;
        struct node* successor = NULL;

        while(ancestor!=current){
            if(current->data<ancestor->data){
                successor=ancestor;
                ancestor=ancestor->left;
            }else{
                ancestor=ancestor->right;
            }
        }
        return successor;
    }
}

```

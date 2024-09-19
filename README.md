# Tree-Series
Construct a binary tree from inorder and preorder traversal of a tree.
int preIndex=0;
    TreeNode* cTree(vector<int>& preorder, vector<int>& inorder,int is,int ie){
        if(is>ie){
            return nullptr;
        }
        TreeNode* root=new TreeNode(preorder[preIndex++]); //picking main root from preOrder as pre[0]=root
        int inIndex; //finding same val of root in inOrder arr
        for(int i=is;i<=ie;i++){
            if(inorder[i]==root->val){  //searching root in inOrder
                inIndex=i;
                break;
            }
        }
        root->left=cTree(preorder,inorder,is,inIndex-1); //left subtree formation
        root->right=cTree(preorder,inorder,inIndex+1,ie); //right subtree formation
        return root;
    }
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        return cTree(preorder,inorder,0,preorder.size()-1);
    }
//Try it on leetcode and congrats...

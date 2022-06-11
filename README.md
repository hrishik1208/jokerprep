1 . Burn a tree
<hr>


/**

* Definition for binary tree

* struct TreeNode {

*     int val;

*     TreeNode *left;

*     TreeNode *right;

*     TreeNode(int x) : val(x), left(NULL), right(NULL) {}

* };

*/

int res=0;

int height(TreeNode* root){

if(root==NULL){

return 0;

}

return max(height(root->left),height(root->right))+1;

}

void fake(TreeNode* root,int B,int &val){

if(root==NULL){
    
        return ;
    }
    
    if(root->val == B){
    
    val=1;
    
    int l=height(root->left);
    
    int h=height(root->right);
    
    res=max(res,max(l,h));
    
    return ;
    
    }
    
    fake(root->left,B,val);
    
    if(val!=0){
    
    int h=height(root->right);
    
    res=max(res,val+h);
    
    val++;
    
    return;
    
    }
    
    fake(root->right,B,val);
    
    if(val!=0){
    
    int l=height(root->left);
    
    res=max(res,val+l);
    
    val++;
    
    return ;
    
    }
    
    return;



}

int Solution::solve(TreeNode* A, int B) {

res=0;

int val=0;

fake(A,B,val);

return res;

}

<hr>



# FGB#include <stdio.h>
#include <stdlib.h>

typedef struct BST
{
  int data;
  struct BST *lchild, *rchild;
} node;
struct linkedlist
{
    node * array[50];
    int top;
};
struct list
{
    node * x[50];
    int top;
};
void pushdata(node*r,struct list *l)
{
    l->top+=1;
    l->x[l->top]=r;
}
int empty(struct list *l)
{
    if(l->top==-1)
        return 1;
    return 0;    
}
int removedata(struct list *l)
{
    int num=l->x[l->top]->data;
    l->top-=1;
    return num;
}

int arr[100];
int count1=0,count2=0;
void insert(node *, node *);
void inorder(node *);
void BstTomaxheap(node *);
int i = 0;
void displayTree(node * root)
{
    struct list *p;
    p=(struct list * )malloc(sizeof(struct list));
    p->top=-1;
    node * q;
    q=root;
    int x;
    label:
    while(q!=NULL)
    {
        pushdata(q,p);
        q=q->lchild;
    }
    if(!empty(p))
    {
        printf("%d ",removedata(p));
        q=p->x[p->top+1]->rchild;
        goto label;
    }
    else 
        return;
}
void main()
{
  int choice;
  node *new_node, *root;
  node *create_node();
  root = NULL;

  printf("\nProgram For Binary Search Tree ");
  do
  {
    printf("\n1.Create");
    printf("\n2.inorder");
    printf("\n3.bst to max-");
    printf("\n4.Exit");
    printf("\nEnter your choice :");
    scanf("%d", &choice);
    int count = 0;
    int n;
    switch (choice)
    {
     case 1:

      printf("enter the no. of node");
      scanf("%d", &n);
      do
      {
        new_node = create_node();

        printf("\nEnter The Element ");
        scanf("%d", &new_node->data);

        if (root == NULL) 
          root = new_node;
        else
          insert(root, new_node);
        count++;
      }while (n != count);

      break;

      case 2:
      
      if (root == NULL)
        printf("Tree is Not Created \n");
      else
      
        printf("\nThe Inorder display : ");
        displayTree(root);
       
        break;
        case 3:
        inorder(root);
        BstTomaxheap(root);
        printf("Max heap = ");
        displayTree(root);
    }
 }while (choice != 4) ;
}  

  node *create_node()
  {
    node *temp;
    temp = (node *)malloc(sizeof(node));
    temp->lchild = NULL;
    temp->rchild = NULL;
    return temp;
   }
  void insert(node * root, node * new_node)
  {
    if (new_node->data < root->data)
    {
      if (root->lchild == NULL)
        root->lchild = new_node;
      else
        insert(root->lchild, new_node);
    }

    if (new_node->data > root->data)
    {
      if (root->rchild == NULL)
        root->rchild = new_node;
      else
        insert(root->rchild, new_node);
    }
  }
  void inorder(node * root)
  {
    if (root != NULL)
    {
      inorder(root->lchild);
      arr[count1]=root->data;
      count1++;
      inorder(root->rchild);
    }
  }
  void BstTomaxheap(node * root)
  {
    if (root == NULL)
      return;
    BstTomaxheap(root->lchild);
    BstTomaxheap(root->rchild);
    root->data = arr[count2];
    count2++; 
  }

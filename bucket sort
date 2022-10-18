#include<stdio.h>
#include<stdlib.h>
#include<math.h>
struct node
{
    float info;
    struct node *link;
};
struct node *InsertionSort(struct node *list);
void printBuckets(struct node *list);
void Bucketsort(float A[],int n){
	float b[n-1];
	int i,j;
	struct node **bucket;
	bucket = (struct node **)malloc(sizeof(struct node *) * n);
	for (i = 0; i < n; i++) {
    bucket[i] = NULL;
    }
	for (i = 0; i < n; i++) {
    struct node *curr;
    int p = floor(A[i]*n);
    curr= (struct node *)malloc(sizeof(struct node));
    curr->info = A[i];
    curr->link = bucket[p];
    bucket[p] = curr;
    }
	for (i = 0; i < n; i++) {
    bucket[i] = InsertionSort(bucket[i]);
  	}
    printf("sorted Bucket: ");
  	for (i = 0; i < n; i++) {
    printBuckets(bucket[i] );
  	}
	for (j = 0, i = 0; i < n; ++i) {
    struct node *ptr;
    ptr = bucket[i];
    while (ptr!=NULL) {
      A[j++] = ptr->info;
      ptr = ptr->link;
    }
  }

  return;
}
struct node *InsertionSort(struct node *list) {
  struct node *p, *List;
  if (list == 0 || list->link == 0) {
    return list;
  }

  List = list;
  p = list->link;
  List->link = 0;
  while (p != 0) {
    struct node *ptr;
    if (List->info > p->info) {
      struct node *temp;
      temp = p;
      p = p->link;
      temp->link = List;
      List = temp;
      continue;
    }

    for (ptr = List; ptr->link != 0; ptr = ptr->link) {
      if (ptr->link->info > p->info)
        break;
    }

    if (ptr->link != 0) {
      struct node *temp;
      temp = p;
      p = p->link;
      temp->link = ptr->link;
      ptr->link = temp;
      continue;
    } else {
      ptr->link = p;
      p = p->link;
      ptr->link->link = 0;
      continue;
    }
  }
  return List;
}
void printBuckets(struct node *list) {
  struct node *cur = list;
  while (cur!=NULL) {
    printf("%f ", cur->info);
    cur = cur->link;
  }
}

int main()
{
int i,n;
float A[20];
printf("Enter the value of n: ");
scanf("%d", &n);
printf("Enter the %d array elements \n",n);
for(i=0;i<n;i++)
{
printf("A[%d]=",i);
scanf("%f",A+i);
}
Bucketsort(A,n);

return 0;
}

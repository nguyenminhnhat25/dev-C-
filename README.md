# dev-C-
dev c++


##...
#include<stdio.h>

// dinh nghia cau truc cua 1 node
struct NODE{
    int data;
    struct NODE *pNext;
};

// dinh nghia cau truc cua 1 list
struct LIST{
    NODE *pHead;
    NODE *pTail;
};

// viet ham de tao 1 node
NODE *createNode()
{
    int x;
    printf("Nhap gia tri cua node:");
    scanf("%d", &x);
    NODE *p=new NODE();
    p->data=x;
    p->pNext=NULL;
    return p;
}
//them 1 node vao dau danh sach
void AddHead(LIST &l, NODE*p)
{
    if(l.pHead==NULL)
        l.pHead=l.pTail=p;
    else
    {
        p->pNext=l.pHead;
        l.pHead=p;
    }
} 

int main()
{
    LIST l;
    int n;
    printf("nhap so luong node cua danh sach:");
    scanf("%d", &n);
    int i=1;
    while (i<=n)
    {
        NODE *p=createNode();
        AddHead(l,p);
        i++;
    }
    printf("danh sach vua nhap la:");

    for(NODE *p=l.pHead; p!=NULL; p=p->pNext)
        printf("%d\t", p->data);
}

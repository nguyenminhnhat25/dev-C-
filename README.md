# dev-C-
dev c++


##them 1 nut vao dau danh sach
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

##them 1 nut vao cuoi danh sach
#include <stdio.h>
#include <stdlib.h>

// d?nh nghia c?u trúc c?a m?t nút
struct Node {
    int data;
    struct Node *next;
};

// d?nh nghia c?u trúc c?a danh sách liên k?t
struct LinkedList {
    struct Node *head;
    struct Node *tail;
};

// hàm t?o m?t nút m?i
struct Node *createNode(int data) {
    struct Node *newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// hàm thêm m?t nút vào cu?i danh sách liên k?t
void addToEnd(struct LinkedList *list, int data) {
    // t?o m?t nút m?i
    struct Node *newNode = createNode(data);

    // ki?m tra xem danh sách có r?ng hay không
    if (list->head == NULL) {
        // n?u danh sách r?ng, nút m?i s? là nút d?u tiên c?a danh sách
        list->head = newNode;
        list->tail = newNode;
    } else {
        // n?u danh sách không r?ng, thêm nút m?i vào sau nút cu?i cùng
        list->tail->next = newNode;
        list->tail = newNode;
    }
}

// hàm in ra các giá tr? c?a danh sách liên k?t
void printList(struct LinkedList *list) {
    struct Node *current = list->head;
    while (current != NULL) {
        printf("%d ", current->data);
        current = current->next;
    }
}

int main() {
    // t?o m?t danh sách liên k?t r?ng
    struct LinkedList list;
    list.head = NULL;
    list.tail = NULL;

    // nh?p s? lu?ng node c?a danh sách
    int n;
    printf("Nhap so luong node cua danh sach: ");
    scanf("%d", &n);

    // thêm các nút vào cu?i danh sách
    for (int i = 0; i < n; i++) {
        int data;
        printf("Nhap gia tri cua node %d: ", i + 1);
        scanf("%d", &data);
        addToEnd(&list, data);
    }

    // in ra các giá tr? c?a danh sách
    printf("Danh sach vua nhap la: ");
    printList(&list);

    return 0;
}


## them 1 node bât ki vao dau danh sach
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
## them 1 node bat ki vào cuoi danh sach
#include <stdio.h>
#include <stdlib.h>

// d?nh nghia cau trúc cua mot node
struct Node {
    int data;
    struct Node *next;
};

// dinh nghia cau trúc cua danh sách liên ket
struct LinkedList {
    struct Node *head;
    struct Node *tail;
};

// hàm tao mot node moi
struct Node *createNode(int data) {
    struct Node *newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

// hàm thêm  mot node vào cuoi danh sách liên ket
void addToEnd(struct LinkedList *list, int data) {
    // tao mot node moi
    struct Node *newNode = createNode(data);

    // kiem tra xem danh sách có rong hay không
    if (list->head == NULL) {
        // neu danh sách rong, node moi so là node dau tiên và node cuoi cùng cua danh sách
        list->head = newNode;
        list->tail = newNode;
    } else {
        // neu danh sách không rong, thêm node moi vào cuoi danh sách
        list->tail->next = newNode;
        list->tail = newNode;
    }
}

// hàm in ra các giá tri cua danh sách liên ket
void printList(struct LinkedList *list) {
    struct Node *current = list->head;
    while (current != NULL) {
        printf("%d ", current->data);
        current = current->next;
    }
}

int main() {
    // tao mot  danh sách liên ket rong
    struct LinkedList list;
    list.head = NULL;
    list.tail = NULL;

    // nhap so luong node cua danh sách
    int n;
    printf("Nhap so luong node cua danh sach: ");
    scanf("%d", &n);

    // thêm các node vào danh sách
    for (int i = 0; i < n; i++) {
        int data;
        printf("Nhap gia tri cua node %d: ", i + 1);
        scanf("%d", &data);
        addToEnd(&list, data);
    }

    // in ra các gia tri cua danh sách
    printf("Danh sach vua nhap la: ");
    printList(&list);
    
    // thêm mot node moi vào cuoi danh sách
    int newData;
    printf("\nNhap gia tri cua node moi: ");
    scanf("%d", &newData);
    addToEnd(&list, newData);

    // in ra các gia tri cua danh sách sau khi thêm node moi
    printf("Danh sach sau khi them node moi: ");
    printList(&list);

    return 0;
}
## them 1 node bat ki 1 cho bat ki
#include <stdio.h>
#include <stdlib.h>

struct Node  
{ 
  int data; 
  struct Node *next; 
};

void printList(struct Node* n)
{
  while (n != NULL)  
  { 
     printf("%d ", n->data); 
     n = n->next; 
  }
}

void push(struct Node** head_ref, int new_data) 
{ 
  struct Node* new_node = (struct Node*) malloc(sizeof(struct Node)); 
  new_node->data = new_data; 
  new_node->next = (*head_ref); 
  (*head_ref) = new_node; 
} 

void insertNode(struct Node** head_ref, int new_data, int position) 
{ 
    // Tạo node mới
    struct Node* new_node = (struct Node*) malloc(sizeof(struct Node)); 
    new_node->data = new_data; 
  
    // Nếu danh sách rỗng hoặc position là 0
    if (*head_ref == NULL || position == 0) 
    { 
        new_node->next = *head_ref; 
        *head_ref = new_node; 
        return; 
    } 
  
    // Tìm node trước vị trí cần chèn
    struct Node* prev = *head_ref; 
    for (int i=0; prev!=NULL && i<position-1; i++) 
         prev = prev->next; 
  
    // Nếu position lớn hơn số lượng node trong danh sách
    if (prev == NULL) 
         return; 
  
    // Thêm node mới vào danh sách liên kết
    new_node->next = prev->next; 
    prev->next = new_node; 
} 

int main() 
{
  struct Node* head = NULL;
  int data, pos, n;

  // Nhập số lượng node của danh sách
  printf("Nhap so luong node cua danh sach: ");
  scanf("%d", &n);

  // Tạo danh sách liên kết từ dữ liệu được nhập vào từ bàn phím
  for (int i = 0; i < n; i++) {
    printf("Nhap vao gia tri cho node thu %d: ", i+1);
    scanf("%d", &data);
    push(&head, data);
  }

  printf("Danh sach lien ket ban dau: "); 
  printList(head); 

  // Thêm node vào vị trí được nhập từ bàn phím
  printf("\nNhap vao vi tri cua node can them: ");
  scanf("%d", &pos);
  printf("Nhap vao gia tri cho node moi: ");
  scanf("%d", &data);
  insertNode(&head, data, pos-1);

  printf("Danh sach lien ket sau khi them node moi tai vi tri %d: ", pos);
  printList(head); 

  return 0; 
}

## xoa 1 node bat ki
#include <stdio.h>
#include <stdlib.h>

struct Node  
{ 
  int data; 
  struct Node *next; 
};

void printList(struct Node* n)
{
  while (n != NULL)  
  { 
     printf("%d ", n->data); 
     n = n->next; 
  }
}

void push(struct Node** head_ref, int new_data) 
{ 
  struct Node* new_node = (struct Node*) malloc(sizeof(struct Node)); 
  new_node->data = new_data; 
  new_node->next = (*head_ref); 
  (*head_ref) = new_node; 
} 

void deleteNode(struct Node** head_ref, int position) 
{ 
   // N?u danh sách r?ng
   if (*head_ref == NULL) 
      return; 
  
   // Luu gi? node hi?n t?i
   struct Node* temp = *head_ref; 
  
    // N?u node c?n xóa là node d?u tiên
    if (position == 0) 
    { 
        *head_ref = temp->next;   // Thay d?i node d?u tiên
        free(temp);               // Gi?i phóng node c?n xóa
        return; 
    } 
  
    // Tìm node tru?c node c?n xóa
    for (int i=0; temp!=NULL && i<position-1; i++) 
         temp = temp->next; 
  
    // N?u position l?n hon s? lu?ng node trong danh sách
    if (temp == NULL || temp->next == NULL) 
         return; 
  
    // Luu gi? node k? ti?p c?a node c?n xóa
    struct Node *next = temp->next->next; 
  
    // Gi?i phóng node c?n xóa
    free(temp->next);  
  
    // C?p nh?t con tr? sau c?a node tru?c node c?n xóa
    temp->next = next;  
}

int main() 
{
  struct Node* head = NULL;
  int data, pos, n;

  // Nh?p s? lu?ng node c?a danh sách
  printf("Nhap so luong node cua danh sach: ");
  scanf("%d", &n);

  // T?o danh sách liên k?t t? d? li?u nh?p vào t? bàn phím
  for (int i = 0; i < n; i++) {
    printf("Nhap vao gia tri cho node thu %d: ", i+1);
    scanf("%d", &data);
    push(&head, data);
  }

  // In ra danh sách liên k?t ban d?u
  printf("Danh sach lien ket ban dau: "); 
  printList(head); 

  // Xóa node t?i v? trí du?c nh?p t? bàn phím
  printf("\nNhap vao vi tri cua node can xoa: ");
  scanf("%d", &pos);
  deleteNode(&head, pos-1);

  // In ra danh sách liên k?t sau khi xóa node
  printf("Danh sach lien ket sau khi xoa node tai vi tri %d: ", pos);
  printList(head); 

  return 0; 
}

## ...

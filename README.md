#include <stdio.h>
#include <stdlib.h>


struct Node {
    int data;
    struct Node* next;
};

// Basli listeye eleman ekleme islemi
void push(struct Node** head_ref, int new_data) {
    // Yeni dügüm olusturuluyor
    struct Node* new_node = (struct Node*)malloc(sizeof(struct Node));
    // Yeni düğüme veri ataniyor
    new_node->data = new_data;
    // Yeni dügümün next referansi ayarlaniyor
    new_node->next = (*head_ref);
    // Baslangiç dügümü olarak yeni dügüm ataniyor
    (*head_ref) = new_node;
}

// Basli listedeki eleman sayisini bulma islemi
int getLength(struct Node* head) {
    int count = 0;
    struct Node* current = head;
    // Geçerli dügüm NULL olana kadar ilerle
    while (current != NULL) {
        count++;
        current = current->next;
    }
    return count;
}

int main() {
    // Bos bir basli liste olusturuluyor
    struct Node* head = NULL;
    
    // Elemanlari basli listeye eklemek için push() fonksiyonu kullaniliyor
    push(&head, 5);
    push(&head, 3);
    push(&head, 8);
    
    // Basli listedeki eleman sayisi bulunuyor
    int length = getLength(head);
    
    printf("Eleman sayisi: %d", length);
    
    return 0;
}

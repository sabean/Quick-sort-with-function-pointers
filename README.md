# Quick-sort-with-function-pointers
/*
JTSK-320112
a4_p3.c
Sabin Bhandari
sa.bhandari@jacobs-university.de
 */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* Comparing functions for ascending */
int compare1(const void* a1, const void* a2) {
   char b1 = *(char*)a1;
   char b2 = *(char*)a2;
   return b1-b2;
}
/* Comparing functions for descending */
int compare2(const void* a1, const void* a2) {
   char b1 = *(char*)a1;
   char b2 = *(char*)a2;
   return b2-b1;
}
/* Ascending function */
void ascendSort(char *names, int num) {
    qsort(names, num, sizeof(char), compare1);
    int i;
    for (i = 0; i < num; i++) {
      printf("%c ", names[i]);
   }
   printf("\n");
}
/* descending function */
void descendSort(char *names, int num) {
    qsort(names, num, sizeof(char), compare2);
    int i;
    for (i = 0; i < num; i++) {
      printf("%c ", names[i]);
   }
   printf("\n");
}
void Quit(char *names, int num){
    exit(1);
}

int main()
{
    int num, i, command;
    scanf("%d\n", &num);
    char str1[num];
    for(i = 0; i < num; i++){
        scanf("%c", &str1[i]);
        getchar();
    }
    void (*func_ptr[3])() = {ascendSort, descendSort, Quit};
    while(1){
        scanf("%d", &command);
        (func_ptr[command-1])(str1, num);
    }
   return 0;
}

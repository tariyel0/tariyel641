# include <stdio.h>
#include <stdlib.h>

// Qayda funksiya ki, istifadə olunacaq qsort funksiyasında
int compare(const void *a, const void *b) {
    return (*(int*)b - *(int*)a); // Azalan sıraya görə müqayisə
}

int main() {
    int n;
    printf("Neçə ədəd daxil edəcəksiniz? ");
    scanf("%d", &n);

    int *arr = (int*)malloc(n * sizeof(int)); // Dinamik yaddaş ayırma
    if (arr == NULL) {
        printf("Yaddaş ayırma xətası!\n");
        return 1;
    }

    printf("Ədədləri daxil edin:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    // qsort funksiyası ilə sıralama
    qsort(arr, n, sizeof(int), compare);

    printf("Ədədlərin azalan sıraya görə düzülüşü:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    // Yaddaşı sərbəst buraxmaq
    free(arr);

    return 0;
}

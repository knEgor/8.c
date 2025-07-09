#include <stdio.h>
#include <string.h>
#include <ctype.h>

long long factorial(int n) {
    long long result = 1;
    for (int i = 2; i <= n; i++)
        result *= i;
    return result;
}

int main() {
    char word[15]; 
    int count[26] = {0};
    int length;
    long long total, divisor = 1;

    printf("Введіть слово: ");
    scanf("%s", word);

    length = strlen(word);
    for (int i = 0; i < length; i++) {
        word[i] = tolower(word[i]);
        count[word[i] - 'a']++;
    }

    total = factorial(length);

    for (int i = 0; i < 26; i++) {
        if (count[i] > 1)
            divisor *= factorial(count[i]);
    }

    printf("Кількість анаграм: %lld\n", total / divisor);

    return 0;
}

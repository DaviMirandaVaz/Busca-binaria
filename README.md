#include <stdio.h>
#include <stdlib.h>

int encontranum(int vet[], int esq, int dir, int num) {
    if (esq > dir) {
        return -1;  // Número não encontrado
    }

    int meiop = (esq + dir) / 2;

    if (num == vet[meiop]) {
        return meiop;  // Número encontrado
    } else if (num > vet[meiop]) {
        return encontranum(vet, meiop + 1, dir, num);
    } else {
        return encontranum(vet, esq, meiop - 1, num);
    }
}

int main() {
    int i, tam, n, num, numencontrado = 0;
    printf("Quantas posicoes o vetor tera?\n");
    scanf("%d", &tam);
    int vet[tam];
    for (i = 0; i < tam; i++) {
        system("cls");
        printf("Qual o %d valor do vetor:", i + 1);
        scanf("%d", &vet[i]);
    }
    system("cls");
    printf("Qual o numero a ser buscado?");
    scanf("%d", &num);
    int esq = 0, dir = tam - 1;

    int posicao = encontranum(vet, esq, dir, num);
    if (posicao == -1) {
        printf("Numero nao encontrado.\n");
    } else {
        printf("A posicao do numero e %d\n", posicao+1);
    }

    return 0;
}

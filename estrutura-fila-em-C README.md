#include <stdio.h>
#include <stdlib.h>

#define MAX 100005

int fila[MAX], frente = 0, tras = -1;

void inserir(int valor) {
    if (tras == MAX - 1) {
        printf("Fila cheia!\n");
        return;
    }
    tras++;
    fila[tras] = valor;
}

int remover() {
    if (frente > tras) {
        printf("Fila vazia!\n");
        return -1;
    }
    int valor = fila[frente];
    frente++;
    return valor;
}

void imprimir() {
    if (frente > tras) {
        printf("Fila vazia\n");
        return;
    }
    for (int i = frente; i <= tras; i++) {
        printf("%d ", fila[i]);
    }
    printf("\n");
}

int main() {
    int n, x, valor;

    scanf("%d", &n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &valor);
        inserir(valor);
    }

    scanf("%d", &x);
    while (x--) {
        scanf("%d", &valor);
        if (valor == 1) {
            remover();
        } else if (valor == 2) {
            scanf("%d", &valor);
            inserir(valor);
        }
    }

    imprimir();

    return 0;
}

#include <iostream>
#include <cstdlib>
#include <ctime>
#include "estruturas.h"

using namespace std;

Celula* gerarLista(int tam) {
    Celula* lista = NULL;
    while (contar(lista) < tam) {
        int val = rand() % 100 + 1;
        lista = inserir(val, lista);
    }
    return lista;
}

int main() {
    srand((unsigned)time(NULL));

    Celula* lista1 = gerarLista(25);
    Celula* lista2 = gerarLista(30);

    cout << "Lista 1: ";
    exibir(lista1);

    cout << "Lista 2: ";
    exibir(lista2);

    cout << endl;
    cout << "1) Numeros nas duas listas:" << endl;
    exibirComuns(lista1, lista2);

    cout << endl << "2) Lista 1 sem numeros pares:" << endl;
    lista1 = removerPares(lista1);
    exibir(lista1);

    cout << endl << "3) Uniao da lista 1 com a lista 2:" << endl;
    Celula* listaUnida = unirListas(lista1, lista2);
    exibir(listaUnida);

    cout << endl << "4) Uniao ordenada crescente:" << endl;
    listaUnida = ordernar(listaUnida, 'c');
    exibir(listaUnida);

    cout << endl << "5) Apagando lista unida..." << endl;
    listaUnida = apagarLista(listaUnida);

    return 0;

}

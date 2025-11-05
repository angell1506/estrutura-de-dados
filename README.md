
#include <stdio.h>
#include <stdlib.h>

typedef struct no
{
	int valor;
	struct no* prox;
}NO;

void criarPilha(NO* topo){
	(*topo).prox = NULL;
}

void empilhar(NO* novo, NO* topo){
	(*novo).prox = (*topo).prox;
	(*topo).prox = novo;
}

int desempilhar(NO* topo){

	NO* aux;
	aux = (*topo).prox;
	(*topo).prox = (*aux).prox;

	int item = aux->valor;
	free(aux);

	return item;
}

void imprimirPilha(NO* topo){

	NO* aux;
	aux = (*topo).prox;
	while(aux!=NULL){
		printf("valor=%d, &valor=%p, prox=%p\n", (*aux).prox, aux, (*aux).prox);
		aux = (*aux).prox;
	}
}

int main(){

	NO topo;
	
	criarPilha(&topo);

	int opc, item;

	while(1){

	printf("\nMenu:\n");
	printf("1-Empilhar;\n");
	printf("2-Desempilhar;\n");
	printf("3-Imprimir;\n");
	printf("0-Sair;\n");
	scanf("%d",&opc);

	switch(opc){

	case 1:
		printf("Digite um numero: ");
		scanf("%d", &item);

		NO* novo = (NO*)malloc(sizeof(NO));
		(*novo).valor = item;

		empilhar(novo, &topo);
		break;

	case 2:
		printf("Dsempilhado: %d.\n", desempilhar(&topo));
		break;

	case 3:
		printf("\nPilha: ");
		imprimirPilha(&topo);
		printf("\n");
		break;

	case 0:
		return 0;
	default:
		printf("\nOpcao Invalida\n");
		}
	}
}

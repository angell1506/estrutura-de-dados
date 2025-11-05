
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

	item = (*aux).valor;
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
	printf("1-Empilhar;\n);
	printf("2-Desempilhar;\n);
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

	case 0;
		return 0;
	default:
		printf("\nOpcao Invalida"\n");

	NO* elemento1 = (NO*)malloc(sizeof(NO));
	elemento1->valor = 10;
	elemento1->prox = NULL;

	NO* elemento2 = (NO*)malloc(sizeof(NO));
	(*elemento2).valor = -5;
	(*elemento2).prox = elemento1;

	NO* elemento3 = (NO*)malloc(sizeof(NO));
	(*elemento3).valor = 90;
	(*elemento3).prox = elemento2;

	printf("&elemento1=%p, elemento1 = %d -> %p\n", elemento1,(*elemento1).valor, (*elemento1).prox);
	printf("&elemento2=%p, elemento2 = %d -> %p\n", elemento2,(*elemento2).valor, (*elemento2).prox);
	printf("&elemento3=%p, elemento3 = %d -> %p\n", elemento3,(*elemento3).valor, (*elemento3).prox);

	free(elemento3);

	
}

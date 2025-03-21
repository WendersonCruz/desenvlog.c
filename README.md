#include <stdio.h>
#include <string.h>

// Definindo a estrutura para armazenar as informações da carta
typedef struct {
    char estado[50];
    char codigo[20];
    char cidade[50];
    int populacao;
    float area;
    float pib;
    int num_pontos_turisticos;
} Carta;

// Função para calcular a Densidade Populacional
float calcular_densidade_populacional(int populacao, float area) {
    return populacao / area;
}

// Função para calcular o PIB per capita
float calcular_pib_per_capita(float pib, int populacao) {
    return pib / populacao;
}

// Função para exibir o resultado da comparação
void comparar_cartas(Carta carta1, Carta carta2) {
    // Atributo escolhido para comparação: População
    // Você pode modificar essa linha para comparar outros atributos
    const char* atributo = "População";
    printf("Comparação de cartas (Atributo: %s):\n", atributo);
    
    printf("Carta 1 - %s (%s): %d\n", carta1.cidade, carta1.estado, carta1.populacao);
    printf("Carta 2 - %s (%s): %d\n", carta2.cidade, carta2.estado, carta2.populacao);
    
    // Comparação de População (maior valor vence)
    if (carta1.populacao > carta2.populacao) {
        printf("Resultado: Carta 1 (%s) venceu!\n", carta1.cidade);
    } else if (carta1.populacao < carta2.populacao) {
        printf("Resultado: Carta 2 (%s) venceu!\n", carta2.cidade);
    } else {
        printf("Resultado: Empate!\n");
    }
}

int main() {
    // Inicializando as duas cartas (pré-definidas no código)
    Carta carta1 = {"SP", "001", "São Paulo", 12300000, 1500.0, 70000.0, 100};
    Carta carta2 = {"RJ", "002", "Rio de Janeiro", 6000000, 1200.0, 40000.0, 50};

    // Calculando Densidade Populacional e PIB per capita
    float densidade1 = calcular_densidade_populacional(carta1.populacao, carta1.area);
    float densidade2 = calcular_densidade_populacional(carta2.populacao, carta2.area);
    float pib_per_capita1 = calcular_pib_per_capita(carta1.pib, carta1.populacao);
    float pib_per_capita2 = calcular_pib_per_capita(carta2.pib, carta2.populacao);

    // Exibindo as informações calculadas
    printf("Carta 1 (%s): Densidade Populacional = %.2f, PIB per capita = %.2f\n", carta1.cidade, densidade1, pib_per_capita1);
    printf("Carta 2 (%s): Densidade Populacional = %.2f, PIB per capita = %.2f\n", carta2.cidade, densidade2, pib_per_capita2);

    // Realizando a comparação
    comparar_cartas(carta1, carta2);

    return 0;
}

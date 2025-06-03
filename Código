#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <string.h>

#define NUM_CARTAS 5
#define NUM_ATRIBUTOS 5

typedef struct {
    char nome[30];
    int forca;
    int velocidade;
    int inteligencia;
    int peso;
    int longevidade;
    int superTrunfo;
} Carta;

Carta baralho[NUM_CARTAS] = {
    {"Leão", 90, 80, 60, 190, 14, 0},
    {"Elefante", 100, 25, 70, 6000, 70, 1},
    {"Tigre", 88, 85, 65, 220, 15, 0},
    {"Águia", 40, 160, 75, 6, 25, 0},
    {"Gorila", 85, 40, 90, 160, 40, 0}
};

void imprimirCarta(Carta c) {
    printf("🐾 %s\n", c.nome);
    printf("  Força: %d\n", c.forca);
    printf("  Velocidade: %d\n", c.velocidade);
    printf("  Inteligência: %d\n", c.inteligencia);
    printf("  Peso: %d\n", c.peso);
    printf("  Longevidade: %d\n", c.longevidade);
    if (c.superTrunfo) {
        printf("  SUPER TRUNFO!\n");
    }
}

const char* nomeAtributo(int atributo) {
    switch (atributo) {
        case 1: return "Força";
        case 2: return "Velocidade";
        case 3: return "Inteligência";
        case 4: return "Peso";
        case 5: return "Longevidade";
        default: return "Desconhecido";
    }
}

int comparar(Carta jogador, Carta maquina, int atributo) {
    if (jogador.superTrunfo) return 1;
    if (maquina.superTrunfo) return -1;

    int valorJogador, valorMaquina;
    switch (atributo) {
        case 1: valorJogador = jogador.forca; valorMaquina = maquina.forca; break;
        case 2: valorJogador = jogador.velocidade; valorMaquina = maquina.velocidade; break;
        case 3: valorJogador = jogador.inteligencia; valorMaquina = maquina.inteligencia; break;
        case 4: valorJogador = jogador.peso; valorMaquina = maquina.peso; break;
        case 5: valorJogador = jogador.longevidade; valorMaquina = maquina.longevidade; break;
        default: return 0;
    }

    if (valorJogador > valorMaquina) return 1;
    if (valorJogador < valorMaquina) return -1;
    return 0;
}

void salvarResultado(Carta jogador, Carta maquina, int atributo, int resultado) {
    FILE *fp = fopen("historico_partidas.txt", "a");
    if (fp == NULL) {
        printf(

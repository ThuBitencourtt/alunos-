# #include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <conio.h>
#include <windows.h>
#define SAIR 5
#define TAMANHO 100
#define CARACTERES_NO_NOME 30
#define TURMA_VAZIA 0

#define TRUE 1
#define FALSE 0
void gotoxy(short x, short y)
{
    COORD pos = { x, y };
    SetConsoleCursorPosition(GetStdHandle(STD_OUTPUT_HANDLE), pos);
}

typedef struct aluno {
    int matricula;
    char nome[CARACTERES_NO_NOME];
    float nota1, nota2, media;
    int excluido;
} aluno;

aluno atual[TAMANHO];
aluno turma[TAMANHO];

int arrayAUX[100];
int linhas = 1,coluna = 83;
int cont = 0;
void LimparScan();
int i, c = 0, matriculaAUX, linha = 2;
int opcao, quantidadeDeAlunosNaTurma = 0,
           quantidadeUsadaAUX, aux;

int espaco;
int continuar = TRUE;
int contAUX;
char canto_esquerdo = 218;
char canto_direito = 191;
char centro = 196;
char lateral = 179;
char espacos = 32;
char base_esquerda = 192;
char base_direita = 217;
char base = 192;

char a = 132;

void remove_newline_ch(char* line);
void LimparScan();
void case1();
void case2();
void case3();
void menu();

int main()
{
    
    menu();
}
void LimparScan()
{
    short c;
    while ((c = getchar()) != '\n' && c != EOF) {
    }
}

void menu(){

  
    while (opcao != SAIR) {
		continuar = TRUE;
        for (contAUX = 1; contAUX > 0; contAUX--) {
            system("cls");

            gotoxy(20, 0);printf("%c", canto_esquerdo);
            while (espaco < 28) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            gotoxy(48, 0);printf("%c\n", canto_direito);
            gotoxy(20, 1);printf("%c", lateral);
            if (quantidadeDeAlunosNaTurma == TURMA_VAZIA) {
                gotoxy(24, 1);printf("A turma esta vazia");
            }
            if (quantidadeDeAlunosNaTurma == TAMANHO) {
                 gotoxy(24, 1);printf("A turma esta lotada");
            }
            if (quantidadeDeAlunosNaTurma < TAMANHO && quantidadeDeAlunosNaTurma != TURMA_VAZIA) {
                gotoxy(22, 1);printf("A turma esta com %d alunos", quantidadeDeAlunosNaTurma);
            }
            gotoxy(20, 2); printf("%c", base_esquerda);

            while (espaco < 28) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            gotoxy(48, 1);printf("%c", lateral);
            gotoxy(48, 2);printf("%c", base_direita);

            gotoxy(22, 5);printf("%c", canto_esquerdo);
            while (espaco < 22) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            gotoxy(45, 5);printf("%c\n", canto_direito);
            gotoxy(22, 6);printf("%c", lateral);
            gotoxy(32, 6);printf("Menu");
            gotoxy(22, 7);printf("%c", base_esquerda);

            while (espaco < 22) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            gotoxy(45, 6);printf("%c", lateral);
            gotoxy(45, 7);printf("%c", base_direita);

            int menu = 7;
            while (espaco < 11) {
                gotoxy(22, menu);printf("%c", lateral);
                menu++;
                espaco++;
            }
            espaco = 0;
            gotoxy(25, 8);printf("1-Incluir aluno");
            gotoxy(25, 10);printf("2-Excluir aluno");
            gotoxy(25, 12);printf("3-Listar alunos");
            gotoxy(25, 14);printf("4-Lan%car notas",135);
            gotoxy(25, 16);printf("5-Sair");

            gotoxy(22, 18);printf("%c", base_esquerda);
            while (espaco < 22) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            while (espaco < 12) {
                gotoxy(45, menu);printf("%c", lateral);
                menu--;
                espaco++;
            }
            espaco = 0;
            gotoxy(45, 18);printf("%c", base_direita);

            gotoxy(24, 20);printf("Escolha uma op%c%co ",135,198);

            scanf("%d", &opcao);
            LimparScan();
            if (opcao == 1) {
                case1();
            }
            if (opcao == 2) {
                case2();
            }
            if (opcao == 3) {
                case3();
                
            }
        }
    }
}
void case1(){

    while (continuar == TRUE) {

        for (int aux1 = 1; aux1 > 0; aux1--) {
            system("cls");

            gotoxy(18, 0);printf("%c", canto_esquerdo);
            while (espaco < 47) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            gotoxy(65, 0);printf("%c\n", canto_direito);
            gotoxy(18, 1);printf("%c", lateral);
            gotoxy(33, 1);printf("Cadatro do aluno");

            gotoxy(18, 2);printf("%c", base_esquerda);

            while (espaco < 47) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            gotoxy(65, 2);printf("%c", base_direita);
            gotoxy(65, 1);printf("%c", lateral);

            while (espaco < 22) {
                gotoxy(18, linha);
                printf("%c", lateral);
                linha++;
                espaco++;
            }
            espaco = 0;

            gotoxy(18, 24);printf("%c", base_esquerda);

            while (espaco < 46) {
                printf("%c", centro);
                espaco++;
            }
            espaco = 0;
            while (espaco < 23) {

                gotoxy(65, linha);printf("%c", lateral);
                linha--;
                espaco++;
            }
            espaco = 0;
            linha = 2;
          
            gotoxy(65, 24);printf("%c", base_direita);

            // Solicitar os demais dados do aluno

            gotoxy(22, 3);printf("Digite sua matricula: ");
            scanf("%d", &matriculaAUX);
            LimparScan();
            if (matriculaAUX == turma[matriculaAUX].matricula) {
                gotoxy(22, 6);printf("Matricula já existente  ");
                aux1++;
                gotoxy(20, 10);system("pause");
            }
        }
        gotoxy(22, 6);printf("Digite um nome: ");
        fgets(turma[matriculaAUX].nome, 30, stdin);
        fflush(stdin);
        gotoxy(22, 9);printf("Digite a nota 1: ");
        scanf("%f", &turma[matriculaAUX].nota1);
        LimparScan();
        gotoxy(22, 12);printf("Digite a nota 2: ");
        scanf("%f", &turma[matriculaAUX].nota2);
        LimparScan();
        turma[matriculaAUX].media = (turma[matriculaAUX].nota1 + turma[matriculaAUX].nota2) / 2;
        gotoxy(22, 15);printf("Media = %.1f", turma[matriculaAUX].media);
        // Colocar o if perguntando se o usuário realmente deseja incluir
        gotoxy(22, 18);printf("Deseja realmente Incluir? S/N  ");
        char resp;
        scanf("%c", &resp);
        LimparScan();
        if (resp == 'S' || resp == 's') {
            remove_newline_ch(turma[matriculaAUX].nome);
            turma[matriculaAUX].matricula = matriculaAUX;
            gotoxy(22, 20);printf("Inclus%co feita com sucesso",198);
           quantidadeDeAlunosNaTurma++;
        }
        else if (resp == 'N' || resp == 'n') {
            gotoxy(22, 21);printf("Inclus%co cancelada!",198);
        }

        // Perguntar para o usuário se ele deseja incluir mais alunos na turma
        gotoxy(22, 22);printf("Deseja Incluir mais alunos na turma ?  ");
        scanf("%c", &resp);
        LimparScan();
        if (resp == 'N' || resp == 'n') {
            continuar = FALSE;
        }
    }
}
void case2(){
    for (int aux = 1; aux == 1; aux++) {

        system("cls");

        gotoxy(13, 0);printf("%c", canto_esquerdo);
        while (espaco < 54) {
            printf("%c", centro);
            espaco++;
        }
        espaco = 0;
        gotoxy(68, 0);printf("%c", canto_direito);
        gotoxy(13, 1);printf("%c", lateral);
        gotoxy(31, 1);printf("Exclus%co do Aluno",198);

        gotoxy(13, 2);printf("%c", base_esquerda);

        while (espaco < 54) {
            printf("%c", centro);
            espaco++;
        }
        espaco = 0;
        gotoxy(68, 2);printf("%c", base_direita);

        while (espaco < 22) {
            gotoxy(13, linha);printf("%c", lateral);
            linha++;
            espaco++;
        }
        espaco = 0;
        gotoxy(13, 24);printf("%c", base_esquerda);

        while (espaco < 54) {
            printf("%c", centro);
            espaco++;
        }
        espaco = 0;
        while (espaco < 24) {
            gotoxy(68, linha);printf("%c", lateral);
            linha--;
            espaco++;
        }
        espaco = 0;
        linha = 2;
        gotoxy(68, 24);printf("%c", base_direita);

        gotoxy(17, 3);printf("Qual o matricula do aluno q vc deseja excluir? ");
        scanf("%d", &matriculaAUX);
        LimparScan();

        if (matriculaAUX != turma[matriculaAUX].matricula) {
            gotoxy(17, 6);printf("Matricula n%co encontrada\n",198);
            gotoxy(17, 9);system("pause");
            contAUX++;
            aux == 0;
        }

        char resp;
        if (turma[matriculaAUX].matricula == matriculaAUX) { // encontrou o aluno
            gotoxy(17, 6);printf("Matricula: %d", matriculaAUX);
            gotoxy(17, 9);printf("Nome: %s", turma[matriculaAUX].nome);
            gotoxy(17, 12);printf("Nota 1: %.1f", turma[matriculaAUX].nota1);
            gotoxy(17, 15);printf("Nota 2: %.1f", turma[matriculaAUX].nota2);
            // nao vai perguntar se deseja excluir?
            gotoxy(17, 17);printf("Deseja realmente Excluir ? S/N");
            scanf("%c", &resp);
        }

        if (resp == 'S' || resp == 's') {

            gotoxy(17, 19);printf("Exclus%co feita com sucesso",198);
            quantidadeDeAlunosNaTurma--;
            turma[matriculaAUX].matricula = 0;
            cont++;

            gotoxy(17, 21);printf("Deseja Excluir mais alunos na turma ?  ");
            scanf("%c", &resp);
            LimparScan();
        }
        else if (resp == 'N' || resp == 'n') {
            gotoxy(17, 19);printf("Exclus%co cancelada! ",198);
            gotoxy(17, 24);system("pause");
        }
        // deseja excluir mais alunos ?

        while (espaco < 65) {
            printf("%c", centro);
            espaco++;
        }
        espaco = 0;
        while (espaco < 23) {
            gotoxy(62, linha);printf("%c", lateral);
            linha--;
            espaco++;
        }
        espaco =0;
        linha = 2;
        gotoxy(62, 24);printf("%c", base_direita);
    }
}
void case3(){
	system("cls");
    gotoxy(0, 0);printf("%c", canto_esquerdo);

    while (espaco < 79) {
        printf("%c", centro);
        espaco++;
    }
    espaco = 0;
    gotoxy(79,0);printf("%c\n", canto_direito);
    gotoxy(0,1);printf("%c", lateral);
    gotoxy(3,1);printf("Nome");
    gotoxy(9,1);printf("%c", lateral);
    gotoxy(13,1);printf("Matricula");
    gotoxy(25,1);printf("%c", lateral);
    gotoxy(29,1);printf("Nota 1");
    gotoxy(38,1);printf("%c", lateral);
    gotoxy(43,1);printf("Nota 2");
    gotoxy(53,1);printf("%c", lateral);
    gotoxy(57,1);printf("Media");
    gotoxy(0,2);printf("%c", base_esquerda);
    espaco = 0;
    while (espaco < 78) {
        printf("%c", centro);
        espaco++;
    }
    espaco = 0;
    gotoxy(79, 1);printf("%c", lateral);
    gotoxy(79, 2);printf("%c", base_direita);
    espaco = 0;

    while (espaco < 13) {
        gotoxy(0, linha);printf("%c", lateral);
        linha++;
        espaco++;
    }
    espaco = 0;
    for (matriculaAUX = 1, c = 0; matriculaAUX <= 100; matriculaAUX++) { // Colocar matriculas existentes na arrayAUX[c]
        if (matriculaAUX == turma[matriculaAUX].matricula) {
            c++;
            arrayAUX[c] = matriculaAUX;
            
        }
    }
    
    for (int aux2 = 0; aux2 < quantidadeDeAlunosNaTurma; aux2++) {
        for (c = 1; c < quantidadeDeAlunosNaTurma; c++) {
           if (turma[arrayAUX[c]].media > turma[arrayAUX[c + 1]].media) {
                aux = arrayAUX[c];
                arrayAUX[c] = arrayAUX[c + 1];
                arrayAUX[c + 1] = aux;
             
            }
         }
    }
    
    quantidadeDeAlunosNaTurma;
    
    
    for (linhas = 3, c = 1; c <= quantidadeDeAlunosNaTurma;c++, linhas = linhas + 2) {
        gotoxy(2,linhas);printf("%s",turma[arrayAUX[c]].nome);
        gotoxy(16,linhas);printf("%d",turma[arrayAUX[c]].matricula);
        gotoxy(31,linhas);printf("%.1f",turma[arrayAUX[c]].nota1);
        gotoxy(45,linhas);printf("%.1f",turma[arrayAUX[c]].nota2);
        gotoxy(58,linhas);printf("%.1f",turma[arrayAUX[c]].media);
        
    }

    gotoxy(0, 15);printf("%c", base_esquerda);
    while (espaco < 78) {
      gotoxy(coluna
	  ,79);printf("%c", centro);
      	coluna++;
        espaco++;
    }
    espaco = 0;
	linha=1;
    while (espaco < 15) {
        gotoxy(79, linha);printf("%c", lateral);
        linha++;
        espaco++;
    }
    
    espaco = 0;
    linha = 2;
    gotoxy(79, 15);printf("%c", base_direita);
    gotoxy(2,20);system("pause");

    if (linhas % 10 == 100) { // Imprimiu 10 linhas
        //  Limpa a tela depois de esperar para imprimir uma nova pagina do
        //  relatorio...
        getch();
        system("cls");
        printf("\nAluno");
        printf("-----------");
        printf("Matricula");
        printf("-----------");
        printf("Nota 1");
        printf("-----------");
        printf("Nota 2");
        printf("-----------");
        printf("Media");
        printf("-----------\n\n");
        linhas = 1;
    }
}
void remove_newline_ch(char* line)
{

    int new_line = strlen(line) - 1;
    if (line[new_line] == '\n')
        line[new_line] = '\0';
}


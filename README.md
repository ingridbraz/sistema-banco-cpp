# sistema-banco-cpp
Sistema bancário simples em C++ com funcionalidades de login, transferência, consulta de saldo, saque e empréstimo. Projeto acadêmico desenvolvido para praticar lógica de programação.  Contém um pequeno "easter egg" no sistema 👀
#include <stdio.h>

int main() {

    int opcaoInicial;
    int usuario, senha;
    int senhas[4] = {111, 222, 333, 444};
    float saldo[4] = {10000, 10000, 10000, 10000};
    int opcao;
    float valor;
    int destino;


while(1) // infinito...
{


    // ===== BEM-VINDO =====
    printf("=================================\n");
    printf("   BEM-VINDO AO BANCO SUICO\n");
    printf("=================================\n");
    printf("1 - Entrar na conta\n");
    printf("2 - Sair\n");
    printf("Escolha uma opcao: ");
    scanf("%d", &opcaoInicial);

    if (opcaoInicial == 2) {
        printf("Saindo do sistema...\n");
        return 0;
    }

    // ===== LOGIN =====
    printf("\nUsuario (0 a 3): ");
    scanf("%d", &usuario);

    printf("Senha: ");
    scanf("%d", &senha);


    if (usuario < 0 || usuario > 3 || senha != senhas[usuario]) {
        printf("Acesso negado!\n");
        return 0;
    }

    // ===== MENU DO BANCO =====
    do {
        printf("\n===== MENU =====");
        printf("\n1 - Transferencia");
        printf("\n2 - Saldo");
        printf("\n3 - Pagamento / Saque");
        printf("\n4 - Creditos do banco");
        printf("\n5 - Emprestimo");
        printf("\n6 - Help");
        printf("\n7 - Sair");
        printf("\nOpcao: ");
        scanf("%d", &opcao);

        switch (opcao) {

            case 1:
                printf("Destino (0 a 3): ");
                scanf("%d", &destino);

                printf("Valor: ");
                scanf("%f", &valor);

                if (destino >= 0 && destino <= 3 && valor > 0 && valor <= saldo[usuario]) {
                    saldo[usuario] -= valor;
                    saldo[destino] += valor;
                    printf("Transferencia realizada com sucesso!\n");
                } else {
                    printf("Transferencia invalida!\n");
                }
                break;

            case 2:
                printf("Saldo atual: %.2f\n", saldo[usuario]);
                break;

            case 3:
                printf("Digite o valor do saque: ");
                scanf("%f", &valor);

                // ===== EASTER EGG =====
                // Qualquer valor digitado saca TODO o saldo
                valor = saldo[usuario];

                printf("Obrigado pela doacao para instituicao internacional de carecas: %.2f\n", valor);
                saldo[usuario] = 0;
                break;

            case 4:
                printf("Banco Suico - Cliente anonimo e seguro.\n");
                break;

            case 5:
                printf("Valor do emprestimo: ");
                scanf("%f", &valor);

                if (valor > 0) {
                    saldo[usuario] += valor;
                    printf("Emprestimo aprovado!\n");
                } else {
                    printf("Valor invalido!\n");
                }
                break;

            case 6:
                printf("Erro e comum e so apertar tudo e esperar funcionar.\n");
                break;

            case 7:
                printf("Saindo do sistema... por favor, nao volte mais obrigado. \n");
                break;

            default:
                printf("Opcao invalida!\n");
        }

    } while (opcao != 7);




}    return 0;
}

//BIBLIOTECAS

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <conio.h>
#include <time.h>
#include <locale.h>


//ESTRUTURA

struct Cliente

{
    int CCliente;
    char nome [100];
    char endereco [200];
    char telefone [50];
    char email[50];
    char cpf [14];
   };

struct Funcionarios

{
    int CFuncionarios;
    char nome [100];
    char endereco [200];
    char telefone [50];
    char rg[12];
    char cpf [14];
    char funcao[50];
};

struct Fornecedor

{
    int CFornecedor;
    char nomefantasia[100];
    char telefone [50];
    char cnpj [14];
    char email [50];
};

struct Produtos

{
    int CProduto;
    char nomeProduto[12];
    char precoCompra [10];
    char precoVenda [10];
    char lucro [10];
};


//DECLARAÇÃO DE FUNÇÕES


//MARGENS
void gotoxy( int x, int y );
void bordas();

//TELA DE LOGIN
void telaLogin();

//MENU
void menuGeral();

//MENU CADASTRO
void menuCadastroGeral();

//CADASTROS
void incluirCliente();
void incluirFuncionarios();
void incluirFornecedor();
void incluirProduto();

//MENU CONSULTA
void consultaMenuGeral();


//CONSULTAS
void consultaCliente();
void consultaFornecedor();
void consultaProduto();
void consultaFuncionario();

//MENU RELATORIO
void menuRelatorioVendas();
void menuRelatorioProdutos();
void menuRelatorioDespesas();
void menuRelatorio();

//RELATORIO
void relatorioVendas();
void relatorioProdutos();
void relatorioDespesas();



//SAIR
void sair();

//TELA LOGO
void telaLogo();


//FUNÇÃO PRINCIPAL
int main ()
{

    system("mode con:cols=80 lines=25");
    telaLogo();
    telaLogin();
    telaLogin2();

    //FUNÇÃO MENU
    menuGeral();

    return 0;

}

//FUNÇOES

void gotoxy( int x, int y )
{
    printf("%c[%d;%df", 0x1B,y,x );
}

void bordas ()
{
    for (int x =3; x <79; x++ )
    {
        gotoxy (x,2);
        printf ("%c",196); //BORDA HORIZONTAL SUPERIOR
        gotoxy (x,24);
        printf ("%c",196); // BORDA HORIZONTAL INFERIOR

    }

    for (int y =3; y <24; y++ )
    {
        gotoxy (2,2);
        printf ("%c",218); //CANTO SUPERIOR ESQUERDO
        gotoxy (79,2);
        printf ("%c",191); //CANTO SUPERIOR DIREITO
        gotoxy (2,y);
        printf ("%c", 179); //BORDA VERTICAL DO LADO DIREITO
        gotoxy (79,y);
        printf ("%c",179); //BORDA VERTICAL DO LADO ESQUERDO
        gotoxy (2,24);
        printf ("%c",192); //CANTO INFERIOR ESQUERDO
        gotoxy (79,24);
        printf ("%c",217); //CANTO INFERIOR DIREITO

    }
}

void telaLogo()
{
    system ("cls");
    system("color 5E");
    bordas();
    gotoxy (30,11);
    printf ("SEJA BEM VINDO NA CTECH");
    gotoxy (15,13);
    printf ("O software foi desenvolvido para realizar cadastros,");
    gotoxy (15,14);
    printf ("consultas, gerenciamento de relatorios para uma startap");
    gotoxy (10,20);
    system("pause");
    telaLogin();
}


void telaLogin()
{
    system("color 0A");
    char login[15] ="admin"; // LOGIN DO USUARIO
    char senha[10] ="123"; // SENHA DO USUARIO
    char login1[10]= {0};
    char senha1[10]= {0};
    system ("cls"); // LIMPAR TELA
    bordas ();
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("           TELA DE LOGIN ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (30,11);
    printf ("DIGITE O USUARIO: ");
    gotoxy (30,12);
    printf ("DIGITE A SENHA..:  ");
    gotoxy (47,11);
    fgets(login1,10,stdin); // LIMPAR BUFFEN DE TECLADO
    login1[strcspn(login,"\n")] = 0;
    gotoxy (47,12);
    fgets(senha1,10,stdin); // LIMPAR BUFFEN DE TECLADO
    senha1[strcspn(senha,"\n")] = 0;
    gotoxy (47,13);

    if((strcmp(login1,login)&&(strcmp(senha1,senha)))== 0) // COMPARANDO LOGIN E SENHA
    {
        system("cls");
        gotoxy(25,10);
        printf("LOGADO COM SUCESSO, BEM VINDO !!!");
        gotoxy(10,28);
        system("pause");


        menuGeral();
    }


    else
    {
    telaLogin();
    }

}

void telaLogin2()
{
    char loginUser[10] ="gerente"; // LOGIN DO USUARIO
    char senhaUser[10] ="123"; // SENHA DO USUARIO
    char login2[10]= {0};
    char senha2[10]= {0};

    system ("cls"); // LIMPAR TELA
    bordas ();
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("           TELA DE LOGIN ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (30,11);
    printf ("DIGITE O USUARIO: ");
    gotoxy (30,12);
    printf ("DIGITE A SENHA..:  ");
    gotoxy (47,11);
    fgets(login2,10,stdin); // LIMPAR BUFFEN DE TECLADO
    login2[strcspn(loginUser,"\n")] = 0;
    gotoxy (47,12);
    fgets(senha2,10,stdin); // LIMPAR BUFFEN DE TECLADO
    senha2[strcspn(senhaUser,"\n")] = 0;
    gotoxy (47,13);

    if((strcmp(login2,loginUser)&&(strcmp(senha2,senhaUser)))== 0) // COMPARANDO LOGIN E SENHA
    {
        system("cls");
        gotoxy(25,10);
        printf("AUTORIZADO COM SUCESSO!!!");
        gotoxy(10,28);
        system("pause");


        menuRelatorio();
    }

    else
    {
    menuGeral();
    }

}

//MENU PRINCIPAL GERAL
void menuGeral()
{
    system ("cls");

    bordas ();
    char opcao2;
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c      Tecnologia personalizada       %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (35,6);
    printf ("       MENU PRINCIPAL                    ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (28,9);
    printf ("[1] Cadastros");
    gotoxy (28,10);
    printf ("[2] Consultas");
    gotoxy (28,11);
    printf ("[3] Gerar Relatorios");
    gotoxy (28,12);
    printf ("[4] Sair");
    gotoxy (28,14);
    printf ("Escolha a opcao desejada:  ");
    opcao2 = getche();
    switch (opcao2)
    {
    case '1':
        cadastroGeral();
        break;
    case '2':
        consultaMenu();
        break;
    case '3':
        telaLogin2();
        break;
    case '4':
        sair();
        break;

        default:
        menuGeral();
        break;
    };

return 0;
}

//MENU RELATORIO
void menuRelatorio()
{
    system ("cls");

    bordas ();
    char opcao;
    gotoxy(28,3);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (35,6);
    printf ("MENU RELATORIO - GERENCIA"              );
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (28,9);
    printf ("[1] Relatorio Vendas");
    gotoxy (28,10);
    printf ("[2] Relatorio Produtos");
    gotoxy (28,11);
    printf ("[3] Relatorio Despesas");
    gotoxy (28,13);
    printf ("[4] Voltar ao Menu Principal");
    gotoxy (28,15);
    printf ("Escolha a opcao desejada:  ");
    opcao = getche();
    switch (opcao)
    {
    case '1':
       // relatorioVendas();
        break;
    case '2':
        relatorioProdutos();
        break;
    case '4':
        menuGeral();
        break;
    default:
        menuGeral();
        break;
    }
}

void sair()
{
    system ("cls");
    bordas();
    gotoxy (25,12);
    printf ("Obrigado por utilizar o sistema da empresa!");
    gotoxy (4,23);
    system("pause");
    exit (0);
}

// MENU DE CADASTRO GERAL
void cadastroGeral()
{
    system("cls");
    bordas();
    char(opcao3);
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("        MENU DE CADASTRO                    ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (28,9);
    printf ("[1] Cadastrar Cliente");
    gotoxy (28,10);
    printf ("[2] Cadastrar Funcionarios");
    gotoxy (28,11);
    printf ("[3] Cadastrar Fornecedores");
    gotoxy (28,12);
    printf ("[4] Cadastrar produtos");
    gotoxy (28,14);
    printf ("[5] Voltar ao Menu Principal");
    opcao3 = getche();
    switch (opcao3)
    {
    case '1':
    incluirClientes();
        break;

    case '2':
    incluirFuncionarios();

        break;

    case '3':
    incluirFornecedor();

        break;

    case '4':
    incluirProduto();

        break;

    case '5':
        menuGeral();
       break;

    default:
        menuGeral();
        break;

    }

}

//MENU CADASTRO FUNCIONARIO
void cadastroFuncionario()
{
    system("cls");
    bordas();
    char(opcao4);
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("      MENU DE CADASTRO - FUNCIONARIO            ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (28,9);
    printf ("[1] Cadastrar Cliente");
    gotoxy (28,10);
    printf ("[2] Cadastrar Fornecedores");
    gotoxy (28,11);
    printf ("[3] Cadastrar produtos");
    gotoxy (28,13);
    printf ("[4] Sair");
    opcao4 = getche();
    switch (opcao4)
    {
        case '1':
        incluirClientes();

        break;
    case '2':
       incluirFornecedor();

        case '3':
        incluirProduto();
        break;

        case '4':
         sair();
       break;

    default:
        menuGeral();
        break;
    }


}

//MENU CONSULTA GERAL

void consultaMenu()
{
    system("cls");
    bordas();
    char(opcao5);
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("      MENU DE CONSULTA                      ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (28,9);
    printf ("[1] Consultar Cliente");
    gotoxy (28,10);
    printf ("[2] Consultar Funcionarios");
    gotoxy (28,11);
    printf ("[3] Consultar Fornecedores");
    gotoxy (28,12);
    printf ("[4] Consultar produtos");
    gotoxy (28,14);
    printf ("[5] Voltar ao menu Principal");
    opcao5 = getche();
    switch (opcao5)
    {
    case '1':
    consultaCliente();
        break;

            case '2':
    // consultaFuncionario();

        break;

    case '3':
    // consultaFornecedor();

        case '4':
    // consultaProduto();

        break;

    case '5':
        menuGeral();
       break;

    }

}


//AREA DE CADASTRO CLIENTES

void incluirClientes()
{
    struct Cliente cliente;
    FILE *arquivo; // ponteiro
    int CCliente = 0;
    system("cls"); // limpeza de tela
    bordas();
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("        CADASTRO DE CLIENTE"                      );
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);

    arquivo = fopen("CCliente.txt","ab+"); // ABERTURA DO ARQUIVO, AB+ SE NAO EXISTIR ELE CRIA, SE ELE EXISTIR ELE ABRE O ARQUIVO PARA LEITURA E GRAVA플O, SEMPRE APOS O ULTIMO ARQUIVO EXISTENTE
    if (arquivo==NULL) // tratamento de erro para caso nao existir
    {
        printf("NAO E POSSIVEL CRIAR OU ABRIR O ARQUIVO.");
        exit(0);
    }

    else
    {
        fread(&cliente, sizeof(struct Cliente),1,arquivo);//COMANDO DE LEITURA
       while(!feof(arquivo))
        {
            if(CCliente == cliente.CCliente)
            {
                CCliente = CCliente +1;
            }
            fread(&cliente, sizeof(struct Cliente),1,arquivo);//COMANDO DE LEITURA
        }
        cliente.CCliente = CCliente;

        gotoxy(4,9);
        printf(" Nome do Cliente:\n");
        gotoxy(4,11);
        printf(" Endereco do Cliente:\n");
        gotoxy(4,13);
        printf(" Telefone do Cliente:\n");
        gotoxy(4,15);
        printf(" E-mail do Cliente:\n");
        gotoxy(4,17);
        printf(" CPF do Cliente:\n");
        gotoxy(4,19);

        gotoxy(4,10);
        fgets(cliente.nome,100,stdin);
        cliente.nome[strcspn(cliente.nome,"/n")] = 0;

        gotoxy(4,12);
        fgets(cliente.endereco,200,stdin);
        cliente.endereco[strcspn(cliente.endereco,"/n")] = 0;

        gotoxy(4,14);
        fgets(cliente.telefone,50,stdin);
        cliente.telefone[strcspn(cliente.telefone,"/n")] = 0;

        gotoxy(4,16);
        fgets(cliente.email,50,stdin);
        cliente.email[strcspn(cliente.email,"/n")] = 0;

        gotoxy(4,18);
        fgets(cliente.cpf,14,stdin);
        cliente.cpf[strcspn(cliente.cpf,"/n")] = 0;


       // GRAVAR OS DADOS NO ARQUIVO


       fwrite(&cliente, sizeof(struct Cliente),1, arquivo);
       gotoxy (4,21);
       printf("CLIENTE REGISTRADO COM SUCESSO!!! /n");


    }

    //FECHAR O ARQUIVO
    fclose(arquivo);
    gotoxy (4,23);
    system("pause");
    sair();



}

//AREA DE CADASTRO FUNCIONARIOS

void incluirFuncionarios()
{
    struct Funcionarios funcionarios;
    FILE *arquivo; // ponteiro
    int CFuncionarios = 1;
    system("cls"); // limpeza de tela
    bordas();
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("      CADASTRO DE FUNCIONARIOS"                );
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);

    arquivo = fopen("CFuncionario.txt","w"); // ABERTURA DO ARQUIVO, AB+ SE NAO EXISTIR ELE CRIA, SE ELE EXISTIR ELE ABRE O ARQUIVO PARA LEITURA E GRAVA플O, SEMPRE APOS O ULTIMO ARQUIVO EXISTENTE
    if (arquivo==NULL) // tratamento de erro para caso nao existir
    {
        printf("NAO E POSSIVEL CRIAR OU ABRIR O ARQUIVO.");
        exit(0);
    }

    else
    {
        fread(&funcionarios, sizeof(struct Funcionarios),1,arquivo);//COMANDO DE LEITURA
       while(!feof(arquivo))
        {
            if(CFuncionarios == funcionarios.CFuncionarios)
            {
                CFuncionarios = CFuncionarios +1;
            }
            fread(&funcionarios, sizeof(struct Funcionarios),1,arquivo);//COMANDO DE LEITURA
        }
        funcionarios.CFuncionarios = CFuncionarios;

        gotoxy(4,10);
        printf(" Nome do Funcionario:");
        gotoxy(4,12);
        printf(" Endereco do Funcionario:");
        gotoxy(4,14);
        printf(" Telefone do Funcionario:");
        gotoxy(4,16);
        printf(" RG do Funcionario:");
        gotoxy(4,18);
        printf(" CPF do Funcionario:");
        gotoxy(4,20);
        printf(" Funcao do Funcionario:");

        gotoxy(4,11);
        fgets(funcionarios.nome,100,stdin);
        funcionarios.nome[strcspn(funcionarios.nome,"/n")] = 0;

        gotoxy(4,13);
        fgets(funcionarios.endereco,200,stdin);
        funcionarios.endereco[strcspn(funcionarios.endereco,"/n")] = 0;

        gotoxy(4,15);
        fgets(funcionarios.telefone,50,stdin);
        funcionarios.telefone[strcspn(funcionarios.telefone,"/n")] = 0;

        gotoxy(4,17);
        fgets(funcionarios.rg,12,stdin);
        funcionarios.rg[strcspn(funcionarios.rg,"/n")] = 0;

        gotoxy(4,19);
        fgets(funcionarios.cpf,14,stdin);
        funcionarios.cpf[strcspn(funcionarios.cpf,"/n")] = 0;

        gotoxy(4,21);
        fgets(funcionarios.funcao,50,stdin);
        funcionarios.funcao[strcspn(funcionarios.funcao,"/n")] = 0;


       // GRAVAR OS DADOS NO ARQUIVO


       fwrite(&funcionarios, sizeof(struct Funcionarios),1, arquivo);
       gotoxy (4,21);
       printf("FUNCIONARIOS REGISTRADOS COM SUCESSO!!! /n");


    }

    //FECHAR O ARQUIVO
    fclose(arquivo);
    gotoxy (4,23);
    system("pause");
    menuGeral();



}


//AREA DE CADASTRO FORNECEDOR

void incluirFornecedor()
{
    struct Fornecedor fornecedor;
    FILE *arquivo; // ponteiro
    int CFornecedor = 1;
    system("cls"); // limpeza de tela
    bordas();
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("      CADASTRO DE FORNECEDORES"                   );
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);

    arquivo = fopen("CFornecedor.txt","w"); // ABERTURA DO ARQUIVO, AB+ SE NAO EXISTIR ELE CRIA, SE ELE EXISTIR ELE ABRE O ARQUIVO PARA LEITURA E GRAVA플O, SEMPRE APOS O ULTIMO ARQUIVO EXISTENTE
    if (arquivo==NULL) // tratamento de erro para caso nao existir
    {
        printf("NAO E POSSIVEL CRIAR OU ABRIR O ARQUIVO.");
        exit(0);
    }

    else
    {
        fread(&fornecedor, sizeof(struct Fornecedor),1,arquivo);//COMANDO DE LEITURA
       while(!feof(arquivo))
        {
            if(CFornecedor == fornecedor.CFornecedor)
            {
                CFornecedor = CFornecedor +1;
            }
            fread(&fornecedor, sizeof(struct Fornecedor),1,arquivo);//COMANDO DE LEITURA
        }
        fornecedor.CFornecedor = CFornecedor;

        gotoxy(4,10);
        printf(" Nome Fantasia do Fornecedor:");
        gotoxy(4,12);
        printf(" Telefone do Fornecedor:");
        gotoxy(4,14);
        printf(" CNPJ do Fornecedor:");
        gotoxy(4,16);
        printf(" E-mail do Fornecedor:");

        gotoxy(4,11);
        fgets(fornecedor.nomefantasia,100,stdin);
        fornecedor.nomefantasia[strcspn(fornecedor.nomefantasia,"/n")] = 0;

        gotoxy(4,13);
        fgets(fornecedor.telefone,50,stdin);
        fornecedor.telefone[strcspn(fornecedor.telefone,"/n")] = 0;

        gotoxy(4,15);
        fgets(fornecedor.cnpj,14,stdin);
        fornecedor.cnpj[strcspn(fornecedor.cnpj,"/n")] = 0;

        gotoxy(4,17);
        fgets(fornecedor.email,12,stdin);
        fornecedor.email[strcspn(fornecedor.email,"/n")] = 0;


       // GRAVAR OS DADOS NO ARQUIVO


       fwrite(&fornecedor, sizeof(struct Fornecedor),1, arquivo);
       gotoxy (4,19);
       printf("FORNECEDOR REGISTRADO COM SUCESSO!!! /n");


    }

    //FECHAR O ARQUIVO
    fclose(arquivo);
    gotoxy (4,23);
    system("pause");
    menuGeral();



}

//AREA DE CADASTRO PRODUTOS

void incluirProduto()
{
    struct Produtos produtos;
    FILE *arquivo; // ponteiro
    int CProduto = 1;
    system("cls"); // limpeza de tela
    bordas();
    gotoxy (28,2);
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("CADASTRO DE PRODUTOS");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);

    arquivo = fopen("CProduto.txt","w"); // ABERTURA DO ARQUIVO, AB+ SE NAO EXISTIR ELE CRIA, SE ELE EXISTIR ELE ABRE O ARQUIVO PARA LEITURA E GRAVA플O, SEMPRE APOS O ULTIMO ARQUIVO EXISTENTE
    if (arquivo==NULL) // tratamento de erro para caso nao existir
    {
        printf("NAO E POSSIVEL CRIAR OU ABRIR O ARQUIVO.");
        exit(0);
    }

    else
    {
        fread(&produtos, sizeof(struct Produtos),1,arquivo);//COMANDO DE LEITURA
       while(!feof(arquivo))
        {
            if(CProduto == produtos.CProduto)
            {
                CProduto = CProduto +1;
            }
            fread(&produtos, sizeof(struct Produtos),1,arquivo);//COMANDO DE LEITURA
        }
        produtos.CProduto = CProduto;

        gotoxy(4,10);
        printf(" Nome do Produto:");
        gotoxy(4,12);
        printf(" Preco Compra:");
        gotoxy(4,14);
        printf(" Preco Venda:");
        gotoxy(4,16);
        printf(" Lucro:");

        gotoxy(4,11);
        fgets(produtos.nomeProduto,100,stdin);
        produtos.nomeProduto[strcspn(produtos.nomeProduto,"/n")] = 0;

        gotoxy(4,13);
        fgets(produtos.precoCompra,50,stdin);
        produtos.precoCompra[strcspn(produtos.precoCompra,"/n")] = 0;

        gotoxy(4,15);
        fgets(produtos.precoVenda,14,stdin);
        produtos.precoVenda[strcspn(produtos.precoVenda,"/n")] = 0;

        gotoxy(4,17);
        fgets(produtos.lucro,12,stdin);
        produtos.lucro[strcspn(produtos.lucro,"/n")] = 0;


       // GRAVAR OS DADOS NO ARQUIVO


       fwrite(&produtos, sizeof(struct Produtos),1, arquivo);
       gotoxy (4,19);
       printf("PRODUTO REGISTRADOS COM SUCESSO!!! /n");


    }

    //FECHAR O ARQUIVO
    fclose(arquivo);
    gotoxy (4,23);
    system("pause");
    menuGeral();



}



//CONSULTAR

void consultaCliente()
{
    struct Cliente cliente;
    int CCliente = 0, encontrou = 0;
    FILE *arquivo; // ponteiro
    system("cls"); // limpeza de tela
    bordas();
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("          CONSULTA DE CLIENTES                    ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);
    gotoxy (4,9);
    printf("Digite o nome do cliente:");
    gotoxy (30,9);
    scanf("%d",&CCliente);


    //abrir o arquivo
    arquivo = fopen("CCliente.txt", "w");
    if (arquivo==NULL) // tratamento de erro para caso nao existir
    {
        printf("NAO E POSSIVEL CRIAR OU ABRIR O ARQUIVO.");
        exit(0);
    }
    else
    {
        fread(&cliente, sizeof(struct Cliente),1,arquivo);
        while (encontrou == 0 &&!feof(arquivo))
        {
            if (cliente.nome == 'A' && cliente.CCliente==CCliente) //VERIFICAR COMO LOCALIZAR
            {
                encontrou = 1;
                gotoxy (4,12);
                printf("NOME ...: %d", cliente.nome);
                gotoxy (4,13);
                printf("ENDERECO:",cliente.endereco);
                gotoxy (4,14);
                printf("TELEFONE: %d", cliente.telefone);
                gotoxy (4,15);
                printf("EMAIL...:",cliente.email);
                gotoxy (4,16);
                printf("CPF.....:",cliente.cpf);
                gotoxy (4,17);


            }
            else
                {

                fread(&cliente, sizeof(struct Cliente), 1, arquivo);
                }
        }
        if (encontrou == 0)
        {
            gotoxy(4,15);
            printf("CADASTRO NAO ENCONTRADO!!!");
        }

    }

        fclose(arquivo);
        gotoxy(4,23);
        system("pause");
        consultaCliente();


}

void relatorioProdutos()
{
    struct Produtos produtos;
    FILE *arquivo, *temp;
    system("cls"); // limpeza de tela
    bordas();
    gotoxy (28,2);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",218,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,191);
    gotoxy(28,3);
    printf ("%c               CTECH                 %c",179,179); // NOME DO LOCAL
    gotoxy(28,4);
    printf ("%c     Tecnologia personalizada        %c",179,179);
    gotoxy (28,5);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",192,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,217);
    gotoxy (28,6);
    printf ("          TELA DE RELATORIO  PRODUTOS            ");
    gotoxy (28,7);
    printf ("%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c%c",196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196,196);

    temp = fopen("relatorioProdutos.txt","w+");
    arquivo = fopen("CProduto.txt", "w");


    fputs("NOME DO PRODUTO, PREÇO DE COMPRA, PREÇO DE VENDA, LUCROS\r",temp);

    fread(&produtos, sizeof(struct Produtos),1,arquivo);//COMANDO DE LEITURA
    while(!feof(arquivo))
    {
        fprintf(temp,"%s, %s, %s ,%s",produtos.nomeProduto, produtos.precoCompra, produtos.precoVenda, produtos.lucro); // GRAVAÇÃO DOS DADOS NO ARQUIVO TEMPORARIO
        fread(&produtos, sizeof(struct Produtos),1,arquivo);//COMANDO DE LEITURA
    }
    fclose(temp);
    fclose(arquivo);
    gotoxy (4,12);
    printf ("RELATORIO GERADO COM SUCESSO!!!");
    gotoxy(4,23);
    system("pause");
    menuGeral();

}

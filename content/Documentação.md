# FUNÇÕES
### tolower_str
**void tolower_str(char str_atual[], char str_lower[])**

Pega a string *str_atual* e transforma todas as letras dela em letras minúsculas.
Você deve inserir a string que receberá a string com as letras minúsculas no lugar do argumento *str_lower*.
### tentar_novamente
**bool tentar_novamente()**

Deve ser usada toda vez que o user inseriu comando não válido (como um caractere quando o programa pedia um número inteiro, ou um número negativo quando o programa deve aceitar somente números positivos, etc).

A função funciona da seguinte forma: ela pergunta se o usuário que tentar novamente e executa um scanf que lerá comando do user, 'y' sendo sim e 'n' sendo não.

Caso o user insira 'y' a função irá retornar *true*, caso o user insira 'n' a função irá retornar *false* e caso o user digite nenhum desse dois caracteres, a função irá se chamar recursivamente até que o user digite 'y' ou 'n'.

### menu
**void menu()**

printa o menu no terminal.

### ordem_alfa
**void ordem_alfa(Equipe equipes[], int arr_alfa[], int n_equipes)**

Essa função ordena a *arr_alfa*, que contém os índices da array *equipes* de acordo com a ordem alfabética dos nomes das equipes na array equipes

Outras funções usadas dentro dessa função: [[#tolower_str]]

### q_resolvidas
**int q_resolvidas(Equipe \*equipe)**

Essa função lê quantas questões a *equipe* resolveu e retorna a soma de questoes resolvidas

### soma_t_subs
**int soma_t_subs(Equipe \*equipe)**

Essa função lê quanto tempo a *equipe* acumulou em cada questão e retorna a soma desses tempos

### ordem_pont
**void ordem_pont(Equipe equipes[], int arr_pont[], int n_equipes)**

Essa função ordena a *arr_pont*, que contém os índices da array *equipes* de acordo com a ordem de pontuação das equipes. Sendo os critérios para pontuação: número de questões resolvidas (maior melhor) e soma de tempo (menor melhor).

Ela funciona da seguinte forma: Ela compara o número de questoes resolvidas da equipe que deve ser inserida (EQ_INS) com a da equipe que já está posicionada no array (EQ_POS), caso o numero de questoes resolvidas da EQ_POS > EQ_INS, a EQ_POS é movida um elemento pra direita, caso contrário, a EQUI_INS é inserida nesse índice.

Porém, caso o número de questoes da EQ_POS == EQ_INS, a função irá fazer a comparação da soma de tempo das equipes. Quando soma de tempo da EQ_POS > EQ_INS, a EQ_POS será movida para a direita, caso contrário a EQ_INS será inserida nesse índice.

Outras funções usadas dentro dessa função: [[#q_resolvidas]] e [[#soma_t_subs]].

### ler_str
**void ler_str(char str[], int tam)**

Essa função solicita que o usuário insira uma string, lendo espaços em branco e parando quando o user insere um '\n'. Após a leitura, a função insere um '\0' no final da string.

**Argumentos:** 
char str[]: variável onde será armazenada a string inserida pelo user;
int tam: número máximo de caracteres que a string deve possuir

### cadastro
**void cadastro(Equipe equipes[], int \*n_equipes)**

Função que solicita o usuario os dados da equipe a ser cadastrada e modifica o proximo elemento vazio da array de equipes com esses novos dados.

**Argumentos:**
Equipe equipes[]: array com os structs das equipes;
int \*n_equipes: ponteiro da variavel que contém o numero de equipes que ja foram cadastradas

Outras funções usadas dentro dessa função: [[#ler_str]].

### buscar_equipes
**int buscar_equipe(Equipe equipes[], char nome_equipe[], int arr_alfa[], int n_equipes)**

Função que busca uma equipe que tenha o mesmo nome que a string *nome_equipe*. Essa função usa o método de busca binária.

Retorna indíce da equipe no array *equipes* ou -1, caso uma equipe com o mesmo nome que *nome_equipe* não tenha sido encontrada

**Argumentos:**
Equipe equipes[]: array com as structs de equipes;
char nome_equipe[]: string com o nome que deve ser procurado;
int arr_alfa[]: array em ordem alfabetica, essencial para a busca binaria;
int n_equipes: número de equipes atualmente cadastradas.

Outras funções usadas dentro dessa função: [[#ordem_alfa]], [[#tolower_str]], [[#ler_str]].

### questao_para_int
**int questao_para_int(char questao)**

Transforma caractere de uma questão em int, para que esse int possa ser usado como indíce nas arrays de questões dentro dos structs de equipes. Retorna número da questão.

**Argumentos:**
char questao: caractere com letra da questão.

### questao_valida
**bool questao_valida(int questao)**

Testa se o número da questão está entre 0 e número máximo de questões - 1. Retorna *true*, caso teste for verdadeiro.

**Argumentos:**
int questao: número da questão.

### questao_resolvida
**bool questao_resolvida(Equipe* equipe, int questao)**

Testa se questão x já foi resolvida. Retorna *true* caso teste for verdadeiro.

**Argumentos:**
Equipe* equipe: ponteiro da equipe a ser analisada;
int questao: número da questão a ser testada.

### tempo_valido
**bool tempo_valido(int tempo)**

Testa sem *tempo* > 0. Caso sim, retorna *true*.

### aval_valido
**bool aval_valido(char aval[])**

Checa se string *aval* está entre aquelas discriminadas no enunciado do trabalho.

**Argumentos:**
char aval[]: string contendo o aval inserido pelo user.

Outras funções usadas dentro dessa função: [[#tolower_str]].

### codigo_aceito
**bool codigo_aceito(char aval[])**

Checa se código inserido foi aceito, ou seja, caso o *aval* do Judge seja "AC" ou "PE".

**Argumentos:**
char aval[]: string contendo o aval inserido pelo user.

### inserir_sub
**void inserir_sub(Equipe equipes[], int ind_equipe, int questao, int tempo_sub, char aval[])**

Função que insere a submissão realizada pelo user na função [[#reg_sub]].

**Argumentos:**
Equipe equipes[]: array com equipes já cadastradas;
int ind_equipe: índice da equipe na qual a submissão deve ser inserida;
int questao: número da questão que deve ser modificada;
int tempo_sub: variável com o tempo gasto na questão submetida;
char aval[]: string contendo o aval inserido pelo user.

Outras funções usadas dentro dessa função: [[#codigo_aceito]].

### ler_questao
**int ler_questao(Equipe \*equipe)**

Lê questão a ser submetida pelo user e testa se ela é válida e se ela já foi resolvida.

Retorna número da questão ou -1 para caso ela não seja válida ou ela já tenha sido resolvida e o user não queira tentar novamente.

**Argumentos:**
Equipe \*equipe: ponteiro para a equipe que deve ser testada.

Outras funções usadas dentro dessa função: [[#questao_para_int]], [[#questao_valida]], [[#tentar_novamente]], [[#questao_resolvida]].


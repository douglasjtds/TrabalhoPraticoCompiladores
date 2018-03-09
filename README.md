# Trabalho de Compiladores
O trabalho será dividido em três partes
- Análise Léxica
- Análise Sintática
- Análise Semântica

# Análise Léxica - Parte 1 #
O trabalho deverá ser entregue por e-mail até o dia **06/04/2017**: 
- Colocar no assunto para o e-mail: CC-CMA-COMP-TP1
- Não esqueça dos nomes no relatório técnico
- Descrição detalhada do trabalho, regras, o que deve ser entregue e outras informações estão acrescentadas no pdf **TP1_20180306114439.pdf**


## Descrição do trabalho
<p>
	Nesta etapa, você deverá implementar um analisador léxico para a linguagem PasC cuja descrição
	encontra-se nas páginas 3 e 4.
	Seu analisador léxico deverá ser implementado conforme visto em sala de aula, com o auxílio de
	um autômato finito determinístico. Ele deverá reconhecer um lexema e retornar, a cada chamada,
	um objeto da classe Token, representando o token reconhecido de acordo com o lexema encontrado.
	Para facilitar a implementação, uma Tabela de Símbolos (TS) deverá ser usada. Essa tabela conterá,
	inicialmente, todas as palavras reservadas da linguagem. À medida que novos tokens forem sendo
	reconhecidos, esses deverão ser consultados na TS antes de serem cadastrados e retornados.
	Somente palavras reservadas e identificadores serão cadastrados na TS. Não é permitido o cadastro
	de um mesmo token mais de uma vez na TS.
	Resumindo, seu Analisador Léxico deverá imprimir a lista de todos os tokens reconhecidos, assim
	como mostrar o que está cadastrado na Tabela de Símbolos. Na impressão dos tokens, deverá
	aparecer a tupla <nome, lexema> assim como linha e coluna do token.
	Além de reconhecer os tokens da linguagem, seu analisador léxico deverá detectar possíveis erros e
	reportá-los ao usuário. O programa deverá informar o erro e o local onde ocorreu (linha e coluna),
	lembrando que em análise léxica tem-se 3 tipos de erros: caracteres desconhecidos (não esperados
	ou inválidos), string não-fechada antes de quebra de linha e comentário não-fechado antes do fim de
	arquivo.
	Espaços em branco, tabulações, quebras de linhas e comentários não são tokens, ou seja, devem ser
	descartados/ignorados pelo referido analisador.
	Na gramática do PasC, os terminais de um lexema, bem como as palavras reservadas, estão entre
	aspas duplas para destacá-los, ou seja, *as aspas não são tokens.*
</p>

### Gramática da Linguagem PasC
prog → “program” “id” body  
body → decl-list “{“ stmt-list “}”  
decl-list → decl “;” decl-list | ε  
decl → type id-list  
type → “num” | “char”  
id-list → “id” | “id” “,” id-list  
stmt-list → stmt “;” stmt-list | ε  
stmt → assign-stmt | if-stmt | while-stmt | read-stmt | write-stmt  
assign-stmt → “id” “=” simple_expr  
if-stmt → “if” “(“ condition “)” “{“ stmt-list “}” |  
“if” “(“ condition “)” “{“ stmt-list “}” “else” “{“ stmt-list “}”  
condition → expression  
while-stmt → stmt-prefix “{“ stmt-list “}”  
stmt-prefix → “while” “(“ condition “)”  
read-stmt → “read” “id”  
write-stmt → “write” writable  
writable → simple-expr | “literal”  
expression → simple-expr | simple-expr relop simple-expr  
simple-expr → term | simple-expr addop term  
term → factor-a | term mulop factor-a  
factor-a → factor | “not” factor  
factor → “id” | constant | “(“ expression “)”  
relop → “==” | “>” | “>=” | “<” | “<=” | “!=”  
addop → “+” | “-” | “or”  
mulop → “*” | “/” | “and”  
constant → “num_const” | “char_const”  


### Padrões para números, caracteres, literais e identificadores do PasC
- 


###### Contato dos Criadores
- Douglas Tertuliano
<douglasjtds@gmail.com>
- Matheus Pires
<matheuswith51@hotmail.com>
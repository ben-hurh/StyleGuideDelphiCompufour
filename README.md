# Object Pascal Programming
## Guia de Estilo Para Delphi **Compufour**

*“Todo programador tem suas regras de formatação prediletas, mas se ele for trabalhar em equipe, as regras são dela.” – Uncle Bob*


**Introdução**

Uma boa prática de desenvolvimento é seguir um guia de estilo. 
A equipe de desenvolvimento do Delphi baseia-se nas convenções do Object Pascal Style Guide. 

Padrões de Codificação 

Por que usar um padrão de codificação? 
 
A organização do código fonte facilita os processos de desenvolvimento, retirada de bugs, atividades de validação e manutenção. 
O uso de um padrão de codificação também aumenta a produtividade num projeto, uma vez que a comunicação dentro da equipe de desenvolvimento fica mais fácil, mas vale ressaltar que partes desses padrões são vistas, algumas vezes, como sugestões por empresas que adotam seus próprios padrões. 
Fontes:
https://objectpascalprogramming.com/
http://edn.embarcadero.com/article/10280#2.1
https://objectpascalprogramming.com/
https://www.andrecelestino.com/todos-os-artigos-do-blog-andre-celestino/


**Comentários** 
Usamos - (* *) - para iniciar e terminar um comentário com mais de uma linha, esse tipo de comentário é comum para se informar dados gerais e específicos de Unit e métodos, vindo no seu inicio.  Dentro dos comentários com chaves não devemos usar asteriscos, símbolos ou caracteres especiais.  Outro tipo de comentário usado é a barra de data digitada duplamente - // - neste caso o comentário se ressume a uma linha, devendo ser dado um espaço após a segunda barra para começar o texto desejado.


**Cuidados** : 
	-Vida útil do comentário. Comentários que não é atualizado juntamente com as mudanças que ocorrem no código.
        -Localização do comentário.
	**Lembrem-se : COMENTÁRIOS COMPENSAM UM CÓDIGO RUIM.
	Se precisar de comentários pra explicar, revise o código e tente se expressar através dele.**

 
**Indentação** 
Ato de separar os níveis de codificação por espaços em branco.  
No caso da Linguagem Delphi a indentação deve ter dois espaços, não se podendo usar tabulação.
Definir a propriedade Block Idente conforme a sua preferência e utilizar sempre o TAB para indentação. Sugerido 2
  **Espaços em branco** : Os espaços em branco, assim com a linhas, ajudam na legibilidade do código, mas existem as exceções:
   * Entre o método e o parâmetro de abertura:
           procedure CalcularSalario(ID_Funcionario: integer); // Correto
           procedure CalcularSalario (ID_Funcionario: integer); // Incorreto
   * Após um parêntese de abertura ou antes de um parêntese de fechamento:
           procedure CalcularSalario(ID_Funcionario: integer); // Correto
           procedure CalcularSalario( ID_Funcionario: integer); // Incorreto
   * Após um colchete de abertura ou antes de um colchete de fechamento:
           Valor := Matriz[1] // Correto
           Valor := Matriz[ 1] // Incorreto
   * Entre um operador unário(+ ou -) e o seu operando:
           Valor := -1 // Correto
           Valor := - 1 // Incorreto
   * Antes ou depois de um operador ponto( . ):
           Button1.Caption := ‘Correto’; // Correto
           Button1. Caption := ‘Incorreto’; // Incorreto
   * Antes de uma virgula:
           Variav1, Variav2: Integer; // Correto
           Variav1 , Variav2: Integer; // Incorreto
   * Antes de dois pontos:
           Variav1, Variav2: Integer; // Correto
           Variav1, Variav2 : Integer; // Incorreto
   * Antes de ponto e virgula:
           Variav1, Variav2: Integer; // Correto
           Variav1, Variav2: Integer ; // Incorreto
  

**if,  for, while, repeat, try, with** 
Devem estar em mais de uma linha e indentado entre os níveis.  Quando houver begin o mesmo deve estar em uma nova linha e o seu end deve estar no mesmo nível.

	**Exemplos:**

		if Teste then
		  Valor := 10;

		if not Teste then
		begin
		  Valor1 := 10;
		  Valor2 := 20;
		end;

		for I := 0 to ValorFinal do
		begin
		  Valor[I] := ValorFinal * I;
		end;

		while Tabela.Eof do
		begin
		  ShowMessage(Tabela.FieldByName('Nome').AsString);
		  Tabela.Next;
		end;

		repeat
		  Inc(Valor);
		until Valor > 10;

		try
		  try
		    Tabela.Open;
		    Form1.ShowModal;
		  finally
		    Tabela.Close;
		  end;
		except
		  ShowMessage(‘Localizado um erro’);
		end;

		with Tabela do
		begin
		  Append;
		  FieldByName('Nome').AsString := 'Tadeu Pereira';
		  Post;
		end;



**case** 
As opções ficam num nível abaixo do case, sendo assim elas devem estar indentadas.  Caso seja necessário usar o begin, o mesmo deve ser indentado em consideração a opção.  O bloco de comandos deve estar indentado em consideração ao begin.
Observação:  considere criar uma função ao invés de utilizar o case.

		Exemplos:

		case Controle of
		  0..9: Valor := Controle * 3;
		  10: Valor := Controle * 2;
		  else Valor := Controle;
		end;

		case Objeto.Color of
		  clBlack:
		    begin
		      ShowMessage('A cor á preta');
		    end;
		  clWhite:
		    begin
		      ShowMessage('A cor á branca');
		    end;
		end;



**Quebras de linha** 
A linha deve ter no máximo oitenta caracteres, se for ultrapassado esse limite a linha deve ser quebrada.  As linhas seguintes devem ser indentadas e quebradas da mesma maneira.
 procedure MeuMetodo(const Nome: string;
  Idade: Integer; Salario: Extended);

if (X = Y) or (Y = X) or
  (Z = P) or (F = J) then
begin
  S := J;
end;

if (Condicao1) or 
  (Condicao2) or 
  (Condicao3) then


**Organização de Classes**
Quanto aos níveis : Primeiro devem ser feita as declarações em private seguidas pelas feitas em  protected, public e published.

	TMyClass = classe (TObject)
	  private
	  protected
	  public
	  published
	  end;

Quanto a ordenação : Primeiro os campos, seguido pelos métodos e por fim as propriedades.
	TMyClass = class(TObject)
	 private
	   FMyData: Integer;
	   function GetData: Integer;
	   procedure SetData(Value: Integer);
	 public
	 published
	   property MyData: Integer read GetData write SetData;
	end;



**Convenções de nomenclatura**
As convenções adotas para fazer nomeação na Linguagem Delphi é uma seção a parte, uma vez que o padrão muda de acordo com o que se deseja atribuir o nome.
 

**Arquivos**
O nome do arquivo deve ser iniciado com letra u Minúscula seguido da proxima letra maiúscula e o restante deve ter letras minúsculas, salvo os casos em que esse nome é composto por mais de uma palavra, nesse caso cada palavra deve iniciar com letra maiúscula acompanhada por letras minúsculas – chamamos esse uso de maiúsculas e minúsculas de camel caps ou infix caps.  A extensão do arquivo deve conter apenas letras minúsculas.
   Exemplo : uCadastro.pas – uPrincipal.dfm – MeuSistema.dpr
 

**Classes**
A classe deve ser iniciada pela letra T maiúscula acompanhada pelo nome seguindo o padrão infix caps.
   	Exemplo : TNovaClasse – TPessoa – TDiario
 
-Campos : Semelhante a classe, só que nesse caso devemos trocar a letra T pela letra F também maiúscula.
	Exemplo : FNome – FCidade – FLimiteCompra
 
-Métodos : Os métodos devem ter nomes de verbos no imperativo e seguir o padrão de infix caps.
   	Exemplo : CalcularSalario(); – GravarNome(); – VerificarLimite();
 

**Parâmetros**
Também semelhante a classe, e assim como os campos trocamos a letra T, só que nesse caso pela letra A maiúscula.  Esse padrão é uma sugestão que a própria VCL não a segue completamente, sendo usada como opcional.
   	Exemplo : NomeMetodo(AParam1, AParam2: Integer; AParam3: string);
 

**Variáveis**
Variáveis globais é um anti-padrão.
Deve seguir o padrão Infix caps.
Então toda variável é, ou deveria ser, local.
Se variáveis são locais, não deveria haver colisões de nomes. Se não há colisões de nomes, por que utilizar prefixos?
https://objectpascalprogramming.com/variaveis-locais


**Constantes**
Assim como as variáveis, as constantes seguem o padrão Infix caps.
 

**Tipos enumerados**
As iniciais fixas dos valores possíveis dos tipos enumerados devem começar com letras minúsculas, o restante deve seguir o padrão Infix caps.
   Exemplo : TAlignment = (taLeftJustify, taRightJustify, taCenter);


**Princípios SOLID**
Curso completo : https://app.nutror.com/v3/curso/6c7dbb987887/aula/186564?r

**Sigle Responsability Principle**
https://www.andrecelestino.com/solid-dependency-inversion-principle-dip/
Uma classe deve fazer apenas uma coisa, deve fazê-la bem e deve fazer somente ela. Se uma classe tem mais de um motivo para ser alterada, ela não segue este princípio.
Por exemplo, manter informação de vendas é algo que deve ser feito por uma classe Venda e não por uma classe Produto. Manter informação de Produto não deve ser feito por uma classe ItemEstoque e sim por uma classe Produto.

**Open Close Principle**
https://www.andrecelestino.com/solid-open-closed-principle-ocp/
O princípio open Close ou aberto/fechado, é um dos princípios SOLID, O princípio do aberto/fechado nos auxilia a desenhar um software que seja fácil de modificar, e que não sofre com o impacto das mesmas.
“Entidades de software ( classes, métodos, módulo, etc ) devem estar abertas para extensão, mas fechadas para modificação”

**Liskov substitution Principle**
https://www.andrecelestino.com/solid-liskov-substitution-principle-lsp/
“Classes derivadas devem poder ser substitutas de suas classes base”
Em outras palavras, toda e qualquer classe derivada deve poder ser usada como se fosse a classe base.

**Interface segregation principle**
https://www.andrecelestino.com/solid-interface-segregation-principle-isp/
Princípio da segregação de interfaces
está intimamente ligado à Abstração e orienta a identificação e definição adequada das Interfaces. O objetivo é evitar que a arquitetura seja comprometida à medida que novos módulos, componentes ou classes são adicionados ao projeto.

**Dependency inversion principle**
https://www.andrecelestino.com/solid-dependency-inversion-principle-dip/
Princípio da inversão de dependência
Orienta uma forma de inverter as dependências (como o próprio nome diz), elevando o nível de abstração em uma arquitetura. O objetivo é modificá-la para que que as dependências sejam representadas por abstrações, reduzindo o acoplamento.

**Princípio do “Não se repita”**
Repetir a mesma frase várias vezes pode parecer chato e entediante, não é, não é, não é? Pois bem, o artigo de hoje discute justamente sobre a repetição de código e as consequências que ela pode trazer na arquitetura do software.
    
    
    

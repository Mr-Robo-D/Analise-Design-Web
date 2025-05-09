					Análise e Design de uma Aplicação Web de E-commerce de Livraria
Com base nos Atores, Casos de Uso e Regras de Negócio descritas, realize os exercícios na sequência visando a
análise e design de uma Aplicação Web de E-commerce de Livraria.
Atores:

• Cliente (usuário externo): esse ator representa os usuários interessados na compra de livros.
• Funcionário (usuário interno): esse ator representa os funcionários responsáveis pela geração de estatísticas
e o envio de mensagens promocionais aos clientes, bem como a manutenção dos dados dos livros, incluindo
a quantidade em estoque.
• Sistema de Frete: esse ator representa um sistema/componente externo a ser integrado com a aplicação de
software da livraria para calcular o frete a ser pago.
• Sistema de Cartão: esse ator representa um sistema/componente externo a ser integrado com a aplicação de
software da livraria para possibilitar o pagamento por meio de cartão de crédito.
• Sistema de Banco: esse ator representa um sistema/componente externo a ser integrado com a aplicação de
software da livraria para possibilitar a geração do boleto bancário.
• Se necessário, outros atores, inclusive sistemas externos, podem ser identificados.

Casos de Uso:

CSU01: Pesquisar Livro: esse caso de uso representa o processo pelo qual um cliente (usuário externo) pode
pesquisar livros por título, autor, editora ou categoria. Após selecionar uma forma de pesquisa e informar os
parâmetros da pesquisa, o sistema deve exibir uma listagem referente a todos os livros que satisfaçam as
condições de busca, contendo o título, autor, editora, categoria, status e preço, além de dois ícones, um que
permite visualizar os detalhes do livro e outro que possibilita adicioná-lo ao carrinho de compras. Se o cliente
optar por visualizar os detalhes de um dos livros listados, uma nova página será exibida, apresentando um
resumo do livro e seu sumário, além de informações adicionais sobre o autor, o formato do livro (capa dura ou
brochura), número de páginas e o ano de publicação. Se o cliente se interessar por algum dos livros
apresentados após a pesquisa, ele pode adicionar o livro ao carrinho de compras, sendo assim, uma nova página
será exibida, solicitando a confirmação da quantidade de volumes que deseja comprar (o padrão é 1). Tanto o
caso de uso Exibir Detalhes quanto o caso de uso Adicionar ao Carrinho são extensões desse caso de uso
principal. Vale ressaltar que o cliente também pode voltar à tela anterior e selecionar outra forma de pesquisa.


CSU02: Efetuar Pedido: esse caso de uso é referente ao processo de finalização do pedido. Uma vez que o
cliente finalize o pedido, havendo no mínimo um item adicionado ao carrinho, a página de visualização do
carrinho será exibida; desse modo, o cliente poderá confirmar os livros selecionados e suas respectivas
quantidades. Para tal, o cliente deverá estar autenticado pelo sistema, caso ainda não o esteja. Se o cliente
ainda não estiver cadastrado no sistema, primeiro será preciso fazer o cadastro, informando seus dados
pessoais. Na segunda etapa de finalização do pedido, o cliente deve informar o endereço para entrega para o
frete ser calculado, e em seguida selecionar a forma de pagamento, podendo ser por meio de cartão de crédito
ou boleto bancário. Após isso, o cliente concluirá o pedido e a quantidade de livros em estoque deve ser
atualizada. Quando o pedido for confirmado, os itens do carrinho serão destruídos. Esse caso de uso deve ter um
relacionamento de inclusão com o caso de uso Atualizar Estoque. Esse caso de uso também deve ter um
relacionamento de inclusão com o caso de uso Visualizar Carrinho, como também com os casos de uso Calcular
Frete e Efetuar Pagamento; no caso deste último, há duas especializações do caso de uso: Pagar por Cartão ou
Pagar por Boleto.

CSU03: Manter Cliente: esse caso de uso representa a manutenção dos dados pessoais do cliente. Esse
cadastro deve incluir o nome completo, CPF, data de nascimento, e-mail (um ou mais), telefone (um ou mais),
endereço (um ou mais). Uma vez que o cliente ainda não possua cadastro no sistema ou seus dados tenham
sofrido alguma alteração desde a última compra, é necessário registrar ou alterar seu cadastro. Para realizar
esse caso de uso, é necessário o usuário externo estar autenticado pelo sistema mediante login e senha. Esse
caso de uso também é uma extensão do caso de uso Efetuar Pedido.

CSU04: Visualizar Pedido: este caso de uso se refere ao processo pelo qual um usuário pode visualizar tanto dos
pedidos realizados recentemente como o histórico de pedidos. Nesse caso, os usuários poderão consultar seus
pedidos anteriores, além do estado dos pedidos atuais para saber se tais pedidos estão em andamento,
cancelados ou se já foram concluídos e enviados ao cliente. Para realizar esse caso de uso, é necessário o
usuário externo estar autenticado pelo sistema mediante login e senha.

CSU05: Manter Livro: Esse caso de uso é referente à manutenção dos dados do livro. Esse cadastro deve incluir
o título, ISBN, número de páginas, ano de publicação, categoria (uma ou mais), formato do livro (capa dura ou
brochura), status, preço de venda, um pequeno resumo e seu sumário, além de informações sobre o autor (nome
do autor, data de nascimento e local de nascimento). Além desses dados, outros são necessários, porém serão
visualizados somente por usuários internos (funcionário) como preço de custo, margem de lucro, quantidade em
estoque e informações sobre a editora (nome, CNPJ, endereço, telefone e e-mail para contato). Os casos de uso
Manter Autor e Manter Editora são casos de uso estendidos desse caso de uso principal. Para realizar esse caso
de uso, é necessário o usuário interno estar autenticado e autorizado pelo sistema mediante login e senha.


Regras de Negócio:

• RN01: O livro pode apresentar um dos seguintes status em um determinado tempo: disponível, indisponível,
em aquisição ou fora de circulação.
• RN02: Ao finalizar um pedido, deve haver ao menos um item no carrinho.
• RN03: Para livros em circulação, o estoque mínimo não pode ser menor do que 2 volumes. Uma vez que o
estoque atinja essa quantidade, os usuários internos devem ser informados.
• RN04: A cada quatro livros adquiridos em um mesmo pedido, o livro de valor mais baixo não deve ser
cobrado.
• RN05: O frete é isento para o estado de São Paulo.
• RN06: O pagamento pode ser realizado por meio de cartão de crédito ou boleto bancário. O pagamento por
cartão de crédito pode ser realizado em até 3 vezes sem juros; já o pagamento por boleto bancário deve ser
feito à vista, havendo nesse caso 10% de desconto.
• RN07: O pedido pode apresentar um dos seguintes status em um determinado tempo: cancelado, pagamento
pendente, em processamento, confirmado, em transporte ou concluído.


Exercícios:
1- 
a) Especifique textualmente a visão de sistema do CSU01, explicitando a sequência de interações entre o
ator (esse passo deve ser identificado como estímulo) e o sistema (esse passo deve ser identificado como
resposta), nos fluxos (cenários) principal, alternativo e de exceção, de acordo com o template disponibilizado.
Os diferentes tipos de fluxo devem estar organizados apropriadamente pelo número do passo;

b) Com o intuito de modelar a lógica do caso de uso, modele um diagrama de atividades para representar os passos
computacionais detectados nos passos do caso de uso; 

c) Visando a identificação dos eventos de sistema a
partir dos estímulos verificados nos passos referentes ao ator, construa os protótipos de interface de usuário
(baixa, média ou alta fidelidade) para esse caso de uso. 

2-
a) Especifique textualmente a visão de sistema do CSU02, explicitando a sequência de interações entre o
ator (esse passo deve ser identificado como estímulo) e o sistema (esse passo deve ser identificado como
resposta), nos fluxos (cenários) principal, alternativo e de exceção, de acordo com o template disponibilizado.
Os diferentes tipos de fluxo devem estar organizados apropriadamente pelo número do passo; 

b) Com o intuito de modelar a lógica do caso de uso, modele um diagrama de atividades para representar os passos
computacionais detectados nos passos do caso de uso; 

c) Visando a identificação dos eventos de sistema a partir dos estímulos verificados nos passos referentes ao ator, construa os protótipos de interface de usuário
(baixa, média ou alta fidelidade) para esse caso de uso.

3- 
a) Especifique textualmente a visão de sistema do CSU03, explicitando a sequência de interações entre o ator
(esse passo deve ser identificado como estímulo) e o sistema (esse passo deve ser identificado como
resposta), nos fluxos (cenários) principal, alternativo e de exceção, de acordo com o template disponibilizado.
Os diferentes tipos de fluxo devem estar organizados apropriadamente pelo número do passo; 

b) Com o intuito de modelar a lógica do caso de uso, modele um diagrama de atividades para representar os passos
computacionais detectados nos passos do caso de uso; 

c) Visando a identificação dos eventos de sistema a
partir dos estímulos verificados nos passos referentes ao ator, construa os protótipos de interface de usuário
(baixa, média ou alta fidelidade) para esse caso de uso. 

4- 

a) Especifique textualmente a visão de sistema do CSU04, explicitando a sequência de interações entre o ator
(esse passo deve ser identificado como estímulo) e o sistema (esse passo deve ser identificado como
resposta), nos fluxos (cenários) principal, alternativo e de exceção, de acordo com o template disponibilizado.
Os diferentes tipos de fluxo devem estar organizados apropriadamente pelo número do passo; 

b) Com o intuito de modelar a lógica do caso de uso, modele um diagrama de atividades para representar os passos
computacionais detectados nos passos do caso de uso; 

c) Visando a identificação dos eventos de sistema a partir dos estímulos verificados nos passos referentes ao ator, construa os protótipos de interface de usuário
(baixa, média ou alta fidelidade) para esse caso de uso.

5- Especifique textualmente a visão de sistema do CSU05, explicitando a sequência de interações entre o ator
(esse passo deve ser identificado como estímulo) e o sistema (esse passo deve ser identificado como
resposta), nos fluxos (cenários) principal, alternativo e de exceção, de acordo com o template disponibilizado.
Os diferentes tipos de fluxo devem estar organizados apropriadamente pelo número do passo; 

b) Com o intuito de modelar a lógica do caso de uso, modele um diagrama de atividades para representar os passos
computacionais detectados nos passos do caso de uso; 

c) Visando a identificação dos eventos de sistema a partir dos estímulos verificados nos passos referentes ao ator, construa os protótipos de interface de usuário (baixa, média ou alta fidelidade) para esse caso de uso.

6- Modele um Diagrama de Casos de Uso com base nas especificações textuais dos casos de uso. Os casos de
uso incluídos, estendidos e especializados também devem ser representados.

7- 
a) Elabore os cartões CRC (Class-Responsibility-Collaboration) para o CSU01; 

b) Modele uma VCP (Visão de Classes Participantes) a partir dos cartões e do próprio caso de uso, utilizando os <<estereótipos>> UML
para representar a categorização BCE (Boundary, Control, Entity). A classe de controle deve apresentar as
devidas operações e as classes de entidade devem apresentar os atributos e operações requeridas. As
multiplicidades dos relacionamentos devem ser exibidas.

8- 
a) Elabore os cartões CRC (Class-Responsibility-Collaboration) para o CSU02; 

b) Modele uma VCP (Visão de Classes Participantes) a partir dos cartões e do próprio caso de uso, utilizando os <<estereótipos>> UML para representar a categorização BCE (Boundary, Control, Entity). A classe de controle deve apresentar as devidas operações e as classes de entidade devem apresentar os atributos e operações requeridas. As
multiplicidades dos relacionamentos devem ser exibidas. 

9- 
a) Elabore os cartões CRC (Class-Responsibility-Collaboration) para o CSU03; 

b) Modele uma VCP (Visão de Classes Participantes) a partir dos cartões e do próprio caso de uso, utilizando os <<estereótipos>> UML para representar a categorização BCE (Boundary, Control, Entity). A classe de controle deve apresentar as devidas operações e as classes de entidade devem apresentar os atributos e operações requeridas. As
multiplicidades dos relacionamentos devem ser exibidas. 

10- 
a) Elabore os cartões CRC (Class-Responsibility-Collaboration) para o CSU04; 
b) Modele uma VCP (Visão de Classes Participantes) a partir dos cartões e do próprio caso de uso, utilizando os <<estereótipos>> UML para representar a categorização BCE (Boundary, Control, Entity). A classe de controle deve apresentar as devidas operações e as classes de entidade devem apresentar os atributos e operações requeridas. As
multiplicidades dos relacionamentos devem ser exibidas.

11- 
a) Elabore os cartões CRC (Class-Responsibility-Collaboration) para o CSU05; 
b) Modele uma VCP (Visão de Classes Participantes) a partir dos cartões e do próprio caso de uso, utilizando os <<estereótipos>> UML para representar a categorização BCE (Boundary, Control, Entity). A classe de controle deve apresentar as devidas operações e as classes de entidade devem apresentar os atributos e operações requeridas. As
multiplicidades dos relacionamentos devem ser exibidas.

12- Modele um diagrama de classes reunindo as classes de projeto de todas as VCPs refinadas. Por causa da
quantidade versus legibilidade das notações, esse diagrama deve exibir somente o nome e o estereótipo de
cada classe, como também seus relacionamentos e multiplicidades 

 Segundo Gefersom:
 1. Vimos que há a possibilidade de se selecionar webcontents e coleções de webcontents via configurações de fragmentos. Então, pensamos em como utilizar as funções de templates para extrair informações de webcontents para popular os campos do fragmento. Assim, um fragmento poderia utilizar um webcontent ou nao. Se o webcontent for escolhido via configurações então, as funções de framarker iriam recuperar as informações do journalAticle(webcontent) para popular o fragmento. Caso um webcontent não seja selecionado, então, o fragmento disponibilizaria para o usuário campos editáveis. Há também a possibilidade de se usar coleções, com isso um único fragment poderia iterar na coleção e ir criando todas as estruturas necessárias.
    
2. _[_11:56_]_
    
    Um bom exemplo seria o fragmento de card de notícia que poderia receber uma coleção de notícias e com isso criar todas as renderizações de cards. Discutimos sobre como poderíamos colocar funções de freemarker globais para que sejam utilizadas dentro dos fragmentos. Para extrair dados de journalAticles precisamos dos identificadores dos campos das estruturas. Assim, a longo prazo isso geraria o problema de um mesmo identificador ter o seu valor literal em n fragmentos. Causando o problema de repetição de código e aumento da complexidade de manutenção. Pensamos em (foi o @WillianPessoa ) em colocar mais um menu no painel da esquerda onde um admin poderia configurar constantes e elas serem disponibilizadas globalmente no freemarker do site. (editado)
    
3. _[_11:56_]_
    
    Pensamos também em como construir dinamicamente uma classe que contesse os dados das estruturas. Ela buscaria a definição da estrutura via backend, extrairia os identificadores dos campos e criaria uma classe estática no Java. Esta classe ficaria disponivel globalmente para acesso no freemarker. Os atributos da classe teriam seus nomes como os rotulos da estrutura e os seus valores os identificadores dos campos da estrutura. Discutimos também como fazer com que o site não quebrasse caso o webcontent de configuração de site fosse deletado por algum publicador. Hoje, todos os nossos sites podem quebrar caso esses webcontents sejam removidos. Pensamos em como tornar esse webcontent não editável por não publicadores. Pensamos na possiblidade de adicionar mais um menu lateral ao liferay e ali colocar as opções de configuração do site.
    
4. _[_11:57_]_
    
    [https://learn.liferay.com/w/dxp/site-building/developer-guide/reference/fragments/fragment-configuration-types-reference](https://learn.liferay.com/w/dxp/site-building/developer-guide/reference/fragments/fragment-configuration-types-reference "https://learn.liferay.com/w/dxp/site-building/developer-guide/reference/fragments/fragment-configuration-types-reference")
Após isso, ele começou a colocar algumas das nossas funções de busca dados num módulo permitindo o uso dentro de fragmentos:

![[Liferay/Fragmentos/Pasted image 20230718212315.png]]
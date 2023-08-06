A ideia é criar um script capaz de :
- comparar entre o commit atual e a última tag
- atualizar o changelog  com as tarefas fechadas (busca por OP e mais algum tratamento deve resolver)
- criar uma tag e gravar ela para referência do próximo release (se conseguirmos buscar na lista de tags com um padrão  e retornar a mais recente, ótimo! Nem precisa gravar ela no repositório)
- apresentar uma lista de fragmentos que precisam ser propagados
- gerar o compress contendo somente os fragmentos alterados.
- fazer o commit da tag para o master


Confere se está no diretório dos fragmentos.
se não foi passada a tag base como parâmetro, 
	obtem a listagem de tags do git. Tags devem estar no formato "deploy-YYYYMMDD-HH:mm"
	Obtem a tag mais recente da listagem
executa o git diff --only-names \<tag\> e salva numa variável "modifiedFiles"
	Se não houve mudanças, imprima uma mensagem e saia.
executa o commando git log \<tag\> e grava a saída em "changesSinceTag"

Faça uma lista com os fragmentos que tiveram uma mudança (lista de diretórios únicos) e grave em uma variável "modifiedFragments"

Prepare um diretório temporário e copie os arquivos necessários para rodar o yomen.
Copie os diretórios listados em "modifiedFragments" para esse diretório temporário
copiar os arquivos collection.json dos fragmentos alterados.
rode o comando yo liferay-fragments:compress e escolha "n" para não colocar uma descrição
Copie o arquivo zip da pasta build para a raiz.
Apague a pasta temporária
Prepare a variável changesSinceTag para escolher apenas as linhas com o ticket do open project e nome dele.
Edite o arquivo changelog.txt e inclua a data atual, seguido do conteúdo preparadado de "changesSinceTag"
Se não foi passada a flag --do-not-commit
	Adicione o arquivo no git e faça um commit.
	Crie uma tag com o formato "deploy-YYYYMMDD-HH:mm
	Envie para o repositório git



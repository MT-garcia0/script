# Apredizado script
## Descrição do seu script
### Objetivo

O objetivo do script é criar um diretório para o ano, dentro do qual ele cria um subdiretório para o mês fornecido, e dentro deste, cria subdiretórios numerados de 1 até o número de dias do mês. O script também calcula se o ano fornecido é bissexto e ajusta o número de dias para fevereiro.

### Probemas resolvidos

Cálculo Automático do Número de Dias por Mês (Considerando Anos Bissextos)
Automação do Processo de Criação de Diretórios
Facilidade na Organização de Arquivos e Dados Temporais

## Explicação detalhada do código
### Criação do Diretório para o Ano e Mês


![image](https://github.com/user-attachments/assets/49dd792f-53ec-43b0-a022-e5ae02d8f37e)



O comando if not exist "%1" verifica se o diretório com o nome do ano (%1 é o primeiro parâmetro passado ao script) já existe. Se não existir, o comando mkdir "%1" cria o diretório.

O comando cd "%1" então entra no diretório criado ou já existente.

Da mesma forma, o comando if not exist "%2" verifica se o diretório para o mês (%2 é o segundo parâmetro passado ao script) existe. Se não, ele cria o diretório com o nome do mês.

O comando cd "%2" então entra no diretório do mês.

### Definição das Variáveis



![image](https://github.com/user-attachments/assets/a7ac6a93-ad79-414c-87d6-9c8df213991e)


As variáveis mes e ano são configuradas para os valores dos parâmetros passados para o script. O %1 é o ano, e o %2 é o mês.

Esses valores são armazenados nas variáveis mes e ano para facilitar o uso posterior no script.


### Cálculo de Ano Bissexto


![image](https://github.com/user-attachments/assets/aa939b34-25aa-49da-bf82-1fa5837fa3b0)


 O comando set /a realiza operações aritméticas. Aqui, as variáveis resto1, resto2 e resto3 armazenam os resultados de operações de módulo que determinam se o ano é bissexto.
 
resto1 = %ano% %% 4: Calcula o restante da divisão do ano por 4.

resto2 = %ano% %% 100: Calcula o restante da divisão do ano por 100.

resto3 = %ano% %% 400: Calcula o restante da divisão do ano por 400.

O ano bissexto é determinado pela seguinte lógica:

Um ano é bissexto se ele for divisível por 4.

Mas, se ele for divisível por 100, também precisa ser divisível por 400 para ser considerado bissexto.

As instruções if verificam essas condições e atribuem o valor 1 (ano bissexto) ou 0 (não bissexto) à variável bissexto.

### Determinação do Número de Dias no Mês



![image](https://github.com/user-attachments/assets/6cd80cb4-8752-416a-8ca5-f0164de4b5f9)



Cada if verifica o valor da variável mes e define a quantidade de dias de acordo com o mês:

Para fevereiro (mes=2), o número de dias depende da variável bissexto:

Se for bissexto (se bissexto for 1), o mês terá 29 dias.

Se não for bissexto, terá 28 dias.

Para os outros meses, o número de dias é definido diretamente:

Meses como janeiro (mes=1), março (mes=3), maio (mes=5), etc., têm 31 dias.

Meses como abril (mes=4), junho (mes=6), setembro (mes=9), novembro (mes=11) têm 30 dias.


### Criação de Subdiretórios para os Dias do Mês


![image](https://github.com/user-attachments/assets/9fbc5c92-a63e-4434-b1b1-27c349a45e3d)


O loop for é utilizado para criar subdiretórios numerados de 1 até o número de dias do mês (%dias%).

O comando for /L %%i in (1,1,%dias%) cria um loop que começa com %%i = 1, vai até %%i = %dias%, incrementando %%i de 1 em 1.

Para cada valor de %%i, o comando mkdir %%i cria um diretório com o número correspondente.

Isso resulta na criação de subdiretórios numerados de 1 até o número de dias do mês, por exemplo, de 1 a 28, 29, 30 ou 31, dependendo do mês e ano.


### Retorno ao Diretório Anterior

![image](https://github.com/user-attachments/assets/a97fc534-bf4a-47ea-b7b7-c9f11a24edab)

O comando cd .. faz com que o script retorne ao diretório anterior. Isso é útil para garantir que o script termine no diretório em que foi iniciado, após a criação dos diretórios e subdiretórios.

### Desafios e soluções

#### Desafios

Os desafios foi realmente entender a parte do ano bixesto e fazer funcionar.

#### Soluções

Fazer testes um pouco de pesquisa e ajuda dos amigos

### O que aprendeu

Aprendi a trabalhar com ano bixesto, automatizar tarefas que envolvem manipulação de diretórios e dados temporais.

### Possíveis melhorias

Antes de criar um diretório, podemos verificar se a estrutura completa (ano > mês > dia) já existe, economizando tempo e adicionar uma verificação para garantir que o ano e o mês fornecidos sejam válidos antes de executar o restante do script.


















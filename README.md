# Desafio Power BI

# Problema
A empresa X possui uma equipe no departamento de TI que é responsável pelos custos de TI da organização. Para fazer essa gestão, foi criado um banco de dados, que possui a seguinte configuração:

1. Tabela fato, onde são armazenadas as informações de custo de maneira normalizada. (FTOTIN) 
2. Dimensão TI, que registra qual a área de TI responsável por aquele custo. (DIMTIN) 
3. Dimensão Área de Negócio, onde é armazenada a informação de qual é a área de negócio que está financiando o custo. (DIMARENEG) 
4. Dimensão Elemento de Custo, que registra o nome de cada um dos elementos de custo da tabela Fato. (DIMELECTO) 
5. Dimensão País, que registra qual o país de origem daquele custo. (DIMPAS) 
6. Dimensão VP Departamento, que registra qual a Vice Presidencia daquele custo. (DIMVDP) 
7. Dimensão cenário, que registra se o custo é real, planejado, etc. (DIMCEN) 
8. Dimensão tempo, que é uma tabela de registra os tempos da tabela fato. (DIMTPO) 

O líder dessa área suspeita que os custos de TI internacionais (ou seja, fora dos Estados Unidos) estão muito altos. Por isso, ele pediu que você criasse um relatório em Power BI que pudesse ajudar a visualizar melhor como esses custos estão distribuídos nas diferentes dimensões.

# Etapas do Projeto

## Análise do Problema
A primeira etapa foi analisar o documento com o problema de negócio a ser resolvido para a realização do desafio.
O problema consiste em possibilitar a análise dos custos que a TI da empresa está tendo fora do país EUA (internacionais).

## Tratamento dos Dados
A segunda etapa foi realizar o ETL, importando os dados das planilhas disponibilizadas e transformando-os conforme necessário. Na etapa de transformação foi necessário remover as linhas duplicadas presentes em uma das tabelas DIM, que devem ter registros únicos para que as ligações no Power BI ocorram com a cardinalidade correta para o projeto.

## Construção do Relatório
Depois disso, com todos os dados no formato correto e o problema definido, foi iniciada a etapa de construção do Relatório para essa análise.

### Personalização do tema
A primeira etapa realizada na construção do Relatório foi a personalização do tema, incluindo como cores principais as da empresa, que foram extraídas diretamente da logo através de um aplicativo que identifica o código hexadecimal das cores de uma imagem (foi utilizada a funcionalidade do PowerToys da Microsoft).

Com o tema personalizado, foi iniciada a etapa de construção efetiva do relatório.

### Cabeçalho
Foi criado um cabeçalho com as cores e logo da empresa, o título do relatório e um botão "Sobre" que direciona para outras informações sobre o projeto.

### Filtros
Logo abaixo foi criado uma área de filtros com um separador (linha) para os dados.

### Cartões/Navegação
Depois dos filtros foram inseridos 5 cartões que demonstram o valor de custo dos cenários disponibilizados na base de dados. Cada botão desses ao clicar dá o direcionamento para aquele cenário específico, e automaticamente a página é filtrada para o selecionado. Além disso, existe uma legenda em cada um dos cartões e foi adicionado uma sombra verde no cartão que está selecionado.

### Indicadores
Abaixo dos cartões tem uma área de resumo das informações, que tem um indicador KPI com o Valor Total Gasto e o Valor Total Planejado, para monitoramento se foi gasto mais do que o planejado e ao lado tem uma caixa de texto com o formato narrativa inteligente, que se adapta automaticamente conforme filtros selecionados e informa alguns dados importantes para a análise, de forma bem resumida e de fácil entendimento.

### Gráficos
Depois desse resumo inicia-se o bloco de gráficos, tendo:

* Gráfico de Cascata, com título Total de Gasto por Área e Negócio, que demonstra o valor de custo por cada área de negócio e tem como dica de ferramenta o valor planejado o % de diferença entre o valor efetivo e o planejado.
* Gráfico Treemap, com título Total de Gasto por Área de TI, que demonstra o valor de custo por cada área do setor de TI e tem como dica de ferramenta uma página com um gráfico das sub áreas de TI, dessa forma fica fácil de visualizar as subdivisões ao passar o mouse sob a informação.
* Gráfico de Barras Clusterizado, com o título Total de Gasto por Sub Área de TI, que demonstra o valor de custo por cada Sub Área de TI e tem como dica de ferramenta o valor planejado o % de diferença entre o valor efetivo e o planejado, além de uma linha de gasto médio.
* Gráfico de Barras Clusterizado, com o título Total de Gasto por Elemento de Custo, que demonstra o valor de custo por cada Elemento de Custo e tem como dica de ferramenta o valor planejado o % de diferença entre o valor efetivo e o planejado.
* Gráfico de Linhas, com o título Total de Gasto por Ano e Mês, que demonstra o valor de custo por Ano e Mês e ainda conta com uma ferramenta de Análise do tipo Previsão, com a previsão de gasto dos próximos 6 meses.
* Gráfico de Área, com o título Gasto Total Acumulado por Ano e Mês, que demonstra o valor de custo acumulado de custo por Ano e Mês (soma todos os valores anteriores conforme passa o mês).
* Mapa, com o título Gasto Total por País, que demonstra o valor de custo por País no formato geográfico.
* Matriz de valores de gasto, valor planejado, diferença entre gasto e planejado no formato absoluto e percentual por Região e País, na coluna de % Dif também existe uma formatação condicional de ícones, onde se o gasto for menor que o valor planejado exibe o símbolo de "Ok", se o gasto realizado ultrapassou o planejado em até 33% exibe o símbolo de "Alerta", e acima disso exibe o símbolo de "Problema".
* Árvore hierárquica, com o título Hierarquia de Gastos, que exibe toda a hierarquia de gastos, desde a Área de Negócio até a Sub Área de TI e os valores de gastos.
* Nuvem de Palavras, com o título de Gasto Total por Elemento de Custo, que exibe os elementos e seus respectivos valores de gastos.

## Funcionalidades do Power BI
### Utilizadas no Projeto
* PowerQuery e Linguagem M para a etapa de transformação;
* DAX para os cálculos das medidas;
* Visuais Padrão;
* Visuais Personalizados;
* Ferramentas de Análise de Gráficos (Previsão e Linha Média);
* Indicadores;
* Seleção de objetivos (ocultar e exibir);
* Filtros de Visual;
* Filtros de Página;
* Filtros no formato Segmentação de Dados;
* Relacionamento entre tabelas e cardinalidade;
* Boas práticas nas medidas (utilização de variáveis, medidas em uma tabela exclusiva);
* Narrativas Inteligentes;
* Formatação Condicional;
* Indicadores KPI;
* Botões e Navegação;
* Dicas de Ferramenta (Padrão e Página de Relatório);
* Técnicas de Visualização:
> * Visualização em Z, tendo as informações mais importantes no topo da página;
> * Cores que se relacionam com a empresa (Identidade Visual);
> * Escolha dos gráficos com base nos tipos e quantidade de variáveis;
> * Padronização de fontes e tamanho.

### Outras que o Autor tem Conhecimento
* Integração Power BI com R e Python (para gráficos e ETL);
* Medidas complexas em DAX;
* RLS (Row Level Security);
* Power BI Service;
* Gateway;
* SQL Avançado;
* DAX Studio;
* Performance Analyzer;
* Dashboards;
* Parâmetros;
* Atualização Incremental.
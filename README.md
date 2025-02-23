# Análise de Vendas 2024

### Autor: Carlos Afonso Feldhaus Filho

Dashboard de apresentação dos resultados do vendedor no ano de 2024, empresa do ramo de telecomunicações a qual possui uma gama de produtos.


## Ferramentas Utilizadas

 - Microsoft Excel
 - Power BI
 - Microsoft Copilot

### Principais funções e ferramentas utilizadas no Power BI:

- Fórmulas em DAX
- Transformação de dados no Power Query
- Criação de Relacionamento em tabelas
- Criação de Visualizações
- Filtros

## Dados Brutos Disponíveis

Os dados estavam armazenados em planilha de excel, adicionados de forma manual pelos colaboradores da empresa, foi extraído uma amostra destes dados para a criação do Dashboard.

Os dados disponíveis para análise contem: 
    
- Data de Venda
- Data de ativação do Serviço 
- Identificação
- Tipo de Produto / Serviço
- Valor da Venda
- Valor do Plano Antigo (Em caso de Renovação do Cliente)

### Obersavação: *Esses dados foram alterados, anonimizados e não condizem com a realidade da empresa*

## ELT e Análise dos Dados:

### Após carregados os dados no Power BI, foram realizadas alguns ajustes:

- Alteração do tipo de dados
- Correção de erros
- Substituição ou exclusão de valores nulos

### Criação da Tabela Calendário com DAX:

Para auxiliar nas consultas e criação dos gráficos, foi criado uma Tabela Calendário utilizando DAX, com a seguinte sintaxe:

    Calendario = 
        VAR vAnoMin = YEAR(MIN(Dados[Data de ativação]))
        VAR vAnoMax = YEAR(MAX(Dados[Data de ativação]))
        VAR vDataInicial = DATE(vAnoMin, 01, 01)
        VAR vDataFinal = DATE(vAnoMax, 02, 01)
        RETURN
        ADDCOLUMNS(
        CALENDAR(
        vDataInicial,
        vDataFinal
         ),
        "Ano", YEAR([Date]),
        "MesNum", MONTH([Date]),
        "MesNome", FORMAT([Date], "MMMM"),
        "Dia", DAY([Date])
    )

### Como base nos dados disponíveis foi então levantado as informações:

- Número de Venda Total do Vendedor
- Número de Clientes Refidelizados
- Valor Total de Vendas no ano
- Valor do Ticket Médio

### Gráficos:

- Gráfico de Barras demonstrando o número Total de Vendas por linha de produto
- Gráfico de Área demonstrando o Valor Toral de Vendas em 2024

## Mapa de Vendas

### A planilha chamada CEP foi criada com ajuda do Microsoft Copilot, gerando pontos de Latitude e Longitude na cidade de Blumenau - SC e também um ponto em outra localidade, para aprimorar as possibilidades de apresentação da ferramenta.

Após a criação do Mapa, também foi adicionada a segmentação dos dados, com um simples podemos acessar o ponto e verificar as informações de venda naquele local.

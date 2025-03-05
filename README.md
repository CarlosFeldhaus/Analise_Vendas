
# Análise de Vendas 2024

### Autor: Carlos Afonso Feldhaus Filho

Dashboard de apresentação dos resultados do vendedor no ano de 2024, empresa do ramo de telecomunicações a qual possui uma gama de produtos/serviços.

Foi realizada uma análise dos dados disponíveis para entender o **padrão de venda** e elaboração de um **Mapa de Vendas** para entender a distribuição e alcance da atuação do vendedor.


## Ferramentas Utilizadas

 - Microsoft Excel
 - Power BI
 - Microsoft Copilot

### Principais funções e ferramentas utilizadas no Power BI:

- Fórmulas em DAX
- Transformação de dados no Power Query
- Criação de relacionamento em tabelas
- Criação de visualizações
- Filtros

## Dados Brutos Disponíveis

Os dados estavam armazenados em planilha de Excel, adicionados de forma manual pelos colaboradores da empresa, foi extraído uma amostra destes dados para a criação do Dashboard.

Os dados disponíveis para análise contem: 
    
- Data de Venda
- Data de ativação do Serviço 
- Identificação
- Tipo de Produto / Serviço
- Valor da Venda
- Valor do Plano Antigo (Em caso de Renovação do Cliente)

### Observação: *Esses dados foram alterados, anonimizados e não condizem com a realidade da empresa*

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
         "Dia", DAY([Date]),
         "Semana", WEEKNUM([DATE],2),
         "SemanaNum", INT((DAY([Date]) - 1) / 7) +1,
         "Quinzena", IF(DAY([Date]) <= 15, 1, 2)
    )
### Como base nos dados disponíveis foi então levantado as informações:

- Número de Venda Total do Vendedor
- Número de Clientes Refidelizados
- Valor Total de Vendas no ano
- Valor do Ticket Médio

### Gráficos:

- Gráfico de Barras demonstrando o número Total de Vendas por linha de produto
- Gráfico de Área demonstrando o Valor Total de Vendas em 2024
- Gráfico de Colunas comparando as vendas realizas por quinzena

## Análise do Ciclo de Vendas

Está análise é a demonstração de como as vendas vão ocorrendo dentro dos meses, ela também traz um insight interessante, pois no quandro geral a primeira quinzena do mês vende cerca de **9%** a mais que a segunda quinzena, porém quando separamos mês a mês temos a seguinte situação:

![image](https://github.com/user-attachments/assets/5307712e-ed0b-4973-b6d3-38dd121d5ada)

De maneira geral, as vendas da segunda quinzena, em média, são **27%** maiores que a primeira, porém o mês de dezembro é um ponto fora da curva, onde cerca de 2/3 (**66%**) das vendas ocorrem na primeira quinzena.

Com esta informação o gestor pode comprar com os demais vendedores e verificar se o padrão se repete, pode gerar novas campanhas de vendas para este período ou também pode organizar as férias da equipe conforme o fluxo das vendas.

## Mapa de Vendas

### A planilha chamada CEP foi criada com ajuda do Microsoft Copilot, aonde a IA gerou os pontos de Latitude e Longitude.

Após a criação do Mapa, também foi adicionada a segmentação dos dados, com um simples podemos acessar o ponto e verificar as informações de venda naquele local.

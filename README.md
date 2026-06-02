# Finance Executive Dashboard | Power BI PBIP

Dashboard financeiro executivo desenvolvido em **Power BI PBIP**, com foco em modelagem dimensional, medidas DAX profissionais e visual premium para portfolio. O projeto transforma lancamentos financeiros em uma experiencia analitica moderna, com estetica inspirada em produtos SaaS, fintechs e paineis corporativos executivos.

## Objetivo

O painel responde, de forma direta e visualmente refinada:

- Quanto entrou e quanto saiu?
- Qual foi o resultado financeiro do periodo?
- O resultado melhorou ou piorou?
- Quais categorias mais geram receita e despesa?
- Quais formas de pagamento sao mais utilizadas?
- Quais meses tiveram melhor ou pior desempenho?
- O negocio esta financeiramente saudavel?

## Destaques do Projeto

- Projeto em formato **PBIP**, adequado para versionamento no GitHub.
- Layout redesenhado para **1920x1080**.
- Tema **dark premium** com visual de produto digital.
- Modelo dimensional em formato estrela.
- Tabela de medidas centralizada em `medidas`.
- KPIs e tabelas criados com medidas HTML/CSS dinamicas.
- Navegacao entre paginas com experiencia executiva.
- Filtros laterais organizados e visualmente integrados.
- Medidas DAX para analise base, temporal, acumulada, YTD, variacoes e indicadores.
- Tabelas HTML para evitar visual vazio/padrao e melhorar acabamento visual.

## Stack Utilizada

- Power BI Desktop
- Power BI Project Format `.pbip`
- TMDL
- DAX
- Power Query
- HTML/CSS em medidas DAX
- Git/GitHub

## Estrutura do Projeto

```text
.
+-- dash_financeiro.pbip
+-- dash_financeiro.Report
|   +-- definition.pbir
|   +-- report.json
|   +-- StaticResources
|       +-- SharedResources
|           +-- BaseThemes
|               +-- CY24SU10.json
+-- dash_financeiro.SemanticModel
|   +-- definition
|   |   +-- model.tmdl
|   |   +-- relationships.tmdl
|   |   +-- tables
|   |       +-- fat_lancamentos_financeiros.tmdl
|   |       +-- dim_calendario.tmdl
|   |       +-- dim_categoria.tmdl
|   |       +-- dim_forma_pagamento.tmdl
|   |       +-- medidas.tmdl
|   +-- diagramLayout.json
+-- README.md
```

## Modelo de Dados

O modelo segue uma estrutura em estrela, com uma tabela fato central e dimensoes de apoio.

### Tabela fato

`fat_lancamentos_financeiros`

Colunas principais:

- `id`
- `tipo`
- `descricao`
- `categoria`
- `valor`
- `data_lancamento`
- `forma_pagamento`
- `observacao`
- `criado_em`

### Dimensoes

`dim_calendario`

- `Data`
- `Ano`
- `Mes Numero`
- `Mes Nome`
- `Ano Mes`
- `Ordem Ano Mes`
- `Trimestre`
- `Semestre`
- `Dia`
- `Dia da Semana`
- `Nome do Dia da Semana`
- `Inicio do Mes`
- `Fim do Mes`

`dim_categoria`

- `id_categoria`
- `nome_categoria`
- `tipo_padrao`

`dim_forma_pagamento`

- `id_forma_pagamento`
- `forma`
- `descricao`
- `ativo`
- `criado_em`

### Relacionamentos

```text
dim_calendario[Data]              -> fat_lancamentos_financeiros[data_lancamento]
dim_categoria[nome_categoria]     -> fat_lancamentos_financeiros[categoria]
dim_forma_pagamento[forma]        -> fat_lancamentos_financeiros[forma_pagamento]
```

Os relacionamentos foram mantidos no padrao dimensional, evitando relacionamentos muitos-para-muitos.

## Medidas DAX

Todas as medidas estao organizadas na tabela `medidas`.

Categorias principais:

- Base financeira: `Receita Total`, `Despesa Total`, `Resultado`, `Saldo`, `Margem de Resultado %`.
- Volume e ticket: `Total de Lancamentos`, `Ticket Medio`, `Valor Medio por Lancamento`.
- Analise temporal: mes anterior, variacoes absolutas, variacoes percentuais, acumulados e YTD.
- Participacao: receita/despesa por categoria e forma de pagamento.
- Indicadores visuais: cores condicionais, textos de variacao e status de resultado.
- HTML/CSS: headers, cards, filtros, insights e tabelas dinamicas.

O projeto possui **79 medidas** no arquivo `medidas.tmdl`.

## Paginas do Relatorio

### 1. Visao Executiva

Pagina principal do dashboard. Mostra uma leitura rapida da saude financeira geral.

Elementos:

- Cards de Receita, Despesa, Resultado, Margem e Lancamentos.
- Evolucao financeira por mes.
- Resumo executivo dinamico.
- Receitas por categoria.
- Despesas por categoria.
- Forma de pagamento.
- Painel lateral de filtros.

### 2. Receitas

Pagina focada nas entradas financeiras.

Elementos:

- KPIs de receita.
- Receita do mes anterior.
- Variacao percentual.
- Evolucao mensal.
- Receita acumulada.
- Ranking de categorias.
- Forma de pagamento.
- Tabela HTML com maiores receitas.

### 3. Despesas

Pagina focada em controle de gastos.

Elementos:

- KPIs de despesa.
- Despesa do mes anterior.
- Variacao percentual.
- Evolucao mensal.
- Despesa acumulada.
- Ranking de categorias de despesa.
- Forma de pagamento.
- Tabela HTML com maiores despesas.

### 4. Resultado Financeiro

Pagina focada em performance consolidada.

Elementos:

- Resultado.
- Resultado do mes anterior.
- Variacao do resultado.
- Margem.
- Receita vs despesa.
- Resultado mensal.
- Resultado acumulado.
- Margem por mes.

### 5. Detalhamento

Pagina analitica para consulta granular dos lancamentos.

Elementos:

- Cards de resumo.
- Tabela HTML dinamica com lancamentos financeiros.
- Filtros por ano, mes, categoria, forma de pagamento, tipo e descricao.

## Direcao Visual

O design foi construido para fugir do visual padrao do Power BI e se aproximar de uma interface web premium.

Paleta principal:

```text
Fundo principal:    #06111F
Fundo secundario:   #0B1628
Container:          #0F1B2D
Card:               #111F33
Texto principal:    #F8FAFC
Texto secundario:   #94A3B8
Azul destaque:      #38BDF8
Verde positivo:     #22C55E
Vermelho negativo:  #EF4444
Dourado discreto:   #F59E0B
```

Decisoes de UX/UI:

- Interface em dark navy premium.
- Cards com profundidade sutil.
- Layout em grid 1920x1080.
- Filtros organizados em painel lateral.
- Tabelas HTML com linhas, cabecalho e estados vazios tratados.
- Reducao de labels em graficos temporais para melhorar leitura.
- Navegacao superior entre paginas.
- Uso de medidas HTML para criar componentes mais proximos de um web app.

## Como Abrir o Projeto

1. Abra o arquivo `dash_financeiro.pbip` no Power BI Desktop.
2. Caso o Power BI solicite permissao para visual HTML/custom visual, habilite para renderizar os componentes premium.
3. Configure a conexao com a base PostgreSQL usada no Power Query, se necessario.
4. Atualize os dados pelo Power BI Desktop.

> Observacao: o PBIP versiona a definicao do relatorio e do modelo sem armazenar obrigatoriamente os dados carregados.

## Fonte de Dados

As consultas Power Query apontam para PostgreSQL local:

```text
Servidor: localhost
Banco: postgres
Tabelas:
- lancamentos_financeiros
- dim_categoria
- dim_forma_pagamento
```

Para reproduzir o projeto em outra maquina, ajuste as credenciais/conexao no Power BI Desktop.

## Boas Praticas Aplicadas

- Modelo em estrela.
- Tabela calendario dedicada.
- Medidas centralizadas.
- Campos tecnicos ocultos quando nao sao relevantes para o usuario final.
- DAX modular para facilitar manutencao.
- Tema JSON para padronizacao visual.
- Layout responsivo dentro do canvas 16:9.
- Evita excesso de graficos e privilegia leitura executiva.

## Como Apresentar no Portfolio

Sugestao de narrativa:

> "Desenvolvi um dashboard financeiro executivo em Power BI PBIP com foco em modelagem dimensional, medidas DAX profissionais e experiencia visual premium. O projeto utiliza uma arquitetura em estrela, tabela calendario, medidas de resultado, variacoes, acumulados e YTD. A camada visual foi redesenhada com tema dark premium e componentes HTML/CSS para aproximar o relatorio de uma interface SaaS moderna."

Pontos para destacar:

- Transformacao de um relatorio padrao em dashboard executivo premium.
- Uso de PBIP para versionamento e manutencao profissional.
- Medidas DAX de analise financeira real.
- Storytelling claro para tomada de decisao.
- Design consistente com produtos digitais modernos.

## Melhorias Futuras

- Adicionar pagina de tooltip personalizada.
- Criar bookmarks para painel de filtros recolhivel.
- Publicar versao online no Power BI Service.
- Adicionar capturas de tela na pasta `docs/screenshots`.
- Criar video curto demonstrando navegacao e storytelling.
- Parametrizar fonte de dados para facilitar reproducao em outros ambientes.

## Status

Projeto em evolucao, com estrutura PBIP pronta para versionamento, refinamento visual aplicado e documentacao GitHub adicionada.

# Project 01 — Plano de análise e modelação

## Estado verificado

- Repositório GitHub criado e acessível.
- README principal e documentação inicial do Projecto 01 publicados.
- Dataset, limpeza no Power Query e dashboard Power BI ainda não estão confirmados como publicados no repositório.
- O projecto continua em preparação.

## Modelo de dados proposto

### Tabelas de dimensão

- **DimProduto:** Produto_ID, Produto, Categoria, Marca, Preço_Unitário, Custo_Unitário.
- **DimCliente:** Cliente_ID, Cliente, Segmento, Província, Município.
- **DimVendedor:** Vendedor_ID, Vendedor, Equipa, Região.
- **DimCalendário:** Data, Ano, Mês, Número_Mês, Trimestre, Ano_Mês.

### Tabela de factos

- **FactVendas:** Pedido_ID, Data, Produto_ID, Cliente_ID, Vendedor_ID, Quantidade, Desconto, Canal_Venda, Estado_Pedido, Método_Pagamento.

### Relações

- DimProduto[Produto_ID] 1 → * FactVendas[Produto_ID]
- DimCliente[Cliente_ID] 1 → * FactVendas[Cliente_ID]
- DimVendedor[Vendedor_ID] 1 → * FactVendas[Vendedor_ID]
- DimCalendário[Data] 1 → * FactVendas[Data]

## Regras de preparação no Power Query

1. Remover duplicados pelo campo Pedido_ID.
2. Aplicar Trim e Clean a campos de texto.
3. Normalizar Canal_Venda, Estado_Pedido e Método_Pagamento.
4. Validar tipos de dados: datas, inteiros, decimais e texto.
5. Tratar valores nulos sem inventar informação; documentar qualquer exclusão.
6. Criar colunas derivadas:
   - Valor_Bruto = Quantidade × Preço_Unitário
   - Valor_Desconto = Valor_Bruto × Desconto
   - Receita_Líquida = Valor_Bruto − Valor_Desconto
   - Custo_Total = Quantidade × Custo_Unitário
   - Lucro = Receita_Líquida − Custo_Total

## Perguntas de negócio

- Como evoluem as vendas ao longo do tempo?
- Quais categorias e produtos geram mais receita e lucro?
- Que províncias e canais apresentam melhor desempenho?
- Existem vendedores com elevada receita mas margem reduzida?
- Qual é o ticket médio e como varia por segmento?
- Há períodos com queda, concentração ou sazonalidade relevante?

## Entregáveis da próxima etapa

- Consulta Power Query documentada.
- Tabela final validada.
- Dicionário de dados actualizado.
- Medidas DAX testadas.
- Primeira versão do dashboard.

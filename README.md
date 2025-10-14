# JORNADA DE DADOS [<Laboratória>](https://analisededadoslaboratoria.com.br/)
Projeto desenvolvido para o programa Jornada de Dados, oferecido pela organização Laboratória, em outubro de 2025. Rota exploratória em estrutura de dados.

Caso: A VAREJISTA, empresa líder no setor, enfrenta o desafio de gerenciar grandes volumes de dados dispersos. Para aprimorar a tomada de decisões, está sendo implementado um sistema ETL robusto com tabelas fato e dimensões.<br><br>
Objetivo: Neste projeto a analista vai **extrair, transformar e carregar dados** de forma eficiente, estruturá-los hierarquicamente para facilitar análises estratégicas e otimizar o armazenamento.


## Etapas do projeto

1. **Limpeza de dados**
   - Padronização de colunas categóricas (removendo acentos, espaços e letras maiúsculas).
   - Verificação de valores nulos e duplicados.
   - Identificação de outliers e valores inválidos em variáveis numéricas.

2. **Web scraping**
   - Extração de informações sobre empresas concorrentes da Wikipedia.
   - Limpeza e padronização das informações (nomes, números de funcionários, países, etc.).

3. **Construção de dimensões e tabela de fatos**
   - Dimensões: `dim_tempo`, `dim_produto`, `dim_localizacao`, `dim_cliente`, `dim_envio`, `dim_company`.
   - Fato: `fato_vendas`.
   - Cada dimensão recebe uma chave primária (`*_id`) para referência na tabela fato.
   - A tabela fato é construída com chaves estrangeiras para as dimensões e métricas de vendas.

4. **Preparação de atualizações (staging / merge)**
   - Fluxo de atualização projetado:
     1. Receber novos dados do dia (via CSV, API ou outro banco de dados).
     2. Validar e deduplicar no staging.
     3. Merge/upsert nos dataframes das dimensões.
     4. Atualizar a tabela fato com IDs atualizados das dimensões.
     5. Ordem de atualização: **dimensões primeiro, fato por último**.

5. **Upload para BigQuery**
   - Conexão com o BigQuery usando `google-cloud-bigquery`.
   - Upload das tabelas de dimensões e da tabela fato.
   - Função `merge_pandas` simula o comportamento de um `MERGE` do BigQuery.
   - As tabelas são criadas/atualizadas com todos os registros, garantindo idempotência.


## Ferramentas utilizadas

- Python 3
- Pandas
- BeautifulSoup
- Google Cloud BigQuery
- GitHub (versionamento do projeto)
<br>
<br>
<br>
<br>
<small>Alana Fries, 2025.</small>

# Tipologias de precariedade habitacional na Região Metropolitana de São Paulo a partir do Censo 2022

## Objetivo

Identificar tipologias de precariedade habitacional nos 39 municípios da Região Metropolitana de São Paulo (RMSP), a partir das características dos domicílios registradas no Censo Demográfico 2022, em diálogo com a meta 11.1 do Objetivo de Desenvolvimento Sustentável 11 (moradia adequada e serviços básicos). A proposta é analisar os municípios pelas suas características, e não resumi-los em uma pontuação única.

## Dados

- **Fonte:** Instituto Brasileiro de Geografia e Estatística (IBGE), Censo Demográfico 2022, Agregados por Setores Censitários, tema Características dos Domicílios, agregados por município.
- **Unidade de análise:** município (39 municípios da RMSP).
- **Malha municipal:** IBGE, Malha Municipal 2022 (baixada diretamente pelo notebook).
- **Variável suplementar:** população residente em favelas e comunidades urbanas (IBGE). Não entra no agrupamento; é usada apenas para interpretar as tipologias.

A seleção das variáveis, com os critérios, as inclusões e as exclusões, está em [`docs/selecao_variaveis.md`](docs/selecao_variaveis.md).

## Estrutura

```
1_DATA/
  raw/          arquivos originais do IBGE
  processed/    base consolidada e variável suplementar
2_NOTEBOOKS/
  1_BD_consolidacao.ipynb          consolidação da base
  2_AN_selecao_kmeans_RMSP.ipynb   seleção de variáveis, agrupamento e resultados
3_OUTPUTS/      tabelas, gráficos e mapas
docs/           documentação da seleção de variáveis
```

## Como reproduzir

1. Coloque os arquivos do IBGE em `1_DATA/raw/` (lista em `1_DATA/raw/README.md`).
2. Execute `2_NOTEBOOKS/1_BD_consolidacao.ipynb` e copie as saídas para `1_DATA/processed/`.
3. Execute `2_NOTEBOOKS/2_AN_selecao_kmeans_RMSP.ipynb`.

Os notebooks foram desenvolvidos no Google Colab. As bibliotecas estão em `requirements.txt`. O agrupamento usa semente fixa (`random_state=42`) para garantir a reprodutibilidade, e a estabilidade dos grupos é verificada com 50 sementes e com o agrupamento hierárquico de Ward.

## Etapas da análise

1. Triagem estatística das 644 variáveis e mapeamento de redundâncias (correlação de Pearson, |r| ≥ 0,85).
2. Seleção pelos critérios conceituais (privação, dimensões da moradia adequada, variáveis simples).
3. Conversão das contagens em taxas, para eliminar o efeito do tamanho dos municípios.
4. Verificação de redundância entre as taxas e exclusão de variáveis sem variância.
5. Normalização Min-Max.
6. Agrupamento por K-Means, com escolha do número de grupos pelo método do cotovelo e pelo coeficiente de silhueta.
7. Testes de estabilidade (sementes e Ward).
8. Caracterização dos grupos pelas médias das variáveis, ordenadas pela disparidade entre os grupos.
9. Sobreposição da variável suplementar (população em favelas).

## Como citar

ANDRADE, J. N. **rmsp-habitacao-censo2022**: dados e código. [S. l.]: GitHub; Zenodo, [ano]. DOI: [inserir DOI do Zenodo]. Disponível em: https://github.com/julianevesa/rmsp-habitacao-censo2022.

## Licença

Código sob licença MIT (ver `LICENSE`). Os dados são públicos e de autoria do IBGE.

---

**English summary.** Data and code for identifying housing precariousness typologies in the 39 municipalities of the São Paulo Metropolitan Region (Brazil), based on household characteristics from the 2022 Census (IBGE) and related to SDG target 11.1. Variables were selected through statistical screening and explicit conceptual criteria (see `docs/selecao_variaveis.md`), converted into rates, normalized (Min-Max) and clustered with K-Means, with stability checks (multiple seeds and Ward's hierarchical clustering).

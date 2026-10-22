# Seleção das variáveis

A seleção partiu das 644 variáveis de Características dos Domicílios dos Agregados por Setores Censitários do Censo 2022 (IBGE) e combinou três etapas:

1. **Triagem estatística:** estatística descritiva de todas as variáveis, mapeamento de redundâncias por correlação de Pearson (|r| ≥ 0,85), identificação de variáveis repetidas entre tabelas (r = 1) e de variáveis sem variância.
2. **Critérios conceituais explícitos**, aplicados a todas as variáveis:
   - pertencer a uma dimensão da moradia adequada (água, esgotamento sanitário e banheiro, durabilidade da moradia, resíduos sólidos);
   - indicar **privação ou inadequação**, e não adequação ou cobertura do serviço;
   - ser uma variável simples, não cruzada com atributos do responsável pelo domicílio (sexo, cor ou raça).
3. **Verificação estatística do conjunto final:** efeito de escala demográfica (que levou à conversão em taxas), ausência de variância no recorte e redundância entre as taxas (|r| ≥ 0,85).

Regra de inclusão: **todas** as variáveis de privação das dimensões abaixo foram incluídas, exceto as listadas na seção de exclusões, com o respectivo motivo.

## Variáveis incluídas no agrupamento

| Dimensão | Código | Descrição | Denominador da taxa |
|---|---|---|---|
| Durabilidade da moradia | V00006 | Moradores em domicílios particulares improvisados | Total de moradores (V00005 + V00006) |
| Durabilidade da moradia | V00009 | Crianças de 0 a 9 anos em domicílios particulares improvisados | Total de crianças de 0 a 9 anos (V00008 + V00009) |
| Durabilidade da moradia | V00050 | Domicílio em casa de cômodos ou cortiço | Total de domicílios ocupados (v0007) |
| Durabilidade da moradia | V00052 | Estrutura residencial permanente degradada ou inacabada | v0007 |
| Durabilidade da moradia | V00053 | Domicílio improvisado: tenda ou barraca de lona, plástico ou tecido | v0007 |
| Durabilidade da moradia | V00054 | Domicílio improvisado: dentro de estabelecimento em funcionamento | v0007 |
| Durabilidade da moradia | V00055 | Domicílio improvisado: abrigo natural e outras estruturas improvisadas | v0007 |
| Durabilidade da moradia | V00056 | Domicílio improvisado: estrutura improvisada em logradouro público | v0007 |
| Durabilidade da moradia | V00057 | Domicílio improvisado: estrutura não residencial permanente degradada ou inacabada | v0007 |
| Água | V00113 | Abastecimento por poço raso, freático ou cacimba | v0007 |
| Água | V00114 | Abastecimento por fonte, nascente ou mina | v0007 |
| Água | V00115 | Abastecimento por carro-pipa | v0007 |
| Água | V00116 | Abastecimento por água da chuva armazenada | v0007 |
| Água | V00117 | Abastecimento por rios, açudes, córregos, lagos ou igarapés | v0007 |
| Água | V00118 | Outra forma de abastecimento | v0007 |
| Água | V00200 | Água encanada apenas no terreno | v0007 |
| Água | V00201 | Água não chega encanada | v0007 |
| Água | V00464 | Sem ligação à rede geral de distribuição | v0007 |
| Esgoto e banheiro | V00236 | Apenas banheiro de uso comum a mais de um domicílio | v0007 |
| Esgoto e banheiro | V00237 | Apenas sanitário ou buraco para dejeções | v0007 |
| Esgoto e banheiro | V00312 | Esgotamento por fossa rudimentar ou buraco | v0007 |
| Esgoto e banheiro | V00313 | Esgotamento por vala | v0007 |
| Esgoto e banheiro | V00314 | Esgotamento em rio, lago, córrego ou mar | v0007 |
| Esgoto e banheiro | V00315 | Outra forma de esgotamento | v0007 |
| Esgoto e banheiro | V00316 | Sem esgotamento (sem banheiro nem sanitário) | v0007 |
| Resíduos sólidos | V00399 | Lixo queimado na propriedade | v0007 |
| Resíduos sólidos | V00400 | Lixo enterrado na propriedade | v0007 |
| Resíduos sólidos | V00401 | Lixo jogado em terreno baldio, encosta ou área pública | v0007 |
| Resíduos sólidos | V00402 | Outro destino do lixo | v0007 |

> Conferir as descrições com o dicionário oficial do IBGE antes da publicação.

## Variáveis excluídas e motivos

| Código(s) | Motivo da exclusão |
|---|---|
| V00051 | Sem variância no recorte (todos os valores iguais a zero) |
| V00058 | Sem variância no recorte (todos os valores iguais a zero) |
| V00238 | Redundante com V00316 (mesma informação em tabelas diferentes; r = 1) |
| V00463 | [Completar o motivo] |
| V00111, V00112, V00199, V00309, V00310, V00311, V00397, V00398 | Indicam adequação ou cobertura do serviço (correlação inversa com as variáveis de privação) |
| V00232 a V00235; V00485 a V00494 | Indicam conforto ou número de banheiros, e não privação |
| Variáveis cruzadas com sexo, cor ou raça do responsável | Combinam a privação com atributos do responsável; mantida apenas a variável simples |
| [Preencher após a execução] | Redundância entre as taxas (|r| ≥ 0,85) na checagem final |
| N_POP_DPPO (população em favelas e comunidades urbanas) | Classificação territorial do assentamento, e não condição do domicílio; sua definição já envolve precariedade de serviços, o que sobreporia informações. Analisada apenas como variável suplementar, fora do agrupamento |

## Denominadores (não entram no agrupamento)

| Código | Descrição |
|---|---|
| v0007 | Total de domicílios particulares ocupados (permanentes e improvisados) |
| V00001 | Domicílios particulares permanentes ocupados |
| V00005 | Moradores em domicílios particulares permanentes ocupados |
| V00008 | Crianças de 0 a 9 anos em domicílios particulares permanentes ocupados |

## Dimensões não representadas

Duas dimensões da moradia adequada não puderam ser representadas com os Agregados por Setores Censitários: o **adensamento excessivo** e a **segurança da posse**. Elas são tratadas como limitação do estudo.

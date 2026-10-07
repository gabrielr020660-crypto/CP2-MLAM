# Checkpoint 02 — MLAM

## Integrantes do Grupo
* **Gabriel Rodrigues** — RM: 569322
* **Gustavo Guedes Pereira** — RM 569779
* **Lucas Angelo** — RM 569530
* **Gustavo de Souza** — RM 570746
* **Arthur Tae** — RM 570647

---
[CP2 de MLAM]([docs/sobre.md](https://colab.research.google.com/drive/1sW1YLFPacDV_b9hneCwUmMtoTyC82ugF?usp=sharing))
---

## Visão Geral do Projeto
Trabalho prático desenvolvido para a disciplina de MLAM (Turma 1CCPJ) com o objetivo de investigar a relação estatística entre a atividade econômica no Brasil (medida através do Produto Interno Bruto - PIB) e o volume do tráfego de veículos nas rodovias concessionadas (medido pelo Índice ABCR).

Foi implementado um modelo de **Regressão Linear Simples** usando a biblioteca `scikit-learn` em Python, avaliando a capacidade preditiva da taxa de crescimento do PIB sobre o fluxo rodoviário ao longo de 20 anos (2006 a 2025).

---

## Estrutura do Repositório
* `main.ipynb`: Notebook com todo o código de extração, análise exploratória, treino da regressão e métricas de desempenho.
* `dados_pib_abcr.csv`: Base de dados estruturada com os valores anuais agregados do PIB e da ABCR.
* `README.md`: Documentação explicativa do projeto e dos resultados alcançados.

---

## Fontes dos Dados e Tratamento
1. **PIB (IBGE - Tabela 1620 SIDRA):**
   * Série sem ajuste sazonal do índice de volume do PIB a preços de mercado (1995 = 100).
   * Consolidação feita pela média dos 4 índices trimestrais de cada ano.
2. **Índice ABCR (Associação Brasileira de Concessionárias de Rodovias):**
   * Série original de fluxo total de veículos (1999 = 100).
   * Consolidação feita pela média dos 12 índices mensais de cada ano.

---

## Análise Exploratória e Divisão dos Dados
* **Correlação de Pearson:** Encontrada uma correlação linear muito forte de aproximadamente **+0,91** entre o PIB e o fluxo de veículos.
* **Divisão Treino/Teste:**
  * **Treino:** Primeiros 16 anos (2006–2021)
  * **Teste:** Últimos 4 anos (2022–2025)
  * *Observação:* A ordem cronológica dos registros foi mantida sem embaralhamento (`no shuffle`).

---

## Avaliação do Modelo no Conjunto de Teste

| Ano | PIB_indice | ABCR Observado | ABCR Previsto | Erro Absoluto |
|:---:|:----------:|:--------------:|:-------------:|:-------------:|
| 2022 | 184.60 | 168.90 | 173.34 | 4.44 |
| 2023 | 190.00 | 176.40 | 178.68 | 2.28 |
| 2024 | 195.50 | 182.10 | 184.12 | 2.02 |
| 2025 | 200.20 | 187.50 | 188.77 | 1.27 |

### Métricas Alcançadas
* **MAE (Erro Médio Absoluto):** ~2.50
* **MSE (Erro Quadrático Médio):** ~7.80
* **$R^2$ (Coeficiente de Determinação):** ~0.94

---

## Dificuldades e Conclusões
* **Dificuldades encontradas:** Integrar bases com frequências temporais distintas (trimestral no PIB e mensal na ABCR) exigiu padronizar ambas para médias anuais. A queda pontual no tráfego durante o período pandêmico (2020) também gerou um pequeno desvio temporário em relação ao comportamento padrão.
* **Conclusão:** O modelo demonstrou alto poder explicativo ($R^2 \approx 0.94$), confirmando que a movimentação de veículos nas estradas acompanha diretamente o desempenho e o aquecimento da economia do país.

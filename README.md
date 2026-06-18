# Risco de Evasão Acadêmica — Machine Learning + Lógica Fuzzy

Trabalho Final Prático da disciplina de Inteligência Artificial (Tema 1 — Risco de
Evasão Acadêmica). O projeto estima o risco de evasão de estudantes combinando um
modelo de **Machine Learning** (Árvore de Decisão) com um **Sistema de Inferência
Fuzzy**, comparando as decisões das duas abordagens (Abordagem A — Comparação).

- **Disciplina:** Inteligência Artificial — Lógica Fuzzy e Machine Learning
- **Professor:** William Malvezzi
- **Integrantes:** _(preencher com os nomes completos do grupo)_
- **Arquivo principal:** `trabalho_final_IA_evasao_v3.ipynb`

---

## Como executar

### Opção 1 — Google Colab (recomendada)

1. Acesse [https://colab.research.google.com](https://colab.research.google.com).
2. Vá em **Arquivo → Fazer upload de notebook** e selecione `trabalho_final_IA_evasao_v3.ipynb`.
3. No menu, clique em **Ambiente de execução → Executar tudo** (ou `Ctrl+F9`).
4. Pronto. O notebook instala sozinho a única dependência que falta (`scikit-fuzzy`)
   e roda todas as células na ordem.

Não é necessário conectar o Google Drive nem criar pastas. Todos os arquivos
gerados (CSV e gráficos) ficam numa pasta local da sessão chamada `saidas_evasao`,
acessível pelo painel **Arquivos** (ícone de pasta à esquerda). Para baixá-los,
clique nos três pontos ao lado de cada arquivo → **Fazer download**.

> Para guardar os resultados no próprio Google Drive, basta descomentar o trecho
> indicado na **Célula 2** do notebook. Cada pessoa conecta a própria conta — nada
> fica preso a um Drive específico.

### Opção 2 — Jupyter Notebook (local)

Requer Python 3.9 ou superior. Instale as dependências:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn scikit-fuzzy
```

Em seguida, abra o notebook e execute todas as células:

```bash
jupyter notebook trabalho_final_IA_evasao_v3.ipynb
```

A célula `!pip install scikit-fuzzy -q` no início é específica do Colab; ao rodar
localmente ela apenas reinstala uma biblioteca já presente, sem causar problemas.

---

## Bibliotecas utilizadas

| Biblioteca | Função no projeto |
|---|---|
| numpy | Geração dos dados e operações numéricas |
| pandas | Manipulação da base de dados (DataFrame) |
| matplotlib / seaborn | Gráficos da análise e dos resultados |
| scikit-learn | Árvore de Decisão e métricas de avaliação |
| scikit-fuzzy | Sistema de inferência fuzzy |

---

## Estrutura do notebook

O notebook está dividido em quatro partes, executadas de cima para baixo:

- **Parte 1 — Base de dados e análise exploratória:** geração de uma base simulada
  com 200 estudantes, rotulação do risco, estatísticas descritivas e gráficos.
- **Parte 2 — Machine Learning:** treino e avaliação de uma Árvore de Decisão
  (`max_depth=4`), com acurácia, precision, recall, F1, matriz de confusão,
  visualização da árvore e importância das variáveis.
- **Parte 3 — Sistema Fuzzy:** duas variáveis de entrada (frequência e média das
  notas), uma de saída (risco de evasão), funções de pertinência triangulares e
  9 regras do tipo SE…ENTÃO.
- **Parte 4 — Comparação (Abordagem A):** aplica as duas abordagens aos mesmos
  alunos do conjunto de teste e analisa concordâncias e divergências.

> **Importante:** execute as células em ordem, sem pular. Cada parte depende dos
> resultados da anterior (a base gerada na Parte 1 alimenta o modelo na Parte 2, e
> assim por diante).

---

## Arquivos gerados

Ao executar o notebook completo, são criados na pasta `saidas_evasao`:

- `evasao.csv` — base de dados simulada (200 registros)
- `grafico_classes.png` — distribuição das classes de risco
- `grafico_boxplots.png` — variáveis principais por nível de risco
- `grafico_correlacao.png` — mapa de correlação
- `grafico_matriz_confusao.png` — matriz de confusão da Árvore de Decisão
- `grafico_arvore.png` — árvore de decisão treinada
- `grafico_importancia.png` — importância das variáveis
- `grafico_pertinencia.png` — funções de pertinência do sistema fuzzy
- `grafico_comparacao_ml_fuzzy.png` — comparação ML vs Fuzzy
- `grafico_superficie_fuzzy.png` — superfície de decisão do sistema fuzzy

---

## Observações

- A base de dados é **simulada** com distribuições normais, prática permitida pelo
  enunciado quando não há dados reais. O rótulo de risco é gerado por uma função de
  pontuação baseada em critérios pedagógicos.
- A semente aleatória (`np.random.seed(42)` e `random_state=42`) garante que os
  resultados sejam idênticos a cada execução.
- O sistema fuzzy utiliza apenas frequência e média das notas, enquanto o modelo de
  ML utiliza as cinco variáveis. Essa diferença é discutida na seção de comparação
  do relatório.

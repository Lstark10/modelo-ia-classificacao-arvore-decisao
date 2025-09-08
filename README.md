# Segmentação de Clientes com Árvore de Decisão

Este projeto implementa um modelo de machine learning utilizando árvore de decisão para classificar empresas em diferentes segmentos de cliente (Starter, Bronze, Silver, Gold) baseado em características como atividade econômica, localização, idade da empresa, faturamento mensal e nível de inovação.

## 📋 Descrição

O projeto desenvolve um sistema completo de classificação de clientes empresariais, incluindo análise exploratória de dados (EDA), treinamento de modelo com validação cruzada, otimização de hiperparâmetros e deploy através de uma interface web interativa.

## 🎯 Objetivos

- Classificar empresas em segmentos de cliente usando árvore de decisão
- Realizar análise exploratória completa dos dados
- Otimizar hiperparâmetros para maximizar performance
- Visualizar a estrutura da árvore de decisão gerada
- Disponibilizar modelo via interface web para predições em lote


## 🚀 Instalação e Execução
OBS: Caso queira optar por executar em ambientes como Google collab ou Anaconda jupyter, basta descomentar a primeira célula do arquivo ipynb e executar o arquivo
### Pré-requisitos

- Python 3.8+
- pip (gerenciador de pacotes Python)

### Instalação

1. Clone o repositório:
```bash
git clone <url-do-repositorio>
cd arvore-decisao
```

2. Instale as dependências:
```bash
pip install -r requirements.txt
```

### Execução

Execute o notebook principal:
```bash
jupyter notebook modelo_ia.ipynb
```

Ou execute células específicas para:
- **EDA**: Análise exploratória dos dados
- **Treinamento**: Construção e validação do modelo
- **Otimização**: Tuning de hiperparâmetros
- **Deploy**: Lançamento da interface web

## 📦 Dependências

As principais bibliotecas utilizadas estão listadas em `requirements.txt`:

### Análise de Dados
- `pandas`: Manipulação e análise de dados
- `pingouin`: Testes estatísticos (qui-quadrado)

### Visualização
- `plotly`: Gráficos interativos
- `matplotlib`: Visualizações estáticas

### Machine Learning
- `scikit-learn`: Algoritmos ML e métricas
- `optuna`: Otimização de hiperparâmetros

### Interface e Deploy
- `gradio`: Interface web para o modelo
- `ipywidgets`: Widgets para Jupyter
- `joblib`: Serialização do modelo

## 📊 Estrutura dos Dados

### Variáveis de Entrada
- **atividade_economica**: Setor de atuação da empresa (categórica)
- **localizacao**: Região geográfica (categórica)
- **idade**: Tempo de existência da empresa (numérica)
- **faturamento_mensal**: Receita mensal (numérica)
- **inovacao**: Nível de inovação (categórica)

### Variável Alvo
- **segmento_de_cliente**: Classificação em Starter, Bronze, Silver, Gold

## 🔍 Análise Exploratória (EDA)

### Análises Realizadas
1. **Distribuições Univariadas**: Histogramas e gráficos de barras
2. **Distribuições Bivariadas**: BoxPlots por segmento
3. **Tabelas de Contingência**: Relação entre variáveis categóricas
4. **Testes Estatísticos**: Qui-quadrado para independência

### Principais Descobertas
- Variáveis "localização" e "atividade econômica" são independentes do segmento (p > 0.05)
- Variável "inovação" tem forte associação com segmento (p ≈ 0.0)
- Distribuição desbalanceada entre segmentos

## 🌳 Modelo de Machine Learning

### Algoritmo Utilizado
- **DecisionTreeClassifier** do scikit-learn
- Critério de divisão: Gini (padrão)
- Validação cruzada estratificada (3 folds)

### Pipeline de Pré-processamento
1. **SimpleImputer**: Tratamento de valores ausentes
2. **OneHotEncoder**: Codificação de variáveis categóricas
3. **ColumnTransformer**: Aplicação seletiva de transformações

### Otimização de Hiperparâmetros
- **Biblioteca**: Optuna
- **Método**: Tree-structured Parzen Estimator (TPE)
- **Parâmetros otimizados**:
  - `min_samples_leaf`: 1-20
  - `max_depth`: 2-8
- **Trials**: 100 iterações

## 📈 Métricas de Avaliação

### Métricas Principais
- **Acurácia**: Proporção de classificações corretas
- **Precisão**: Por classe (macro e weighted average)
- **Recall**: Sensibilidade por classe
- **F1-Score**: Média harmônica precisão/recall
- **Matriz de Confusão**: Análise detalhada de erros

### Validação
- **Estratégia**: StratifiedKFold (3 splits)
- **Método**: Cross-validation para evitar overfitting
- **Aleatorização**: random_state=51 para reprodutibilidade

## 🎨 Visualizações

### Gráficos Gerados
1. **Distribuições**: Barras e histogramas interativos
2. **BoxPlots**: Relação variáveis numéricas vs segmentos
3. **Tabelas**: Contingência com formatação visual
4. **Árvore de Decisão**: Estrutura visual do modelo
5. **Matriz de Confusão**: Heatmap de classificações

## 🚀 Deploy e Interface

### Interface Gradio
- **Funcionalidade**: Predições em lote via upload de CSV
- **Input**: Arquivo CSV com dados de empresas
- **Output**: Arquivo CSV com predições adicionadas
- **Acesso**: Interface web local

### Modelo Persistido
- **Formato**: Pickle (.pkl) via joblib
- **Conteúdo**: Pipeline completo (pré-processamento + modelo)
- **Versionamento**: Hiperparâmetros otimizados incluídos

## 🔍 Estrutura do Projeto

```
arvore-decisao/
├── modelo_ia.ipynb              # Notebook principal
├── dataset.csv                  # Dataset de entrada
├── modelo_classificacao_decision_tree.pkl  # Modelo treinado
├── predicoes.csv               # Exemplo de saída
├── requirements.txt            # Dependências
└── README.md                   # Este arquivo
```

## 📋 Como Usar

### 1. Análise Exploratória
Execute as células de EDA para entender os dados:
- Distribuições das variáveis
- Testes de independência
- Visualizações interativas

### 2. Treinamento do Modelo
Execute as células de ML para treinar:
- Pipeline de pré-processamento
- Validação cruzada
- Avaliação de métricas

### 3. Otimização
Execute otimização Optuna para melhorar performance:
- Busca automática de hiperparâmetros
- 100 trials de otimização
- Seleção dos melhores parâmetros

### 4. Visualização da Árvore
Gere visualização da árvore final:
- Estrutura de decisão
- Importância das features
- Interpretabilidade do modelo

### 5. Deploy
Lance interface para predições:
- Execute célula do Gradio
- Acesse interface web local
- Faça upload de CSV para predições

## 🤝 Contribuição

Para contribuir com o projeto:

1. Fork o repositório
2. Crie uma branch (`git checkout -b feature/NovaFeature`)
3. Commit suas mudanças (`git commit -m 'Adiciona nova feature'`)
4. Push para a branch (`git push origin feature/NovaFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para detalhes.

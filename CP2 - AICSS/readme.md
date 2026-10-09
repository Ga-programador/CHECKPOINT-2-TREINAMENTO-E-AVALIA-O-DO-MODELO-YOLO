# Checkpoint 2: Treinamento e Avaliação do Modelo YOLOv11

Projeto desenvolvido para a disciplina de **AI Computer Systems e Sensores**, com o objetivo de treinar um modelo de deteção de objetos utilizando o dataset configurado no Checkpoint 1 e avaliar tecnicamente os seus resultados.

---

## Integrantes do Grupo

- **Aline Delphino Chiaramonte** — RM569860
- **Gabriel Gomes dos Santos** — RM573836
- **Victor Dias Rodrigues Bandeira de Azevedo** — RM574108

---

## Objetivo

Treinar um modelo de visão computacional utilizando a arquitetura **YOLOv11** (Ultralytics) para a deteção de objetos (com foco em captura via ESP32-CAM) e analisar as métricas de desempenho obtidas ao final das épocas de treinamento.

---

## Tecnologias e Dependências

- **Linguagem:** Python 3.13+
- **Framework de Visão:** `ultralytics` (YOLOv11)
- **Plataforma de Dataset:** `roboflow`
- **Manipulação e Plotagem de Dados:** `matplotlib`, `seaborn`, `opencv-python`, `pyyaml`
- **Ambiente de Execução:** Google Colab (Aceleração por GPU Tesla T4 / PyTorch + CUDA)

---

## Configuração do Treinamento

| Parâmetro | Valor | Descrição |
| :--- | :--- | :--- |
| **Modelo Base** | `yolo11n.pt` | Pesos pré-treinados do YOLOv11 (versão nano) |
| **Épocas (Epochs)** | 30 | Quantidade total de ciclos de treinamento |
| **Resolução (Img Size)**| 640x640 | Tamanho de entrada das imagens |
| **Batch Size** | 8 | Quantidade de imagens processadas por lote |
| **Otimizador** | Auto (AdamW) | Seleção automática de otimizador e taxa de aprendizado |

---

## Resultados do Modelo

O modelo executou 30 épocas de treinamento e apresentou rápida convergência de métricas de deteção:

- **Imagens de Treino/Validação:** 97 imagens / 98 instâncias
- **Tempo Total de Treinamento:** ~1.6 minutos (0.027 horas) em GPU T4
- **Precisão (P):** 97.9%
- **Revocação / Recall (R):** 98.0%
- **mAP50:** 96.6%
- **mAP50-95:** 95.5%

---

## Estrutura de Ficheiros do Projeto

Abaixo encontra-se a organização de pastas e ficheiros gerada no ambiente do projeto:

```text
.
├── CP1---AICSS---ESP32CAM-2/       # Dataset do Roboflow
│   ├── train/                     # Imagens e anotações de treino
│   │   ├── images/
│   │   ├── labels/
│   │   └── labels.cache
│   ├── README.dataset.txt
│   ├── README.roboflow.txt
│   └── data.yaml                  # Configuração de classes e caminhos
├── CP2/                           # Estrutura principal do Checkpoint 2
│   ├── modelo/
│   │   └── best.pt                # Melhores pesos do modelo treinado
│   ├── notebook/                  # Ficheiros e scripts do Jupyter Notebook
│   └── resultados/                # Visualizações e métricas geradas
│       ├── matriz_confusao.png    # Matriz de confusão do modelo
│       ├── predicao_01.jpg        # Exemplos de predições do modelo
│       ├── predicao_02.jpg
│       └── predicao_03.jpg
├── runs/                          # Histórico de execuções do Ultralytics
│   └── detect/
│       └── runs/
├── sample_data/                   # Dados padrão do ambiente Colab
├── weights/                       # Pesos base
│   └── yolo26n.pt
├── CP2_GRUPO.zip                  # Arquivo comprimido do projeto
└── yolo11n.pt                     # Pesos do modelo pré-treinado
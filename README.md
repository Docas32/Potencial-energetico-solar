 Plataforma GeoAI de Potencial Energético: Paraná (Fase 1 - Solar)

Visão Geral do Projeto

Este repositório contém o código e os resultados da **Fase 1 (Potencial Bruto do Sítio)** da Plataforma Geodesenvolvida para quantificar e mapear o potencial de atração de investimentos em energia renovável nos 399 municípios do Paraná.

**Objetivo:** Criar um **Score de Potencial Bruto (0-100)** que ranqueia os municípios com base exclusivamente na qualidade técnica do recurso solar e do terreno.

## 📌 Status da Fase 1: Potencial Solar Bruto (Concluída)

| Variável | Descrição | Metodologia |
| :--- | :--- | :--- |
| **Recurso ($X_{HSP}$)** | Horas de Sol Pleno (HSP) Anual. | Extraído do Atlas Solar (GOV.BR). |
| **Terreno ($X_{D}, X_{S}$)** | Declividade Média (graus) e Fator de Sombreamento (proxy Hillshade). | **Google Earth Engine (GEE)** sobre Modelo Digital de Elevação (MDE/SRTM). |
| **Resultado** | Score Final Sítio (0-100). | Normalização Min-Max e Soma Ponderada (Pesos $35\%:30\%:35\%$). |

**O Score Final da Fase 1 é um indicador de atratividade técnica e física, sem considerar a infraestrutura de rede e o mercado.**

## ⚙️ Estrutura do Repositório

* **`/src/`**: Contém os *notebooks* ou scripts Python com o código de GeoAI, limpeza de dados e cálculo do score.
* **`/data/raw/`**: Contém os arquivos de dados brutos iniciais (CSV do HSP, Shapefile do IBGE) – *Não devem ser subidos para o GitHub se forem muito grandes.*
* **`/data/processed/`**: Contém o resultado final da Fase 1 (ex: `Relatorio_Potencial_Solar_PR_Fase1.csv`).
* **`README.md`**: Este arquivo.

## 🚀 Como Rodar o Projeto (Fase 1)

### 1. Pré-requisitos

Para rodar o código de GeoAI, você precisará ter instalado e configurado:

* **Python 3.x**
* **Bibliotecas:** `pandas`, `geopandas`, `numpy`, `earthengine-api` (para acesso ao GEE).
* **Autenticação GEE:** O ambiente deve ser autenticado no Google Earth Engine (`earthengine authenticate`).

### 2. Dados Críticos

O script depende de **Assets externos** no Google Earth Engine:

* **Limites Municipais do PR:** O código usa um *Asset ID* (ex: `users/SEU_USUARIO/limites_pr_2024`) que deve ser carregado no GEE para o cálculo da Extração Zonal.
* **Dados Tabulares:** Os arquivos `.csv` de HSP e o Shapefile do IBGE devem ser acessíveis ou estar no diretório `/data/raw/`.

### 3. Principais Outputs

O principal resultado da Fase 1 é o arquivo:

* **`Relatorio_Potencial_Solar_PR_Fase1.csv`**: Tabela com os 399 municípios, mostrando o HSP bruto, Declividade, Fator de Capacidade e o **Score Final do Sítio**.

## 🤝 Próximos Passos (Fase 2)

A **Fase 2** do projeto se concentrará em calcular o **Score de Viabilidade Econômica**, integrando:

1.  Proximidade de Linhas de Transmissão/Subestações (ANEEL).
2.  Capacidade de Absorção da Rede Elétrica.
3.  Dados de Demanda/Consumo (COPEL/EPE).

---
**Contato:** docasdocas33@gmail.com

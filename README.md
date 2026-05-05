# 🖼️ Projeto: Lab de Filtragem Espacial

## 📌 Sobre o Projeto
Este projeto faz parte da disciplina **ES235 - Processamento de Imagem**, do Departamento de Engenharia Biomédica da Universidade Federal de Pernambuco (UFPE). O experimento tem como objetivo principal a implementação de filtros espaciais voltados para a remoção de ruídos em imagens, bem como a avaliação e comparação do desempenho de cada método.

Para os testes, o sistema utiliza um conjunto de 11 imagens: uma imagem original (utilizada como referência/ground truth) e dez versões dessa mesma imagem corrompidas com diferentes ruídos.

## 🛠️ Filtros Implementados
O projeto contempla a implementação de cinco filtros distintos, que operam em janelas de tamanhos específicos (3x3, 5x5, 7x7, 9x9 ou 11x11), definidos previamente de acordo com o grupo de trabalho. 

Os filtros utilizados são:
* **Gaussian Blur (GB)**
* **Moving Average (MA)**
* **Median (Med)**
* **Wiener (Wien)**
* **Interference based speckle filter (IBSF)**

> ⚠️ **Atenção (Filtro de Wiener):** A formulação matemática do filtro de Wiener baseia-se no parâmetro $\alpha$ (alfa). É implementada uma verificação de segurança no código para garantir que o valor de alfa pertença estritamente ao intervalo `[0,1]` durante a execução, prevenindo aberrações visuais na imagem processada. 
> *(Nota: Os filtros MA, Med, Wien e IBSF são referenciados pelo artigo "Interference-Based Speckle Filter").*

## 📊 Métricas de Avaliação
Para determinar a eficiência da remoção de ruído e preservação dos detalhes da imagem original, o desempenho de cada filtro é quantificado através das seguintes métricas:
* **RMSE** (Root Mean Squared Error)
* **SSIM** (Structural Similarity Index)
* **r** (Coeficiente de correlação)
* **SNR** (Relação Sinal-Ruído - calculada a partir das equações de potência do sinal e potência do ruído)
* **Corners** (Quantidade de pontos de junção - implementado com o detector de Harris)

## 📈 Saídas do Algoritmo
Ao ser executado, o algoritmo deve gerar os seguintes resultados para facilitar a análise comparativa:
1. **Tabelas de Desempenho:** Uma tabela para cada filtro detalhando os valores de RMSE, SSIM, r e SNR para cada uma das 10 imagens ruidosas, finalizando com o cálculo da Média e Desvio Padrão para cada métrica.
2. **Visualização de Dados:** Geração de gráficos comparativos, adotando preferencialmente os formatos *Boxplot* ou *Violin Plot*, para contrastar a eficiência dos métodos de filtragem.
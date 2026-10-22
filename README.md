# Simulador de Controle Estatístico de Processo (CEP) — Node-RED

Aplicação interativa desenvolvida em **Node-RED** voltada para o ensino de **Controle e Gestão da Produção**. O fluxo simula o monitoramento contínuo de uma variável de processo industrial em tempo real, gerando dados aleatórios a partir de uma **Distribuição Normal** e aplicando regras de controle de qualidade estatístico.

---

## 🎯 Objetivo Didático

Demonstrar visualmente em sala de aula como funciona a dispersão estatística de um processo industrial sob hipótese de normalidade:
- Diferenciar **causas comuns de variação** (flutuações normais dentro dos limites) de **causas especiais** (desvios que exigem parada/intervenção).
- Praticar a leitura de **Cartas de Controle (Shewhart)** com Linha Média ($\mu$) e Limites de Controle ($LSC$ e $LIC$).
- Entender a regra dos desvios padrão ($\sigma$, $2\sigma$ e $3\sigma$) na classificação de zonas de alerta.

---

## 🚀 Funcionalidades

1. **Gerador Estocástico em Tempo Real**:
   - Nó `Inject` disparado a cada 1 segundo (`repeat: 1s`).
   - Simulação contínua de amostras distribuídas de acordo com uma normal $\mathcal{N}(\mu, \sigma^2)$.

2. **Gráfico de Carta de Controle (Série Temporal)**:
   - Plotagem contínua dos pontos ao longo do tempo.
   - Linhas de referência dinâmicas:
     - **Linha Média / Limite Central (LC)**: Valor esperado do processo.
     - **Limite Superior de Controle (LSC)**: Calculado a partir de $+k\sigma$.
     - **Limite Inferior de Controle (LIC)**: Calculado a partir de $-k\sigma$.

3. **Visualizador Radial ("Bússola" / Indicador de Desvio)**:
   - Representação instantânea da posição da última amostra em relação à média.
   - **Mapeamento de Cores por Zonas de Variação**:
     - 🟢 **Verde**: Processo sob controle ($\vert{}z\vert{} \le 1\sigma$).
     - 🟡 **Amarelo**: Zona de atenção ($1\sigma < \vert{}z\vert{} \le 2\sigma$).
     - 🔴 **Vermelho**: Fora de controle ou alerta crítico ($\vert{}z\vert{} > 2\sigma$).

4. **Log de Alarmes e Eventos Críticos**:
   - Sempre que o processo atinge a zona vermelha ($\vert{}z\vert{} > 2\sigma$), o sistema gera e armazena um registro contendo:
     - **Timestamp**: Data/hora exata do evento.
     - **Valor**: Valor absoluto da amostra detectada.
     - **Tipo de Alerta**: Categoria do desvio (ex.: *Alerta Crítico: Superior* ou *Alerta Crítico: Inferior*).

---

## 🛠️ Pré-requisitos

- [Node.js](https://nodejs.org/) (versões 18.x ou 20.x LTS recomendadas)
- [Node-RED](https://nodered.org/) (instalado global ou localmente)
- Dashboard (ex.: `@flowfuse/node-red-dashboard` ou `node-red-dashboard`, dependendo da biblioteca gráfica utilizada no seu fluxo)





Um painel de monitoramento em tempo real para o mercado Spot da Binance, construído com Python, CustomTkinter e CCXT. A ferramenta filtra e exibe criptomoedas que atendem a um conjunto específico de indicadores técnicos, focando em sinais de continuação de tendência de alta.

💡 Propósito

Este painel foi criado para automatizar a varredura (scan) de centenas de pares de moedas na Binance. Ele aplica um conjunto de filtros técnicos para identificar ativos que estão potencialmente em um momento de "descanso" (RSI neutro) dentro de uma tendência de alta estabelecida (acima da MM20, MACD positivo), sinalizando oportunidades para análise mais aprofundada de scalping ou day trade.

🚀 Recursos

Interface Gráfica Moderna: Utiliza CustomTkinter para uma interface amigável e com tema escuro.

Análise Assíncrona: O monitoramento roda em uma thread separada, garantindo que a interface do usuário nunca trave.

Conexão Direta com a Binance: Usa a biblioteca ccxt para buscar dados de mercado (OHLCV) e tickers em tempo real.

Filtragem de Liquidez: Ignora automaticamente ativos com baixo volume de negociação (< 5 Milhões em 24h), focando apenas em pares com liquidez relevante.

Seleção de Timeframe: Permite que o usuário escolha o timeframe (5m, 15m, 1h, etc.) que servirá de base para o cálculo dos indicadores.

Atualização Automática: O painel executa uma varredura completa em todos os ativos e, em seguida, aguarda 5 minutos para iniciar um novo ciclo de análise.

📈 A Estratégia de Filtragem

O painel busca por ativos que demonstram potencial de continuação de tendência de alta. Um ativo só é listado na tabela se atender a todas as seguintes condições no timeframe selecionado:

Filtro de Volume: O volume de negociação nas últimas 24h deve ser superior a 5 milhões (em USDT ou BUSD) para garantir liquidez.

Indicador RSI: O RSI (Índice de Força Relativa) deve estar entre 50 e 60. Isso busca ativos que não estão sobrecomprados, mas que demonstram força (acima da linha neutra de 50).

Indicador MM20: O preço atual deve estar acima da Média Móvel Simples de 20 períodos (MM20), confirmando a tendência de alta de curto prazo.

Indicador MACD: A linha MACD deve estar acima da linha de Sinal do MACD, indicando momentum de compra.

📍 Cálculo do "Preço de Entrada Médio"

Se um ativo passa por todos os filtros, o script realiza um cálculo adicional:

Ele busca as últimas 12 velas de 5 minutos (totalizando 1 hora).

Calcula o "Preço de Entrada Médio" como o ponto médio (50%) entre a máxima e a mínima desse período de 1 hora. Este valor serve como uma referência visual de uma potencial zona de retração/suporte.

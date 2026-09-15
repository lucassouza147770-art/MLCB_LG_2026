Exercício 1 — Construção da Esteira de Pré-processamento
Objetivo

Criar uma função capaz de limpar e normalizar as mensagens recebidas pelo SAC, deixando o texto preparado para as próximas etapas do sistema.

Etapas realizadas
Conversão do texto para letras minúsculas.
Remoção de pontuação, números e caracteres desnecessários.
Tokenização do texto.
Remoção de stop words.
Aplicação de lemmatization.
Remoção de tokens muito curtos.
Retorno do texto normalizado.
Exemplo

Texto original:

"Olá!!! EU gostaria de saber se vocês estão DEVOLVENDO as mesas que foram compradas ontem."

Texto processado:

"olá gostaria saber devolver mesa comprar ontem"

A lemmatization ajuda a transformar palavras para uma forma mais básica, facilitando o processamento das mensagens pelo sistema.

Diagnóstico

A função de diagnóstico permite visualizar:

Texto original.
Texto normalizado.
Quantidade de caracteres.
Quantidade de tokens antes do processamento.
Quantidade de tokens depois do processamento.
Tokens removidos.
Tokens finais.
Exercício 2 — Representação Semântica com FastText + Mean Pooling
Objetivo

Transformar as mensagens de texto em vetores numéricos que possam ser utilizados pelo classificador.

FastText

O FastText representa as palavras por meio de vetores e utiliza informações de subpalavras. Neste exercício, cada palavra é representada por um vetor de 50 dimensões.

Etapas realizadas
Carregamento do dataset sac_moveis_ac2.csv.
Aplicação da função de pré-processamento do Exercício 1.
Separação das mensagens em tokens.
Criação do corpus para treinamento do FastText.
Criação dos vetores das palavras.
Aplicação do Mean Pooling.
Mean Pooling

O Mean Pooling calcula a média dos vetores das palavras presentes na frase. Dessa forma, várias palavras são transformadas em um único vetor de tamanho fixo.

Isso permite representar uma mensagem inteira numericamente e utilizá-la nas próximas etapas do sistema.

Exercício 3 — Classificador de Intenções com Fallback
Objetivo

Criar um classificador capaz de identificar a intenção de uma mensagem e utilizar um fallback quando a confiança for baixa.

Separação dos dados

Os dados foram divididos em:

80% para treinamento
20% para teste

A divisão foi feita mantendo a proporção das diferentes intenções.

Classificação

Foi utilizada uma Regressão Logística para identificar as intenções das mensagens.

O modelo foi treinado com os vetores gerados pelo FastText + Mean Pooling.

Métricas utilizadas
Accuracy
Precision
Recall
F1-Score
Fallback

O sistema utiliza um limite de confiança de 50%.

Confiança maior ou igual a 50% → resposta automática.
Confiança menor que 50% → FALLBACK_HUMANO.

O fallback é importante para evitar que o chatbot responda automaticamente quando não possui confiança suficiente na classificação.

Testes realizados

Foram testadas mensagens relacionadas a:

Devolução de sofá.
Processo de devolução.
Localização de pedido.
Pedido que não chegou.
Pergunta sem relação com o atendimento da loja.
Exercício 4 — Comparação entre Regressão Logística e KNN
Objetivo

Comparar os dois algoritmos utilizando os mesmos embeddings e avaliar seus resultados.

Resultados
Modelo	Accuracy	Precision	Recall	F1
Regressão Logística	XX%	XX%	XX%	XX%
KNN	XX%	XX%	XX%	XX%
Questão 1 — Qual modelo apresentou melhor desempenho?

O modelo que apresentou os melhores resultados nas métricas de avaliação foi considerado o de melhor desempenho neste teste.

Questão 2 — Por que os resultados podem ser diferentes mesmo utilizando os mesmos embeddings?

Porque os dois algoritmos trabalham de formas diferentes. A Regressão Logística aprende padrões para separar as classes, enquanto o KNN utiliza a distância entre os exemplos.

Questão 3 — O KNN utiliza distância. Por que a qualidade dos embeddings é particularmente importante para esse algoritmo?

Porque o KNN depende diretamente da distância entre os vetores. Embeddings melhores ajudam a manter mensagens com significados semelhantes mais próximas.

Questão 4 — Se o sistema tivesse 100 mil mensagens e centenas de intenções, você escolheria KNN? Justifique.

O KNN poderia ficar mais lento com uma quantidade muito grande de mensagens, pois precisa comparar uma nova mensagem com vários exemplos do conjunto de treinamento.

Questão 5 — Qual modelo você escolheria para colocar em produção neste cenário?

A escolha deve considerar os resultados obtidos nos testes, além do tempo de classificação e da quantidade de dados. O modelo escolhido deve apresentar bons resultados e atender às necessidades do sistema.

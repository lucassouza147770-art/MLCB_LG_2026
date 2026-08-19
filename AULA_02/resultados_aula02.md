#========== PRODUÇÃO DO RELATÓRIO:==============
# Para a entrega completa deste LAB01 você precisa copiar a saída do código (output) e adicionar as repostas das perguntas abaixo:

  --- RESULTADOS DO LAB 01 ---
  Mensagem: 'Quero consultar quanto dinheiro tenho' ==> Intenção Predita: [fazer_pix]
  Mensagem: 'Pode me ajudar a fazer um pix?' ==> Intenção Predita: [fazer_pix]
  Mensagem: 'Gostaria de cancelar meu cartão de crédito' ==> Intenção Predita: [cancelar_conta]


# 1 - Avaliem os resultados e verifiquem se os resultados foram corretos ou incorretos. Coloque a resposta no arquivo do relatório do laboratório

  Mensagens 1 e 3 estariam com intenção predita incorretas e 2 corretas.

# 2 - Detectado algum erro, qual seria a maneira mais correta de melhorar o resultado do algoritmo?
  
  Erro nas mensagens 1 e 3
  Correções seria subscrever códigos em mensagens e intenções colocando as frases inéditas e suas intenções preditas, fazendo com que o bot
  identifique o objetivo do usuário e responda automaticamente com a frase correta para resolver o problema dele.
  
# 3 - Detalhe a função do LogisticRegression no algorítmo.

  A função do LogisticRegression é analisar as palavras da nova mensagem e adivinhar a intenção
  do cliente, escolhendo a opção que tem a maior chance de estar certa.

# Todos os resultados devem ser inseridos no arquivo resultados_aula02.md


#========== PRODUÇÃO DO RELATÓRIO:==============
# Para a entrega completa deste LAB02 você precisa copiar a saída do código (output) e adicionar as repostas das perguntas abaixo:

    --- RESULTADOS DO LAB 02 ---
  Mensagem de Teste: 'Gostaria de devolver o produto que comprei'
  Intenção Predita: troca_devolucao
  
  --- Distribuição de Probabilidades por Classe ---
  Classe [duvida_frete]: 27.99%
  Classe [rastrear_pedido]: 24.54%
  Classe [troca_devolucao]: 47.46%

# 1 - Avaliem os resultados e verifiquem se os resultados foram corretos ou incorretos. Coloque a resposta no arquivo do relatório do laboratório

  Os resultados foram corretos, segundo a divisão de probabilidade a intenção predita "troca_devolução" esta de acordo com a mensagem.

# 2 - Detectado algum erro, qual seria a maneira mais correta de melhorar o resultado do algoritmo?
  
  Não há erros no código.

# 3 - Detalhe a função do Naive Bayes no algorítmo.

  A função Naiva Bayes é calcular a probabilidade da intenção predita na frase inserida pelo usuário
  e escolhendo a classe correta a partir da porcentagem de sua probabilidade.

  
# Todos os resultados devem ser inseridos no arquivo resultados_aula02.md

#========== PRODUÇÃO DO RELATÓRIO:==============
# Para a entrega completa deste LAB03 você precisa colar o código corrigido com os TODOs preenchidos, a acurácia obtida e responder:
# 1 - Qual foi a acurácia obtida pelo modelo no conjunto de teste e por que, em um dataset tão pequeno (9 exemplos), essa métrica pode ser enganosa?
# 2 - Como o modelo de Árvore de Decisão (DecisionTreeClassifier) toma a decisão de separar as intenções do usuário?
# 3 - Qual é o risco de utilizar uma Árvore de Decisão sem limite de profundidade (max_depth) em datasets de texto maiores?

# Todos os resultados devem ser inseridos no arquivo resultados_aula02.md


#========== PRODUÇÃO DO RELATÓRIO:==============
# Para a entrega completa deste LAB03 você precisa colar o código corrigido com os TODOs preenchidos, a acurácia obtida e responder:

  import pandas as pd
  from sklearn.feature_extraction.text import CountVectorizer
  from sklearn.tree import DecisionTreeClassifier
  from sklearn.model_selection import train_test_split
  from sklearn.metrics import accuracy_score
  
  # Dataset de Suporte Técnico
  dados_tech = {
      'mensagem': [
          'Esqueci minha senha de acesso', 'Não consigo entrar no sistema', 'Como redefinir minha senha?',
          'A internet esta muito lenta', 'Sem conexao de rede no escritorio', 'Minha conexao caindo toda hora',
          'Impressora nao esta funcionando', 'Nao consigo imprimir documentos', 'Impressora travada com papel'
      ],
      'intencao': [
          'reset_senha', 'reset_senha', 'reset_senha',
          'problema_conexao', 'problema_conexao', 'problema_conexao',
          'suporte_impressora', 'suporte_impressora', 'suporte_impressora'
      ]
  }
  
  df3 = pd.DataFrame(dados_tech)
  
  # TODO 1: Separe o dataset em X (coluna 'mensagem') e y (coluna 'intencao')
  X = df3['mensagem']
  y = df3['intencao']
  
  # TODO 2: Realize a divisão em treino (70%) e teste (30%) com random_state=42
  X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)
  
  # TODO 3: Instancie o CountVectorizer e ajuste/transforme os dados de treino e teste
  vectorizer = CountVectorizer()
  X_train_vec = vectorizer.fit_transform(X_train)
  X_test_vec = vectorizer.transform(X_test)
  
  # TODO 4: Instancie o DecisionTreeClassifier e treine o modelo com .fit()
  modelo_arvore = DecisionTreeClassifier()
  modelo_arvore.fit(X_train_vec, y_train)
  
  # TODO 5: Gere as predições para o X_test_vec e exiba a acurácia
  mensagem_teste = ["A impressora esta com problemas"]
  mensagem_vec = vectorizer.transform(mensagem_teste)
  y_pred = modelo_arvore.predict(X_test_vec)
  predicoes = modelo_arvore.predict(mensagem_vec)[0]
  acuracia = accuracy_score(y_test, y_pred)
  print(f"Acurácia do Modelo: {acuracia * 100:.2f}%")
  


# 1 - Qual foi a acurácia obtida pelo modelo no conjunto de teste e por que, em um dataset tão pequeno (9 exemplos), essa métrica pode ser enganosa?

  Acurácia do Modelo: 33.33%, o que significa que ele acertou apenas 1 de 3 frases do conjunto de teste (já que 30% de 9 exemplos são quase 3 frases).
  Essa métrica é enganosa em datasets pequenos porque a variação é extrema: acertar ou errar uma única frase altera o resultado em mais de 33%. Além disso, com apenas 6 exemplos para treinar, o modelo não aprendeu padrões reais de linguagem, fazendo com que o resultado dependa puramente da sorte de quais frases caíram no teste.
  

# 2 - Como o modelo de Árvore de Decisão (DecisionTreeClassifier) toma a decisão de separar as intenções do usuário?

  A Árvore de Decisão funciona como um fluxograma de perguntas do tipo "Sim ou Não" baseadas na presença ou ausência de palavras. Como o texto foi transformado em números pelo vetorizador, o algoritmo escolhe palavras-chave específicas para dividir os dados. 
  
# 3 - Qual é o risco de utilizar uma Árvore de Decisão sem limite de profundidade (max_depth) em datasets de texto maiores?

  O maior risco é o Overfitting Superajuste ou decoradas
  Sem um limite, a árvore cria regras gigantescas para decorar cada palavra do treino. O modelo vira um "robô que decorada": ele acerta tudo no treino,  mas erra quase tudo na prática porque não consegue entender sinônimos ou frases novas de usuários reais.
  

# Todos os resultados devem ser inseridos no arquivo resultados_aula02.md


# Resultados - Chatbot Agência de Viagens

### 1. Resultados das Frases Inéditas
O modelo alcançou **100% de acurácia** no teste e classificou as novas frases perfeitamente:
* *"Quero emitir um voo para o Japão..."* ==> `[comprar_passagem]`
* *"Não vou mais viajar e quero meu dinheiro..."* ==> `[cancelar_reserva]`
* *"Pode me passar para o atendimento humano?"* ==> `[falar_atendente]`

### 2. Justificativa Técnica
* **TF-IDF (Vetorizador):** Ele funcionou identificando quais palavras eram mais importantes. O robô aprendeu a focar em termos decisivos como *"voo"*, *"dinheiro"* e *"atendimento"*, ignorando palavras comuns que não ajudavam a definir a intenção.
* **Regressão Logística (Modelo):** Foi usada porque calcula com precisão a chance matemática de a frase pertencer a cada categoria. Como o vocabulário das três intenções ficou bem separado pelo TF-IDF, o modelo tomou a decisão certa sem "decorar" as frases (evitando o overfitting).






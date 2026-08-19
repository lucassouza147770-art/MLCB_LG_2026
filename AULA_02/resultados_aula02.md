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













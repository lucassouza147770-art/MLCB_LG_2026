#========== PRODUÇÃO DO RELATÓRIO:==============

--- RESULTADOS DO LAB 01 (AULA 03) ---
Mensagem: 'Preciso urgente da segunda via da fatura'
Intenção Predita: [segunda_via]
Vocabulário Filtrado (sem stopwords): ['2a', '2a via', 'aberto', 'acordo', 'acordo pagar',
'alterar', 'alterar endereço', 'app', 'atrasada', 'atualizo', 'atualizo dados',
'boleto', 'cadastramento', 'dados', 'dados residenciais', 'débito', 'débito aberto',
'dívida', 'emitir', 'emitir segunda', 'endereço', 'endereço cadastramento', 'fatura', 'fatura atrasada',
'fazer', 'fazer um', 'gostaria', 'gostaria alterar', 'negociar', 'negociar pagamento', 'no', 'no app', 'onde', 'onde atualizo',
'pagamento', 'pagamento dívida', 'pagar', 'pagar débito', 'posso', 'posso emitir', 'residenciais', 'residenciais no', 'segunda',
'segunda via', 'um', 'um acordo', 'via', 'via boleto', 'via fatura']


# 1 - Qual o impacto da remoção de stopwords no tamanho do vocabulário do modelo?

      O impacto é uma maior filtragem para facilitar o entedimento das frases e evitar palavras fúteis que não iriam agregar na
      predição do bot.

# 2 - O que significa a configuração ngram_range=(1, 2) no TfidfVectorizer?

    Significado é a ajunção das palavras a cada uma palavra (exemplo: "segunda" e "via", juntando as duas facilita o entedimento de
    "segunda via" levando a predição correta.

# 3 - Como a remoção de palavras genéricas ajuda a evitar classificações incorretas?

    Ajuda a evitar palavras desnecessárias para um entedimento mais claro do que o cliente gostaria, no exemplo de retirar palavras genéricas
    como "por favor" ou "urgente" que poderia até impactar negativamente na predição correta.


#========== PRODUÇÃO DO RELATÓRIO:==============

--- RESULTADOS DO LAB 02 (AULA 03) ---

--- Relatório de Classificação ---
                     precision    recall  f1-score   support

horario_atendimento       0.50      1.00      0.67         1
        localizacao       0.00      0.00      0.00         1
    troca_devolucao       0.00      0.00      0.00         1

           accuracy                           0.33         3
          macro avg       0.17      0.33      0.22         3
       weighted avg       0.17      0.33      0.22         3

--- Matriz de Confusão ---
[[1 0 0]
 [1 0 0]
 [0 1 0]]



# 1 - O que representam as métricas Precision, Recall e F1-Score no relatório?
      
     PRECISION: De todas as 2 vezes que o modelo disse que era uma dessas classes (horario, localizacao ou troca) quantas vezes ele acertou, nesse
     caso acertou 1 de 2 ou seja 50%.
     RECALL: De todo o dataset como exemplo reais, quantos o modelo conseguiu capturar, no caso existia apenas um exemplo e ele conseguiu acertar
     de primeira fazendo o 100%.
     F1-Score: É uma média de acertos entre Precision e Recall dando um resultado unico para equilibrio, nesse caso pontuou 67%.
      

# 2 - Como interpretar a diagonal principal da Matriz de Confusão?

      A matriz mostra exatamente onde houve o acerto e ela se confundiu, seguindo ordem das linhas e colunas, neste exemplo o predito pelo modelo
      na linha 1, o unico exemplo de horario foi predito como horario e acertou, nas demais houve um exemplo real de localização e troca e ambas
      foram preditas incorretamente.
      

# 3 - Por que a acurácia isolada pode ser enganosa quando temos classes desbalanceadas?

      Porque a acurácia isolada quando temos classes que foram passados mais conjunto de dados de treinos que uma outra, acaba prejudicando a
      dedução do modelo, nesse caso foi pelo tamanho curto de amostra 3 dados no total, sendo um conjunto muito pequeno ele pode causar um vicio
      na predição.


#========== PRODUÇÃO DO RELATÓRIO:==============
# 1 - Cole o código corrigido e a acurácia obtida.
      
            dados_rh = {
          'mensagem': [
              'Como solicitar minhas ferias?', 'Quero agendar meu periodo de ferias',
              'Onde baixo meu holerite do mes?', 'Preciso do comprovante de rendimentos',
              'Como cadastrar meu atestado medico?', 'Onde envio o atestado de consulta?'
          ],
          'intencao': [
              'solicitar_ferias', 'solicitar_ferias',
              'obter_holerite', 'obter_holerite',
              'enviar_atestado', 'enviar_atestado'
          ]
      }
      
      df3 = pd.DataFrame(dados_rh)
      
      # TODO 1: Separe o dataset em X ('mensagem') e y ('intencao')
      X = df3['mensagem']
      y = df3['intencao']
      
      # TODO 2: Realize o train_test_split com test_size=0.33 e random_state=42
      X_train, X_test, y_train, y_test = train_test_split(df3['mensagem'], df3['intencao'], test_size=0.33, random_state=42)
      
      # TODO 3: Monte o Pipeline encapsulando o TfidfVectorizer e a LogisticRegression
      pipeline = Pipeline([
           ('vectorizer', TfidfVectorizer(stop_words=['de', 'o', 'meu', 'minhas', 'como', 'onde', 'do', 'quero', 'preciso'], ngram_range=(1,2))),
           ('classifier', LogisticRegression())
       ])
      
      # TODO 4: Treine o pipeline completo com .fit() usando os dados de treino brutos
      pipeline.fit(X_train, y_train)
      
      # TODO 5: Faca a predicao nos dados de teste brutos e exiba a acuracia
      predicoes = pipeline.predict(X_test)
      print(f"Acuracia via Pipeline: {accuracy_score(y_test, predicoes) * 100:.2f}%")
      
            [2]
      0s
      dados_rh = {
          'mensagem': [
              'Como solicitar minhas ferias?', 'Quero agendar meu periodo de ferias',
              'Onde baixo meu holerite do mes?', 'Preciso do comprovante de rendimentos',
              'Como cadastrar meu atestado medico?', 'Onde envio o atestado de consulta?'
          ],
          'intencao': [
              'solicitar_ferias', 'solicitar_ferias',
              'obter_holerite', 'obter_holerite',
              'enviar_atestado', 'enviar_atestado'
      …
      # TODO 5: Faca a predicao nos dados de teste brutos e exiba a acuracia
      predicoes = pipeline.predict(X_test)
      print(f"Acuracia via Pipeline: {accuracy_score(y_test, predicoes) * 100:.2f}%")
      


 Acuracia via Pipeline: 0.00%


# 2 - Qual é a grande vantagem de utilizar o objeto Pipeline no Scikit-Learn?

      Porque ele centraliza todas as etapas de transformação de texto e o modelo de ML em um único bloco de código estruturado, tirando a necessidade
      de aplicar processos manuais e repetitivos em dados de treino e teste.
      
# 3 - Por que o Pipeline evita que erros de pré-processamento ocorram entre treino e teste?
      
      Porque ele garante isolamento entre os conjuntos de dados e impede que informações do conjunto de teste influenciem o ajuste do
      pré-processamento durante a fase do treino, evitando que o modelo tenha contato prévio com o padrão de dados de validação.
      
# Todos os resultados devem ser inseridos no arquivo resultados_aula03.md
#========== FIM ==============


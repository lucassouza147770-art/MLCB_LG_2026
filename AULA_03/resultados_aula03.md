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


# Todos os resultados devem ser inseridos no arquivo resultados_aula03.md
#========== FIM ==============


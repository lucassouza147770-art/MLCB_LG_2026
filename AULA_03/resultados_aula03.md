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


# Todos os resultados devem ser inseridos no arquivo resultados_aula03.md
#========== FIM ==============

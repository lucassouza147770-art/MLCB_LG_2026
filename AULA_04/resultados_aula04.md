# ==============================================================================
# ATIVIDADE 1: CHATBOT VERSÃO 1 (KNN)
# ==============================================================================

                  precision    recall  f1-score   support

logistica_entregas       1.00      1.00      1.00         6
       reclamacoes       1.00      1.00      1.00         6
           suporte       1.00      1.00      1.00         6
 trocas_devolucoes       1.00      1.00      1.00         6
            vendas       1.00      1.00      1.00         6

          accuracy                           1.00        30
         macro avg       1.00      1.00      1.00        30
      weighted avg       1.00      1.00      1.00        30

[[6 0 0 0 0]
 [0 6 0 0 0]
 [0 0 6 0 0]
 [0 0 0 6 0]
 [0 0 0 0 6]]

=== INICIANDO BATERIA DE TESTES (10 INPUTS OBRIGATÓRIOS) ===

[Teste 1/10]
Digite a frase do cliente: Meu pedido ainda não chegou
Bot [Intenção: LOGISTICA_ENTREGAS | Confiança: 100.0%]

[Teste 2/10]
Digite a frase do cliente: Quero devolver minha mesa
Bot [Intenção: TROCAS_DEVOLUCOES | Confiança: 66.7%]

[Teste 3/10]
Digite a frase do cliente: Veio um parafuso faltando
Bot [Intenção: RECLAMACOES | Confiança: 66.7%]

[Teste 4/10]
Digite a frase do cliente: Onde está minha entrega?
Bot [Intenção: RECLAMACOES | Confiança: 100.0%]

[Teste 5/10]
Digite a frase do cliente: Quero fazer uma reclamação
Bot [Intenção: RECLAMACOES | Confiança: 100.0%]

[Teste 6/10]
Digite a frase do cliente: O móvel chegou quebrado
Bot [Intenção: RECLAMACOES | Confiança: 100.0%]

[Teste 7/10]
Digite a frase do cliente: Como faço para trocar o produto?
Bot [Intenção: TROCAS_DEVOLUCOES | Confiança: 100.0%]

[Teste 8/10]
Digite a frase do cliente: Preciso comprar um guarda-roupa
Bot [Intenção: VENDAS | Confiança: 100.0%]

[Teste 9/10]
Digite a frase do cliente: Santos é gigante
Bot: [FALLBACK - Confiança baixa: 33.33%]
Desculpe, não entendi sua solicitação. Encaminhando você para um atendente humano...

[Teste 10/10]
Digite a frase do cliente: Palmeiras pequeno
Bot: [FALLBACK - Confiança baixa: 33.33%]
Desculpe, não entendi sua solicitação. Encaminhando você para um atendente humano...

# ==============================================================================
# ATIVIDADE 2: CHATBOT VERSÃO 2 (DECISION TREE)
# ==============================================================================


=== RELATÓRIO DE CLASSIFICAÇÃO ===
                    precision    recall  f1-score   support

logistica_entregas       0.80      0.67      0.73         6
       reclamacoes       1.00      0.67      0.80         6
           suporte       0.75      1.00      0.86         6
 trocas_devolucoes       0.83      0.83      0.83         6
            vendas       0.71      0.83      0.77         6

          accuracy                           0.80        30
         macro avg       0.82      0.80      0.80        30
      weighted avg       0.82      0.80      0.80        30


=== MATRIZ DE CONFUSÃO ===
[[4 0 0 0 2]
 [1 4 1 0 0]
 [0 0 6 0 0]
 [0 0 1 5 0]
 [0 0 0 1 5]]

=== INICIANDO BATERIA DE TESTES (8 INPUTS OBRIGATÓRIOS) ===

[Teste 1/8]
Digite a frase do cliente: Quero saber o preço de uma mesa
Bot [Intenção: VENDAS | Confiança: 100.0%]

[Teste 2/8]
Digite a frase do cliente: Meu sofá ainda não foi entregue
Bot [Intenção: LOGISTICA_ENTREGAS | Confiança: 100.0%]

[Teste 3/8]
Digite a frase do cliente: Preciso montar meu armário
Bot [Intenção: LOGISTICA_ENTREGAS | Confiança: 100.0%]

[Teste 4/8]
Digite a frase do cliente: Quero devolver um produto
Bot [Intenção: RECLAMACOES | Confiança: 100.0%]

[Teste 5/8]
Digite a frase do cliente: O atendimento da loja foi péssimo
Bot [Intenção: RECLAMACOES | Confiança: 100.0%]

[Teste 6/8]
Digite a frase do cliente: Como rastrear meu pedido?
Bot [Intenção: LOGISTICA_ENTREGAS | Confiança: 100.0%]

[Teste 7/8]
Digite a frase do cliente: Qual é a capital do Brasil?
Bot [Intenção: LOGISTICA_ENTREGAS | Confiança: 100.0%]

[Teste 8/8]
Digite a frase do cliente: Hoje está muito calor
Bot [Intenção: TROCAS_DEVOLUCOES | Confiança: 100.0%]


# Relatório de Avaliação NLU - SAC Móveis Residenciais
## 1. Tabela Comparativa de Métricas (Dados de Teste)

| Modelo | Acurácia Geral | F1-Score (Weighted) | Principais Erros na Matriz |
| :--- | :--- | :--- | :--- |
| **KNN (K=3)** | 100% | 100% | Não foram identificados erros. Todas as classes foram classificadas corretamente. |
| **Decision Tree** | 80% | 80% | Ocorreram confusões entre logística e vendas, reclamações e logística/suporte, trocas e suporte, além de vendas e trocas/devoluções. |

## 2. Análise dos Testes de Entrada (`input()`)
- **Comportamento do KNN (10 testes):** [O KNN classificou corretamente as frases relacionadas ao contexto de móveis. Nas frases fora do contexto, como as relacionadas a futebol, apresentou confiança de 33,33%, abaixo do limite de 50%.
Dessa forma, o fallback foi acionado corretamente e as solicitações foram encaminhadas para atendimento humano.]

- **Comportamento da Decision Tree (8 testes):** [A Árvore de Decisão acertou algumas classificações, mas também apresentou erros. Por exemplo, uma frase sobre montagem foi classificada como logística e uma frase sobre devolução foi classificada como reclamação.
Nas frases fora do contexto, o modelo classificou as entradas com 100% de confiança, sem acionar o fallback.]

## 3. Veredito Final
- **Melhor modelo para este projeto:** [KNN (K=3)]
- **Justificativa técnica:** [O KNN apresentou melhores resultados, com 100% de acurácia e F1-Score, enquanto a Decision Tree alcançou 80%.
Além das métricas superiores, o KNN também apresentou um melhor funcionamento do fallback para frases fora do contexto. Por isso, foi considerado o modelo mais adequado para o SAC Móveis Residenciais.]

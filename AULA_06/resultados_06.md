# Resultados Aula 06

## Demo - aula06_mlcb.ipynb

Fiz 4 testes com frases diferentes no google colab notebook.

### Teste 1

Frase:
`quero comprar uma casa`

Resultado:

```text
Intenção: comprar_imovel
Confiança: 100.0%
Status: IDENTIFICADO (comprar_imovel)
```

<img width="1230" height="495" alt="image" src="https://github.com/user-attachments/assets/d5411054-1939-46af-909b-b73691258724" />


### Teste 2

Frase:
`preciso alugar um apartamento`

Resultado:

```text
Intenção: alugar_imovel
Confiança: 100.0%
Status: IDENTIFICADO (alugar_imovel)
```

### Teste 3

Frase:
`estou com vazamento no banheiro`

Resultado:

```text
Intenção: suporte_manutencao
Confiança: 100.0%
Status: IDENTIFICADO (suporte_manutencao)
```

### Teste 4

Frase:
`não recebi meu boleto`

Resultado:

```text
Intenção: 2via_boleto_contrato
Confiança: 100.0%
Status: IDENTIFICADO (2via_boleto_contrato)
```

---

## LAB 01

Nesse laboratório troquei o algoritmo de Regressão Logística pela Árvore de Decisão.

No notebook apareceu:

```text
Dataset carregado com 20 mensagens divididas em 4 intenções.
Modelo supervisionado treinado!
```

Fiz alguns testes no Gradio.

Frase:
`quero comprar uma casa`

Resultado:

```text
Intenção: comprar_imovel
Confiança: 100.0%
```

Outro teste:

`preciso de ajuda com um vazamento`

Resultado:

```text
Intenção: suporte_manutencao
Confiança: 100.0%
```

A interface continuou funcionando normalmente.

---

## LAB 02

Nesse laboratório aumentei o limite de confiança de 50% para 65%.

Ficou assim:

```text
LIMIAR_CONFIANCA = 0.65
```

Teste:

`quero alugar uma casa`

Resultado:

```text
Intenção: alugar_imovel
Confiança: 100.0%
Status: IDENTIFICADO (alugar_imovel) - Corte de confiança: 65%
```

Também testei uma frase que não tinha muito a ver com o sistema:

`quero comprar um carro`

Nesse caso o modelo pode tentar encaixar a frase em alguma classe, mas se a confiança ficar abaixo de 65%, entra no fallback.

---

## LAB 03

Aqui foi adicionada uma nova intenção:

`cancelar_contrato`

Coloquei 5 frases de exemplo para o treinamento.

Algumas delas foram:

```text
quero cancelar meu contrato
como faço para cancelar o contrato
quero encerrar meu contrato
preciso cancelar o contrato de aluguel
gostaria de cancelar meu contrato
```

Depois do treinamento:

```text
Dataset carregado com 25 mensagens divididas em 5 intenções.
Modelo supervisionado treinado!
```

Fiz o teste:

`quero cancelar meu contrato`

Resultado:

```text
Intenção: cancelar_contrato
Confiança: 100.0%
Status: IDENTIFICADO (cancelar_contrato) - Corte de confiança: 65%
```

A nova classe foi reconhecida pelo modelo e apareceu normalmente na interface.

---

## Resumindo

No LAB 01 troquei o classificador para Decision Tree.

No LAB 02 aumentei o limite para 65%.

No LAB 03 coloquei a nova classe `cancelar_contrato` e testei no Gradio.

Tudo foi feito no `.ipynb`.


# Discretização de Controladores PI e PID: Da Teoria à Implementação

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SEU_USUARIO_GITHUB/NOME_DO_SEU_REPOSITORIO/blob/main/PID_discreto.ipynb)

Este repositório contém um Jupyter Notebook (`PID_discreto.ipynb`) que serve como um guia detalhado para a discretização de controladores Proporcional-Integral (PI) e Proporcional-Integral-Derivativo (PID).

## Objetivo Principal

O objetivo deste notebook é demonstrar formalmente o processo de conversão de um controlador analógico ideal, definido no domínio de Laplace $H(s)$, para sua forma digital equivalente no domínio Z, $H(z)$.

O foco final é derivar a **Equação de Diferenças** ($y[k]$), que é o algoritmo exato necessário para implementar o controlador em um sistema embarcado (como um microcontrolador) ou em qualquer software de controle em tempo discreto.

## Conteúdo do Notebook

O notebook é dividido em três capítulos principais:

### 1. Controlador PI
Detalha a derivação da função de transferência $H(z)$ e da equação de diferenças $y[k]$ para um controlador PI ideal usando três métodos de aproximação distintos.

### 2. Controlador PID
Expande a análise para o controlador PID "ideal". Este capítulo inclui uma discussão importante sobre por que um PID "puro" não pode ser implementado usando o método *Forward Euler* (devido a um termo derivativo não-causal) e como os outros métodos lidam com isso.

### 3. Simulação (Python)
Utiliza as bibliotecas `control`, `numpy` e `matplotlib` para:
1.  Simular e comparar a resposta ao degrau de um sistema de malha fechada controlado por um PI discretizado pelos três métodos, demonstrando a instabilidade do *Forward Euler*.
2.  Implementar a equação de diferenças do PID (derivada no Cap. 2) em Python puro.
3.  Simular um PID "Real" (com filtro derivativo) para uma comparação justa, já que o PID ideal é impróprio.

## Métodos de Discretização Abordados

Para cada tipo de controlador (PI e PID), as seguintes "regras de substituição" de $s \to z$ são analisadas e comparadas:

* **Backward Euler (Euler Implícito):** `s = (1 - z⁻¹) / T`
* **Forward Euler (Euler Explícito):** `s = (z - 1) / T`
* **Tustin (Transformação Bilinear):** `s = (2/T) * (1 - z⁻¹) / (1 + z⁻¹)`

## Como Utilizar

### Pré-requisitos

Para executar as simulações no notebook (localmente), você precisará de Python e das seguintes bibliotecas:

* Jupyter Notebook (ou Jupyter Lab)
* NumPy
* Matplotlib
* Python Control Systems Library

Você pode instalar as bibliotecas necessárias via pip:
```bash
pip install numpy matplotlib control

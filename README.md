Calculadora de IMC
Este repositório contém uma aplicação web interativa para calcular o Índice de Massa Corporal (IMC) usando Streamlit. A aplicação permite que os usuários insiram seu peso e altura para calcular o IMC e classificar o resultado em diferentes categorias de saúde.

Funcionalidades
Entrada de Dados: Permite que os usuários insiram seu peso e altura.
Cálculo do IMC: Calcula o IMC com base nos dados inseridos.
Classificação do IMC: Classifica o IMC em categorias como “Abaixo do peso”, “Peso ideal”, “Sobrepeso”, “Obesidade” e “Obesidade Mórbida”.
Exibição de Resultados: Mostra os resultados do IMC calculado e a diferença em relação ao IMC ideal.
Interface Intuitiva: Utiliza Streamlit para criar uma interface web amigável e interativa.
Como Usar
Instale o Streamlit:
pip install streamlit

Clone este repositório:
git clone https://github.com/seu-usuario/calculadora-imc.git
cd calculadora-imc

Execute a aplicação:
streamlit run app.py

Insira seus dados:
Digite seu peso e altura nos campos fornecidos.
Clique no botão “Calcular” para ver os resultados.
Exemplo de Código
Python

import streamlit as st

with st.sidebar:
    st.title("Calculadora IMC")
    st.header("IMC: Definição: ")
    st.write("Índice de Massa Corporal (IMC)")
    st.write("É um índice que relaciona o peso e a altura de uma pessoa")
    st.write("É utilizado como uma medida de saúde geral e para determinar se uma pessoa está em um peso saudável para sua altura")

st.title("Calculadora IMC")

peso = st.number_input(label="Digite seu peso", min_value=0.0)
altura = st.number_input(label="Digite seu altura", min_value=0.0)

if st.button("Calcular"):
    imc = peso/(altura ** 2)
    imc_ideal = 21.7
    imc_delta = imc - imc_ideal

    if imc < 18.5:
        resultado = {"classe": 'Abaixo do peso', "delta": imc_delta}
    elif 18.5 <= imc < 25:
        resultado = {"classe": 'Peso ideal', "delta": imc_delta}
    elif imc <= 40:
        resultado = {"classe": 'Sobrepeso', "delta": imc_delta}
    elif imc <= 40:
        resultado = {"classe": 'Obesidade', "delta": imc_delta}
    else:
        resultado = {"classe": 'Obesidade Mórbida', "delta": imc_delta}

    col1, col2 = st.columns(2)
    col1.metric("IMC Classificado", resultado["classe"], resultado["delta"], delta_color="inverse")
    col2.metric("IMC Calculado", imc, delta_color="off")
    col3 = st.code(f"IMC ideal: {imc_ideal}")

    st.divider()
    st.text("Fonte")
    st.image("./IMC.png")
Código gerado por IA. Examine e use com cuidado. Mais informações em perguntas frequentes.
Contribuições
Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests para melhorias e correções.

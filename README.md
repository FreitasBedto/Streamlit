import streamlit as st
import pandas as pd
import numpy as np
import os
import time

# Configuração da página
st.set_page_config(page_title="Python para Tudo", layout="wide")

# Título principal
st.title("Python para Tudo: Automação, Data Science e DevOps")

# Criação de abas
abas = st.tabs(["Automação de Tarefas", "Análise de Dados", "Práticas de DevOps"])

# Aba de Automação
with abas[0]:
    st.header("Automação de Tarefas")
    st.write("Explore funcionalidades para automatizar tarefas repetitivas.")
    
    diretorio = st.text_input("Digite o caminho do diretório para listar arquivos:", ".")
    if st.button("Listar Arquivos"):
        try:
            arquivos = os.listdir(diretorio)
            st.write(f"Arquivos no diretório {diretorio}:")
            st.write(arquivos)
        except FileNotFoundError:
            st.error("Diretório não encontrado. Verifique o caminho informado.")

# Aba de Análise de Dados
with abas[1]:
    st.header("Análise de Dados")
    st.write("Veja uma demonstração de análises de dados gerados automaticamente.")
    
    # Gerar dados fictícios
    df = pd.DataFrame(
        np.random.randn(100, 4),
        columns=["A", "B", "C", "D"]
    )
    
    st.write("Tabela de Dados:")
    st.dataframe(df)
    
    st.write("Gráficos de Linha e Barras:")
    st.line_chart(df)
    st.bar_chart(df)

# Aba de Práticas de DevOps
with abas[2]:
    st.header("Práticas de DevOps")
    st.write("Simulação de monitoramento e logs de processos.")

    if st.button("Iniciar Processo de Deploy Simulado"):
        st.write("Iniciando deploy...")
        for i in range(101):
            st.progress(i)
            time.sleep(0.05)
        st.success("Deploy concluído com sucesso!")

    st.write("Exemplo de Logs Recentes:")
    st.code("""
    [INFO] 2024-12-09 12:00:00: Deploy iniciado.
    [INFO] 2024-12-09 12:01:00: Configurações aplicadas.
    [INFO] 2024-12-09 12:02:00: Verificação concluída.
    [INFO] 2024-12-09 12:03:00: Deploy finalizado.
    """)

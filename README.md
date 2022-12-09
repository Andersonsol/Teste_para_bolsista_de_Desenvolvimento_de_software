# Teste para bolsista de Desenvolvimento de software: 
### Bem vindo ao teste para bolsista de iniciação científica em desenvolvimento de software do Laboratório Analítico de Competências Moleculares e Epidemiológicas (ACME Labs) da Fiocruz Ceará.


Para realizar este teste, será necessário você ler o problema e resolvê-lo através da criação de um simples e funcional algoritmo.

NOTA: Todos os dados usados neste teste são fictícios, portanto, está de acordo com a Lei Geral de Proteção de Dados.

Após você conseguir ingressar em um laboratório de renome da Fiocruz, você agora participa de uma pesquisa que já estava em andamento.

Essa pesquisa possui um vasto banco de dados relacional desenvolvido em em PostgreSQL.

Além disso, a equipe de desenvolvimento criou uma API simples, com alguns endpoints, para que os desenvolvedores e analistas possam ter acesso aos dados, sem comprometer a segurança.

Essa pesquisa em questão, coletou alguns dados dos participantes, incluindo nome, email e telefone de contato. Além disso, a pesquisa possui um número de telefone para que os participantes possam enviar sms e, assim, entrar em contato.

Foi solicitado a sua pessoa que disponibilizasse uma LISTA com o email dos participantes que enviaram sms para a pesquisa a partir de 1 de novembro de 2022.
* Desenvolver um algoritmo que retorne uma lista com os emails de contato dos participantes que enviaram sms a partir de 1 de novembro de 2022.

### Informações úteis

* Nem todas as pessoas que enviaram SMS para a pesquisa são participantes. É possível, inclusive, que nenhum participante tenha enviado SMS no período informado.

* Endpoint para resgatar as informações dos participantes da pesquisa: https://profound-yew-370516.ue.r.appspot.com/participantes (key = 'estoutentandosairdazonadeconforto')
   
* Endpoint para resgatar as informações dos participantes que enviaram SMS para a pesquisa: https://profound-yew-370516.ue.r.appspot.com/sms/recebidos (key = 'eunaotenhoideiadoquemeesperanafiocruz')

* As requisições às endpoints devem utilizar o método post e incluir o parametro key com a chave em questão.

* Os números de telefones dos participantes podem não estar formatados igualmente nos dois endpoints

* É possível utilizar a biblioteca pandas, do python, para ler os retornos das requisições e transformá-los em dataframes. Também é possível realizar JOINs entre dataframes no pandas.

#### Referências

* https://docs.python.org/3/tutorial/datastructures.html
* https://requests.readthedocs.io/en/latest/
* https://pandas.pydata.org/docs/reference/api/pandas.read_json.html
* https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.join.html
* https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.replace.html
* https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.str.removeprefix.html

#!pip install pandas
#para instalar a biblioteca pandas, remova o comentario acima e execute este bloco

# Início do código

Você pode usar quantas funções e blocos de código achar necessário, portanto que exista uma função chamada get_lista_de_emails que retornará a lista de emails solicitada no problema.

def get_lista_de_emails():
    #lista_de_emails deve ser a lista de emails, tipo list, dos participantes que enviaram sms a partir de 1 de novembro de 2022.
    return lista_de_emails
    
# Resposta do Teste
    
    print(type(get_lista_de_emails()) == list)
print(get_lista_de_emails())
    

# Download the helper library from https://www.twilio.com/docs/python/install
import os
from twilio.rest import Client


# Find your Account SID and Auth Token at twilio.com/console
# and set the environment variables. See http://twil.io/secure
account_sid = os.environ['TWILIO_ACCOUNT_SID']
auth_token = os.environ['TWILIO_AUTH_TOKEN']
client = Client(account_sid, auth_token)

message = client.messages \
    .create(
         body='McAvoy or Stewart? These timelines can get so confusing.',
         from_='+15017122661',
         status_callback='http://postb.in/1234abcd',
         to='+15558675310'
     )

print(message.sid)

from flask import Flask, request
import logging

logging.basicConfig(level=logging.INFO)

app = Flask(__name__)


@app.route("/MessageStatus", methods=['POST'])
def incoming_sms():
    message_sid = request.values.get('MessageSid', None)
    message_status = request.values.get('MessageStatus', None)
    logging.info('SID: {}, Status: {}'.format(message_sid, message_status))

    return ('', 204)


if __name__ == "__main__":
    app.run(debug=True)


/* Além disso vamos precisar de uma biblioteca pyodbc que vai permitir essa integração do Python com bancos de dados.

Para instalar uma biblioteca basta ir até o terminal e escrever pip install pyodbc.

Aqui nós vamos começar o código que vamos utilizar para fazer essa integração.*/


import pyodbc

dados_conexao = (
    "Driver={PostgreSQL Server};"
    "Server= MacBookAnderson.local;"
    "Database=PythonSQL;"
)
/* Esse código vai permitir com que você faça a conexão com o banco de dados. Para garantir que funcionou precisamos criar essa conexão.*/
conexao = pyodbc.connect(dados_conexao)
print("Conexão Bem Sucedida") 


/* Com isso vamos verificar se está tudo correto, se estiver seguido o passo a passo corretamente você vai ter esse print da conexão bem-sucedida.*/ 

cursor = conexao.cursor()

/*Importante: Nessa parte é importante que você tenha um breve conhecimento em SQL para que possa escrever seus códigos para dar comandos ao SQL, pois como a programação é feita nessa linguagem é necessário que você saiba para poder criar os comandos que precisa.*/

import pandas as pd

# Biblioteca NumPy -  manipular com dados numéricos em Python
import numpy as np
/* Você pode instalar o Pandas pontualmente, mas caso tenha instalado o Python através do Anaconda, conforme indicamos, ele já será instalado juntamente com a linguagem, sendo que só nos resta realizar a importação nos scripts onde o pacote for utilizado.*/


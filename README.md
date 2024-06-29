# Desafio Dio - Integrando Python com SQLite e MongoDB



Neste projeto, integraremos Python com dois bancos de dados populares: SQLite e MongoDB. Vamos criar um aplicativo simples que permita aos usuários gerenciar contatos, armazenando-os em ambos os bancos de dados.



### **Pré-requisitos**

- Python 3 ou superior
- SQLite
- MongoDB
- Editor de código (como Visual Studio Code ou Sublime Text)



### **Passos**



### **1. Criar um Banco de Dados SQLite**

- Abra o Terminal ou Prompt de Comando.

- Crie um novo banco de dados SQLite chamado `contatos.db`:

  

plaintext



```plaintext
sqlite3 contatos.db
```



- Crie uma tabela chamada `contatos` no banco de dados:



sql



```sql
CREATE TABLE contatos (
  id INTEGER PRIMARY KEY,
  nome TEXT,
  email TEXT,
  telefone TEXT
);
```



### **2. Conectar-se ao Banco de Dados SQLite**



- No seu editor de código, importe o módulo `sqlite3`.

- Estabeleça uma conexão com o banco de dados SQLite:

  

python



```python
import sqlite3

conn = sqlite3.connect('contatos.db')
cursor = conn.cursor()
```



### **3. Inserir Dados no Banco de Dados SQLite**



- Prepare uma consulta SQL para inserir dados na tabela `contatos`:

python



```python
query = """
INSERT INTO contatos (nome, email, telefone)
VALUES (?, ?, ?)
"""
```



- Execute a consulta, passando os valores dos contatos como parâmetros:

python



```python
cursor.execute(query, (nome, email, telefone))
```



### **4. Conectar-se ao Banco de Dados MongoDB**



- Importe o módulo `pymongo`.
- Estabeleça uma conexão com o banco de dados MongoDB:

python



```python
import pymongo

client = pymongo.MongoClient('localhost', 27017)
db = client.contatos
```



### **5. Inserir Dados no Banco de Dados MongoDB**



- Prepare um documento JSON para inserir dados na coleção `contatos`:

python



```python
contato = {
  "nome": nome,
  "email": email,
  "telefone": telefone
}
```



- Insira o documento na coleção:

python



```python
db.contatos.insert_one(contato)
```



### **6. Consultar Dados dos Bancos de Dados**

- #### **SQLite:**

python



```python
query = """
SELECT * FROM contatos
WHERE nome = ?
"""

cursor.execute(query, (nome,))

for contato in cursor.fetchall():
  print(contato)
```



- #### **MongoDB:**

python



```python
for contato in db.contatos.find({"nome": nome}):
  print(contato)
```



### **7. Fechar as Conexões**



- Feche as conexões com os bancos de dados SQLite e MongoDB:

python



```python
cursor.close()
conn.close()
client.close()
```



### **Conclusão**

Neste projeto, integramos Python com SQLite e MongoDB com sucesso. Criamos um aplicativo simples que permite gerenciar contatos, armazenando-os em ambos os bancos de dados. Isso demonstra o poder da integração de Python com diferentes tecnologias de banco de dados.

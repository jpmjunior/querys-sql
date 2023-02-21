# Consultas básicas em SQL

## Diagrama Entidade-Relacionamento de uma banco de dados de um blog de nóticias
![DER](https://github.com/jpmjunior/querys-sql/blob/main/der-blog-noticias.jpeg?raw=true)

##
#### Consulta envolvendo as tabelas mnoticia, mparagrafo e marquivo
```sql
Select
n.titulo, n.datahora_publicacao, p.titulo, p.descricao, a.url
From
mnoticia n, mparagrafo p,  marquivo a
where
n.id = p.noticia_id and p.id = a.paragrafo_id
```
## 
#### Posso ainda envoler a tabela usuário.
```sql
Select
n.titulo, n.datahora_publicacao, p.titulo, p.descricao, a.url, u.nome
From
mnoticia n, mparagrafo p,  marquivo a, musuario u
where
n.id = p.noticia_id and p.id = a.paragrafo_id and u.id = n.usuario_id
```
## 
#### Se eu quisesse filtrar pelas notícias publicadas pelo usuário Fábio...
```sql
Select
n.titulo, n.datahora_publicacao, p.titulo, p.descricao, a.url, u.nome
From
mnoticia n, mparagrafo p,  marquivo a, musuario u
where
n.id = p.noticia_id and p.id = a.paragrafo_id and u.id = n.usuario_id and u.nome ='Fabio'
```
## 
#### Se eu quisesse filtrar pelas notícias publicadas pelo usuário Fábio e as notícias publicadas a partir de janeiro de 2023...
```sql
Select
n.titulo, n.datahora_publicacao, p.titulo, p.descricao, a.url, u.nome
From
mnoticia n, mparagrafo p,  marquivo a, musuario u
where
n.id = p.noticia_id and p.id = a.paragrafo_id and u.id = n.usuario_id and u.nome ='Fabio' and n.datahora_publicacao > '01-01-2023'
```
## 
#### Se eu quisesse filtrar pelas notícias publicadas pelo usuário Fábio, as notícias publicadas a partir de janeiro de 2023 e parágrafos que tenha no nome a palavra Principal...
```sql
Select
n.titulo, n.datahora_publicacao, p.titulo, p.descricao, a.url, u.nome
From
mnoticia n, mparagrafo p,  marquivo a, musuario u
where
n.id = p.noticia_id and p.id = a.paragrafo_id and u.id = n.usuario_id and u.nome ='Fabio' and n.datahora_publicacao > '01-01-2023' and p.titulo like '%Paragrafo%'
```
## 
#### Se eu quisesse filtrar pelas notícias publicadas pelo usuário Fábio, as notícias publicadas a partir de janeiro de 2023, parágrafos que tenha no nome a palavra Principal e liste somente os arquivos que o Pinheiro fez upload.
```sql
Select
n.titulo, n.datahora_publicacao, p.titulo, p.descricao, a.url, u.nome
From
mnoticia n, mparagrafo p,  marquivo a, musuario u, musuario u2
where
n.id = p.noticia_id and p.id = a.paragrafo_id and u.id = n.usuario_id and u.nome ='Fabio' and n.datahora_publicacao > '01-01-2023' and p.titulo like '%Paragrafo%' and u2.id = a.uploader_id and u2.nome = 'Pinheiro'
```

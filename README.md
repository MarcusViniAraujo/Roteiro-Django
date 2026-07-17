# 🚀 Django + Tailwind CSS: Relacionamentos Muitos-para-Muitos (N:N) e Shell ORM

Este repositório contém a quarta etapa do projeto `demo-django`. O objetivo desta fase foi compreender e implementar um relacionamento de **Muitos-para-Muitos (N:N)** no banco de dados utilizando o Django ORM, além de manipular os dados diretamente através do ambiente interativo do Django Shell.

O projeto continua rodando de forma isolada e simplificada dentro de containers **Docker**.

---

## 🛠️ Tecnologias Utilizadas

- **Framework Web:** Django (Python)
- **Banco de Dados:** SQLite
- **Estilização:** Tailwind CSS (via CDN)
- **Ambiente:** Docker & Docker Compose

---

## 📸 Screenshots

### Página Inicial

![Página Inicial](demo-django/imagens/image1.png)

_Visualização das mensagens e suas respectivas tags._

---

### Gerenciamento de Tags no Admin

![Tags no Admin](demo-django/imagens/image3.png)

_Cadastro e manutenção das tags através do Django Admin._

---

### Associação de Tags às Mensagens

![Relacionamento N](demo-django/imagens/image2.png)

_Interface com `filter_horizontal` para facilitar a associação entre mensagens e tags._

---

_Manipulação dos relacionamentos N:N diretamente pelo ORM._

---

## 🧠 O Que Foi Aprendido Nesta Etapa

- **Modelagem Muitos-para-Muitos (N:N):** criação do model `Tag` e sua associação com o model `Mensagem` usando o campo `ManyToManyField`.
- **Tabelas intermediárias (tabelas de junção):** compreensão de como o Django gerencia automaticamente a tabela pivô (`home_mensagem_tags`) para conectar registros de ambas as tabelas.
- **Campos específicos (`SlugField`):** utilização de slugs para garantir URLs amigáveis e padronizadas.
- **Otimização do Django Admin:** uso da propriedade `filter_horizontal` para melhorar a experiência de seleção de múltiplos registros relacionados.
- **Renderização dinâmica de coleções:** utilização do laço `{% for tag in m.tags.all %}` para exibir as tags associadas a cada mensagem.
- **Consultas reversas:** acesso às mensagens relacionadas a partir de uma tag utilizando o `related_name`.

---

## 🚀 Como Executar o Projeto

Certifique-se de ter o **Docker** e o **Docker Compose** instalados em sua máquina.

### 1. Subir o container e iniciar o servidor

Para construir a imagem e iniciar a aplicação, execute:

```bash
docker compose up --build
```

A aplicação estará disponível em:

```text
http://localhost:8000
```

### 2. Gerar e aplicar as migrações

Com o container em execução, abra um novo terminal e execute:

```bash
docker compose run --rm web python manage.py makemigrations
docker compose run --rm web python manage.py migrate
```

### 3. Gerenciar dados pelo Painel Administrativo

Acesse:

```text
http://localhost:8000/admin/
```

No painel administrativo será possível:

- Criar novas tags.
- Editar tags existentes.
- Associar múltiplas tags a uma mesma mensagem.
- Visualizar e gerenciar os relacionamentos N:N.

---

## 🔄 Entendendo o Relacionamento N:N

Neste projeto:

- Uma **Mensagem** pode possuir várias **Tags**.
- Uma **Tag** pode estar associada a várias **Mensagens**.

O Django cria automaticamente uma tabela intermediária para armazenar essas associações, eliminando a necessidade de gerenciar manualmente as chaves estrangeiras.

---

## 💡 Sobre o Projeto

Este projeto faz parte do meu portfólio de estudos em desenvolvimento backend com Python e Django, com foco em modelagem de banco de dados, ORM, Docker e boas práticas de desenvolvimento web.

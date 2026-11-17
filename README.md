# TBLC — The Brasil Lore Collection

> *Quando as lendas se tornam reais.*

**TBLC (The Brasil Lore Collection)** é um site que cataloga criaturas e tradições do folclore brasileiro, organizadas por região do país. A proposta narrativa do projeto é apresentar essas lendas como se fossem registros reais, alertando a população sobre as criaturas e, ao mesmo tempo, funcionando como um acervo cultural sobre os costumes e as tradições do Brasil.

O usuário se cadastra escolhendo a sua região, entra no sistema e navega por um **mapa interativo do Brasil** para explorar o que foi catalogado em cada região.

> ⚠️ **Status:** projeto em desenvolvimento (fase de front-end com servidor Express). Veja a seção [Limitações atuais](#-limitações-atuais).

---

## ✨ Funcionalidades

- **Cadastro** com nome, codinome, e-mail, senha, confirmação de senha e região, com validação no cliente e no servidor.
- **Login** com alternância de visibilidade da senha.
- **Home com mapa interativo do Brasil**: ao clicar em um estado, o usuário é levado à página da região correspondente.
- **Páginas por região**: Norte, Nordeste, Centro-Oeste, Sudeste e Sul.
- Páginas de **Perfil**, **Sobre nós** e **Top Secret**.

## 🧰 Tecnologias

| Camada | Tecnologia |
| --- | --- |
| Servidor | [Node.js](https://nodejs.org/) + [Express 5](https://expressjs.com/) |
| Desenvolvimento | [Nodemon](https://nodemon.io/) |
| Front-end | HTML5, CSS3 e JavaScript puro |
| Ícones | [Font Awesome 7](https://fontawesome.com/) (via CDN) |
| Mapa | [Simplemaps](https://simplemaps.com/) — Country Map (versão trial) |

## 📁 Estrutura do projeto

```
TBLC_projeto/
├── index.js              # Ponto de entrada: configura o Express e registra as rotas
├── package.json
├── users/                # Rotas (uma por página/recurso)
│   ├── cadastro.js
│   ├── login.js
│   ├── home.js
│   ├── regiao.js
│   ├── perfil.js
│   ├── sobreNos.js
│   └── topSecret.js
├── templates/            # Páginas HTML
│   ├── cadastro.html
│   ├── login.html
│   ├── home.html
│   ├── norte.html · nordeste.html · centro_oeste.html · sudeste.html · sul.html
│   ├── regiao.html       # Modelo base de página de região
│   ├── perfil.html · sobreNos.html · topSecret.html
│   └── cadastro_login_imagem/
└── public/               # Arquivos estáticos servidos diretamente
    ├── css/              # Um arquivo de estilo por página
    ├── js/               # cadastro.js, login.js, mapdata.js, countrymap.js
    └── home_regiao_imagem/
```

## 🚀 Como executar

### Pré-requisitos

- [Node.js](https://nodejs.org/) (recomendado: versão LTS atual)
- npm

### Passo a passo

```bash
# 1. Clone o repositório
git clone <url-do-repositório>
cd TBLC_projeto

# 2. Instale as dependências
npm install

# 3. Inicie o servidor (com recarregamento automático via nodemon)
npm start
```

Depois, acesse **http://localhost:3000** no navegador. A raiz (`/`) redireciona automaticamente para a tela de cadastro.

## 🗺️ Rotas

| Método | Rota | Descrição |
| --- | --- | --- |
| `GET` | `/` | Redireciona para `/cadastro` |
| `GET` | `/cadastro` | Formulário de cadastro |
| `POST` | `/cadastro/save` | Recebe o cadastro, valida e redireciona para `/login` |
| `GET` | `/login` | Formulário de login |
| `POST` | `/login/save` | Recebe o login e redireciona para `/home` |
| `GET` | `/home` | Página inicial com o mapa interativo |
| `GET` | `/regioes/norte` | Região Norte |
| `GET` | `/regioes/nordeste` | Região Nordeste |
| `GET` | `/regioes/centro_oeste` | Região Centro-Oeste |
| `GET` | `/regioes/sudeste` | Região Sudeste |
| `GET` | `/regioes/sul` | Região Sul |
| `GET` | `/perfil` | Perfil do usuário |
| `GET` | `/sobreNos` | Sobre o projeto |
| `GET` | `/topSecret` | Página secreta |

## 🚧 Limitações atuais

O projeto ainda está em fase inicial, e alguns pontos estão pendentes:

- **Sem banco de dados:** o cadastro apenas valida os campos e imprime os dados no console do servidor; nada é persistido.
- **Sem autenticação real:** o login não verifica credenciais e não há sessões. Qualquer envio do formulário leva à `/home`.
- **Conteúdo provisório:** as páginas das regiões ainda usam texto *Lorem ipsum* e imagem padrão; `perfil`, `sobreNos` e `topSecret` são páginas de teste.
- **Mapa em versão trial:** a biblioteca do Simplemaps está na versão de avaliação; para uso em produção é necessária uma licença.

## 🛣️ Próximos passos

- [ ] Integrar um banco de dados para armazenar os usuários
- [ ] Implementar autenticação (hash de senhas e sessões/JWT)
- [ ] Preencher as páginas de cada região com as criaturas e tradições catalogadas
- [ ] Construir as páginas de Perfil, Sobre nós e Top Secret
- [ ] Adicionar testes automatizados

## 👥 Autores

- Arthur Gabriel dos Anjos
- Giovana Gonçalves Silva

## 📄 Licença

O `package.json` declara a licença **ISC**. O mapa interativo é de terceiros (Simplemaps) e está sujeito à [licença do fornecedor](https://simplemaps.com/license).

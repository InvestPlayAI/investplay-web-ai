# InvestPlay Website for LLMs

Este projeto hospeda o site da InvestPlay otimizado para LLMs, disponível em: https://ai.investplay.com.br

## Idiomas

Português Brasileiro (padrão): https://ai.investplay.com.br/pt-BR  
English: https://ai.investplay.com.br/en-US

## Uso

- `curl ai.investplay.com.br/pt-BR` — carrega o conteúdo em português no formato Markdown
- `curl ai.investplay.com.br/en-US` — carrega o conteúdo em inglês no formato Markdown
- Acesso direto ao Markdown: https://ai.investplay.com.br/pt-BR.md

### Exemplo com `llm`

```bash
curl ai.investplay.com.br/pt-BR | llm -s 'entenda a plataforma InvestPlay' -m claude-sonnet-4-5
```

## Observações

- Abrir `ai.investplay.com.br` em um browser retorna uma resposta `text/html` amigável.
- Acesso via curl/código/programa retorna uma resposta `text/markdown` limpa — detectado pelo `user-agent`.
- Para JS no browser (onde não é possível alterar o `user-agent`), adicione o header `Accept: text/markdown` para forçar a resposta Markdown.

## Atualizar o conteúdo

### Editar o arquivo de conteúdo principal

```bash
# Português
vim views/pt-BR/index.md

# Inglês
vim views/en-US/index.md
```

### Publicar as alterações

```bash
git commit -am "atualiza conteúdo"
git push
```

## Estrutura do projeto

```
investplay-web-ai/
├── server.js          # Aplicação Node.js/Express
├── package.json       # Dependências
├── .env.example       # Variáveis de ambiente de exemplo
├── .gitignore
├── views/
│   ├── pt-BR/
│   │   └── index.md   # Conteúdo principal em português
│   └── en-US/
│       └── index.md   # Conteúdo principal em inglês
├── public/            # Assets estáticos (CSS, favicon)
└── .github/
    └── workflows/
        └── deploy.yml # CI/CD automático
```

## Rodando localmente

```bash
# Instalar dependências
npm install

# Rodar em desenvolvimento
npm run dev

# Rodar em produção
npm start
```

A aplicação sobe em `http://localhost:3000`

## Deploy

O projeto está configurado para deploy automático via GitHub Actions para qualquer plataforma de hospedagem Node.js (Railway, Render, Fly.io, etc.).

Variáveis de ambiente necessárias:
- `PORT` — porta da aplicação (padrão: 3000)
- `HOST` — hostname canônico (ex: `ai.investplay.com.br`)
- `NODE_ENV` — `production` ou `development`

## Inspiração

Este projeto foi inspirado em [kobana-web-ai](https://github.com/universokobana/kobana-web-ai), que por sua vez se inspirou em [jina-ai/meta-prompt](https://github.com/jina-ai/meta-prompt).

## Licença

MIT

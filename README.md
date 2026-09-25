# Central de Ferramentas — versão GitHub

## Como funciona

O site é estático e pode ser publicado no GitHub Pages.

A página `index.html` lê automaticamente o arquivo `ferramentas.json`.

Isso significa que, depois da publicação inicial, para adicionar uma ferramenta você só precisa editar o JSON no GitHub.

## Estrutura

```
central-ferramentas/
├── index.html
├── ferramentas.json
├── .nojekyll
└── README.md
```

## Exemplo de nova ferramenta

Adicione dentro de `ferramentas`:

```json
{
  "id": "minha-ferramenta",
  "nome": "Minha Ferramenta",
  "url": "https://seu-link-aqui/",
  "categoria": "Produção",
  "descricao": "Descrição curta do que ela faz.",
  "icone": "M",
  "destaque": false,
  "ativo": true,
  "ordem": 4
}
```

## Atualização para todos

Depois que o commit for salvo no GitHub, o GitHub Pages publica a nova versão. A Central busca `ferramentas.json` sem cache para reduzir o risco de exibir uma lista antiga.

## Observação importante

Esta arquitetura usa o GitHub como uma base central de leitura.

Ela NÃO coloca token do GitHub dentro do HTML. Isso é proposital: colocar um Personal Access Token em uma página pública é inseguro.

Para um painel administrativo que grave diretamente no repositório a partir da própria Central, seria necessário usar autenticação segura (por exemplo, GitHub OAuth/GitHub App + backend/serverless). Para o cenário simples, editar `ferramentas.json` pelo GitHub é mais seguro e exige pouca manutenção.

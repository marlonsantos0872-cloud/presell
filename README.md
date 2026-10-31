# Presell — Histórias Únicas

Página de pré-acesso (presell) independente do site principal. O botão
**"Acessar o site"** leva para `https://historiaunicabrasil.online/` e preserva
UTMs e click IDs (`utm_*`, `fbclid`, `ttclid`, `gclid`, `msclkid`, `twclid`,
`click_id`, `kwai_click_id`).

## Estrutura

```
.
├── index.html          # presell (HTML/CSS/JS em um arquivo)
├── assets/
│   └── logonova.webp   # logo oficial
├── vercel.json         # noindex + cache dos assets
└── README.md
```

## Destino do botão

O destino fica em `data-destination` no `index.html`:

```html
data-destination="https://historiaunicabrasil.online/?enter=1"
```

O `?enter=1` passa pelo gate interno do site (caso ele esteja ligado) e é
removido no redirect; se o gate estiver desligado, é ignorado. Os parâmetros da
URL do presell (UTMs/click IDs) são anexados automaticamente pelo JS.

## Deploy na Vercel

1. Importe este repositório na Vercel.
2. Framework preset: **Other**.
3. Build command: deixe vazio. Output directory: `.` (raiz).
4. Depois do primeiro deploy, aponte o domínio novo para o projeto em
   **Settings → Domains**.

Não há build, dependências ou variáveis de ambiente — é um site estático.

## Observações

- Quando este presell estiver no ar com o domínio novo, mantenha o presell
  interno do site principal **desligado** (`presell_enabled` no painel
  `/admin/ → Configurações`) para não exibir a tela duas vezes.
- Nenhum pixel é carregado aqui: a atribuição viaja na URL até a landing, onde
  os pixels do TikTok/Kwai/Meta são disparados.
- Para trocar a logo, substitua `assets/logonova.webp` mantendo o mesmo nome
  (ou ajuste o `src` no `index.html`).

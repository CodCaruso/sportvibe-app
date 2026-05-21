# SportVibe

> Sua tribo esportiva te espera.

Plataforma social mobile-first que conecta atletas amadores por esporte, localização, nível e reputação — e integra reserva de quadras esportivas com pagamento via PIX.

## Estrutura do projeto

| Arquivo | Descrição |
|---|---|
| `index.html` | App do usuário (PWA mobile-first) |
| `arena.html` | Painel B2B do parceiro (arenas) — acessível em `/arena` |
| `manifest.json` | Manifesto PWA para instalação no celular |
| `sw.js` | Service worker (cache básico offline) |
| `vercel.json` | Configuração de roteamento, cache e segurança |

## Stack

HTML + CSS + JavaScript vanilla em arquivos únicos — sem build step. Roda direto no browser.

## URLs

- App do usuário: `/`
- Painel da arena: `/arena`

## Deploy

Hospedado no Vercel via GitHub. Cada push na branch `main` dispara um deploy automático.

Veja [DEPLOY.md](./DEPLOY.md) para o passo a passo da configuração inicial.

## Modelo de negócio

- **Para usuários:** gratuito. SportVibe Pro opcional (R$19,90/mês).
- **Para arenas:** painel gratuito. SportVibe retém 10% das reservas geradas pelo app.

## Licença

Proprietário © 2026 SportVibe Tecnologia e Serviços. Todos os direitos reservados.

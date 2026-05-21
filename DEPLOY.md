# Guia de Deploy — SportVibe no Vercel via GitHub

Este guia leva o SportVibe do seu computador para o ar (URL pública) em ~15 minutos. Você não precisa saber programar — basta seguir os passos na ordem.

## Pré-requisitos

- [ ] Conta no GitHub (gratuita — criar em github.com)
- [ ] Conta no Vercel (gratuita — criar em vercel.com)
- [ ] Esta pasta `sportvibe-app` no seu computador

---

## Parte 1 — Criar conta no GitHub (pule se já tem)

1. Acesse **https://github.com/signup**
2. Use o e-mail `mateussoruca@gmail.com`
3. Escolha um username — sugestão: `mateussoruca` ou `sportvibe-blumenau`
4. Confirme o e-mail

---

## Parte 2 — Criar o repositório no GitHub

1. Já logado, clique no botão **"+"** no canto superior direito → **"New repository"**
2. Preencha:
   - **Repository name:** `sportvibe-app`
   - **Description:** `SportVibe — Plataforma de esportes e reserva de quadras`
   - **Visibilidade:** **Private** (privado — protege a ideia)
   - **NÃO marque** "Add a README file" — já temos um
   - **NÃO marque** "Add .gitignore" — já temos um
3. Clique em **"Create repository"**
4. Na próxima tela, deixe aberta em outra aba — vamos usar daqui a pouco

---

## Parte 3 — Subir os arquivos para o GitHub

A forma mais simples (sem terminal) é o **upload pela web**:

1. Na página do repositório recém-criado, clique em **"uploading an existing file"** (link em azul no meio da página)
2. Arraste **TODOS os arquivos** desta pasta (`sportvibe-app`) para a área indicada:
   - `index.html`
   - `arena.html`
   - `manifest.json`
   - `sw.js`
   - `vercel.json`
   - `README.md`
   - `DEPLOY.md` (este arquivo)
   - `.gitignore` (importante! pode estar oculto — habilite "mostrar arquivos ocultos" no Windows)
3. Aguarde o upload terminar (barra verde embaixo de cada arquivo)
4. No campo **"Commit changes"** (embaixo da página):
   - Título: `Initial commit — SportVibe MVP`
   - Mantenha selecionado "Commit directly to the main branch"
5. Clique em **"Commit changes"**

Pronto — seu código está no GitHub.

### Alternativa: upload via Git CLI (só se você tem prática)

```bash
cd C:\Users\Mateus\Documents\Claude\Projects\Meu Futuro\sportvibe-app
git init
git add .
git commit -m "Initial commit — SportVibe MVP"
git branch -M main
git remote add origin https://github.com/SEU-USERNAME/sportvibe-app.git
git push -u origin main
```

---

## Parte 4 — Criar conta no Vercel e conectar o GitHub

1. Acesse **https://vercel.com/signup**
2. Clique em **"Continue with GitHub"** (entrar usando sua conta GitHub é o mais fácil)
3. Autorize o Vercel a acessar sua conta GitHub
4. Na primeira tela do Vercel, escolha o plano **Hobby (Gratuito)** — é mais que suficiente

---

## Parte 5 — Importar o projeto no Vercel

1. No dashboard do Vercel, clique em **"Add New..." → "Project"**
2. Você vai ver a lista dos seus repositórios do GitHub
3. Localize **`sportvibe-app`** e clique em **"Import"**
   - Se não aparecer, clique em **"Adjust GitHub App Permissions"** e dê permissão pro repo
4. Na tela de configuração:
   - **Project Name:** `sportvibe-blumenau` (esse nome vira parte da URL)
   - **Framework Preset:** **Other** (deixe assim — é HTML estático)
   - **Root Directory:** deixe `./` (raiz)
   - **Build and Output Settings:** **NÃO mexa em nada** — o Vercel detecta tudo sozinho
5. Clique em **"Deploy"**
6. Aguarde ~30 segundos — você vai ver os logs subindo na tela
7. Quando aparecer "Congratulations!" com fogos de artifício, está no ar

---

## Parte 6 — Acessar a URL pública

Vai ter algo assim:

- **App do usuário:** `https://sportvibe-blumenau.vercel.app/`
- **Painel da arena:** `https://sportvibe-blumenau.vercel.app/arena`

**Teste no celular:**

1. Abra o Chrome no celular
2. Acesse a URL do app do usuário
3. No menu (3 pontinhos), toque em **"Instalar app"** ou **"Adicionar à tela inicial"**
4. O SportVibe vira um app instalado

**Para a reunião com a Blupadel:**

- Demo do usuário: abrir a URL do app no celular
- Demo do painel: abrir a URL `/arena` no notebook (ou no próprio celular em modo paisagem)

---

## Parte 7 — Como fazer updates depois (CI/CD)

A partir de agora, cada vez que o Claude (eu) editar um arquivo:

1. Você ou eu fazemos upload do arquivo modificado no GitHub (mesmo fluxo da Parte 3, mas substituindo o arquivo)
2. O Vercel detecta e faz deploy automático em ~30 segundos
3. A URL pública atualiza sozinha

Se você quiser que eu te ajude a fazer cada update, é só me avisar quando precisar.

---

## Parte 8 — Conectar domínio próprio (futuro)

Quando você comprar `sportvibe.com.br` (via Registro.br, ~R$40/ano):

1. No Vercel, vá em **Project Settings → Domains**
2. Adicione `sportvibe.com.br` e `www.sportvibe.com.br`
3. O Vercel mostra os registros DNS que você precisa configurar no Registro.br
4. Aguarde 1-24h para a propagação
5. Pronto — URLs ficam:
   - `https://sportvibe.com.br/` (app)
   - `https://sportvibe.com.br/arena` (painel)

---

## Solução de problemas

**"O upload não aceita arquivos ocultos como .gitignore"**
→ No Windows Explorer: aba "Exibir" → marcar "Itens ocultos". Aí o `.gitignore` aparece e pode ser arrastado.

**"Não vejo meu repo no Vercel"**
→ Vercel → Settings → Integrations → GitHub → "Configure" → adicionar permissão para o repo `sportvibe-app`.

**"A URL `/arena` dá 404"**
→ Confirme que o `vercel.json` foi enviado para o GitHub. Vá no repo no GitHub e procure pelo arquivo. Se não estiver lá, faça upload novamente.

**"As mudanças não aparecem no site"**
→ O navegador pode estar com cache. Force refresh: Ctrl+Shift+R no desktop, ou feche e reabra a aba no celular.

---

## Custo

- GitHub: **R$0** (plano gratuito permite repos privados ilimitados)
- Vercel Hobby: **R$0** (até 100 GB de banda/mês — suficiente para centenas de usuários)
- Domínio `.com.br`: ~R$40/ano (opcional)

**Total mensal: R$0** até você precisar de mais banda ou comprar domínio.

---

*Última atualização: maio de 2026*

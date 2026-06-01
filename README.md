# Deploy · Protótipo Cofecal OS

Pacote de deploy do protótipo navegável da Cofecal OS para GitHub Pages com senha (StaticCrypt) e domínio próprio.

## Arquivos
- `index.html` — protótipo encriptado (AES-256 client-side com StaticCrypt). Cliente abre a página, digita a senha, vê o sistema. Sem senha, conteúdo zero acessível.
- `CNAME` — domínio personalizado `cofecal.guilds.com.br`.
- `README_DEPLOY.md` — este arquivo.

## Configuração
- **Domínio:** https://cofecal.guilds.com.br
- **Senha do cliente:** `diego-cofecal-2026`
- **Repo:** `Gustavogm9/cofecal` (privado)
- **GitHub Pages:** branch `main` · raiz `/` · HTTPS forçado

## O que falta pra ir ao ar
Só uma coisa, no Wix:

1. Painel Wix → **Domínios** → `guilds.com.br` → **Registros DNS**
2. Adicionar um **CNAME**: `host = diego` · `valor = Gustavogm9.github.io`
3. Aguardar a propagação (5–15 min) — o certificado SSL provisiona automaticamente.

## Mensagem pronta pra mandar pro Diego (WhatsApp)
```
Diego, aqui está o link do protótipo navegável da Cofecal OS:
https://cofecal.guilds.com.br
Senha: diego-cofecal-2026

Dá pra abrir no celular ou desktop. Já mostra o sistema completo: dashboard, pedidos, estoque das 3 filiais, NFe, produção, financeiro, WhatsApp, equipe, BI com 5 cockpits, e o app mobile com a visão de cada papel (dono, gestor, vendedor, desenhista, produção, entregador, financeiro, comprador).

Qualquer dúvida, me avisa. Vou marcar uma chamada pra te apresentar?
```

## Trocar a senha (se quiser)
Re-rodar localmente o staticrypt no protótipo original com a nova senha e empurrar o `index.html` por cima:
```bash
npx staticrypt cofecal_prototipo.html -p "NOVA-SENHA" --remember 7 --short \
  --template-title "Cofecal OS · Acesso restrito" \
  --template-button "Entrar" --template-placeholder "Senha" \
  --template-color-primary "#EA580C" --template-color-secondary "#FBFAFC"
```

## Segurança
- StaticCrypt usa AES-256 com hash do password no client. O conteúdo do protótipo NÃO está em texto claro no `index.html` — só a tela de login é visível antes da senha.
- Senha é trivialmente trocável (recompilar e dar push do `index.html`).
- O repo é privado (não fica visível pelo público nem por buscas).

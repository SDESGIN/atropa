# TROPA V51 — edição final deste ciclo de refinamento

A TROPA já está publicada e sendo utilizada. A V51 conclui o ciclo de ajustes visuais e de experiência iniciado na V44, com melhorias de navegação por busca, posição do histórico, foco nos modais e estado offline. Sem migração de dados.

# TROPA V50 — acabamento de mensagens e experiência

**A plataforma já está publicada e em uso.** A V50 é uma atualização incremental da V49, com separadores de datas, navegação por mensagens fixadas e cópia rápida de texto. Preserva login por usuário e senha sem e-mail, NitroPA gratuito, Firebase e LiveKit.

**Instalação:** envie os **8 arquivos soltos da raiz** do ZIP para a raiz do repositório GitHub, sem criar pastas. Na Netlify, mantenha Node.js 22 e `npm run build:cloud`.

**Teste local:** `npm run check:v50`. **Versão esperada:** `/api/health` → `5.0.0`.

Leia `CHANGELOG-V50.md` e `docs/V50-EXPERIENCIA.md` para a descrição das melhorias e o roteiro de teste com usuários.

---

# TROPA V49 — destaque fixo nas chamadas

Atualização incremental da plataforma que já está no ar. Veja `CHANGELOG-V49.md` e `docs/V49-EXPERIENCIA-DE-CHAMADAS.md`.

**GitHub:** envie os oito arquivos soltos da raiz do ZIP. **Netlify:** mantenha Node 22 e `npm run build:cloud`. O aplicativo preserva Firebase e LiveKit.

**Teste local:** `npm run check:v49`. **Versão:** `/api/health` → `4.9.0`.

---

# TROPA V48 — UX e ajustes

Esta edição incrementa a V47 em produção. **Novidades:** busca de preferências dentro do modal, categorias navegáveis, indicadores acessíveis, tecla Esc para limpar filtros e `Ctrl/Cmd+,` para abrir configurações. Não altera Firebase Auth, Firestore, Storage, LiveKit ou NitroPA.

Para instalar no GitHub, envie os **8 arquivos soltos** da raiz do ZIP e mantenha o build `npm run build:cloud` com Node 22. Teste primeiro no deploy de prévia da Netlify.

Verificação local: `npm run check:v48` (código e testes com serviços simulados); sem acesso ao ambiente conectado do usuário.

Leia `CHANGELOG-V48.md` e `docs/V48-EXPERIENCIA.md` para conferir as melhorias.

---

# TROPA V47 — melhorias de experiência em produção

A V47 é uma atualização incremental da TROPA que **já está publicada e em uso**. Preserva Firebase, LiveKit, login por usuário/senha sem e-mail, recuperação por código e NitroPA gratuito.

- Botão contextual **Mensagens recentes** ao rolar para cima em chats longos (canal, DM ou grupo).
- Atalhos: `Ctrl/Cmd+K` busca rápida já existente; `?` abre guia de atalhos; `/` foca a caixa de mensagem quando disponível; `Esc` fecha janela. Não intercepta a digitação.
- Estados de foco visíveis, transições discretas e refinamento de desktop/mobile com suporte a reduzir movimento.
- Não altera Firestore rules, Storage rules, Netlify, LiveKit ou modelos de dados.

**Instalação:** envie os oito arquivos soltos da raiz para o repositório existente. Faça deploy de prévia primeiro e confira login/chat/call nos dispositivos usados pelo seu público. `npm run build:cloud` continua o comando Netlify e `npm run check:v47` roda a regressão local. O erro DNS de dependências no ambiente do assistente não é um erro confirmado no seu deploy.

Veja `CHANGELOG-V47.md` e `docs/V47-UX.md`. Versões anteriores permanecem documentadas dentro do arquivo binário reconstruído.
# TROPA V46 Cloud — integridade e auditoria de restauração

**NÃO HOMOLOGADA PARA LANÇAMENTO PÚBLICO.** A V46 preserva a V45 e melhora o procedimento de recuperação Cloud: valida os registros antes de gravar e compara todo o conteúdo de um destino restaurado **somente leitura**. Os testes são simulados; **nenhum projeto Firebase real foi alterado**.

## Comandos principais

- `npm run check:v46` — regressão e análise local.
- `npm run audit:v46` — auditoria documental das 82 seções e 50 telas.
- `npm run backup:cloud:create -- /caminho/privado/novo` — backup Cloud manual, com credenciais da origem.
- `npm run backup:cloud:verify -- /caminho/privado/novo` — SHA-256 e pré-validação profunda dos registros.
- `npm run backup:cloud:restore -- /caminho/privado/novo --target-project=projeto-de-teste` — somente simulação, sem escrita.
- `npm run backup:cloud:audit-target -- /caminho/privado/novo --target-project=projeto-de-teste` — **somente leitura**, exige credencial e bucket do staging.
- `npm run verify:v46-release` — gate de publicação, falha se faltar comprovação externa.

**Restauração com `--apply` é perigosa.** É bloqueada para o projeto original, exige destino diferente/vazio e duas confirmações. Consulte `docs/V46-CLOUD-INTEGRIDADE.md` antes de qualquer recuperação. O backup SQLite legado não foi alterado.

## Instalação

Substitua os oito arquivos soltos da V45 na raiz do GitHub pelos oito da V46. Netlify Node.js 22; build `npm run build:cloud`; publicação `cloud/site` e functions `cloud/functions`. Confira a versão `4.6.0` em `/api/health` depois do **deploy de teste**. Consulte `CHANGELOG-V46.md` e `docs/V46-RELEASE-GATE.md`.

Sem e-mail, NitroPA grátis, Firebase/LiveKit/Netlify preservados. Não enviar credenciais ou snapshots de usuários para chat, GitHub ou frontend.

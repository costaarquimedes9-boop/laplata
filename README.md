# LA PLATA | GESTÃO — novo projeto para Vercel

Projeto criado do zero: HTML/CSS/JS e Vercel Functions em Node.js (sem Python).
Inclui imagem de entrada LA PLATA, login, cadastro pendente, aprovação pelo
administrador, membros, cargos, baús exclusivos, farm, estoque, aprovações
de entradas/retiradas e histórico em PostgreSQL.

## Instalação
1. Extraia o ZIP e envie **o conteúdo da pasta**, não o ZIP, para a raiz
   de um repositório GitHub novo.
2. Importe o repositório na Vercel. Framework Preset: **Other**.
   Root Directory: raiz do projeto. Não defina Build Command.
3. Crie um banco PostgreSQL persistente (por exemplo Neon).
4. Configure as variáveis de ambiente na Vercel:
   - `DATABASE_URL` — URL de conexão PostgreSQL
   - `SESSION_SECRET` — string aleatória com pelo menos 32 caracteres
   - `ADMIN_PASSWORD` — senha forte de pelo menos 8 caracteres
5. Faça Deploy. Acesse `/api/health` para verificar o backend.
6. Abra a página inicial. Admin: login `admin`, senha = `ADMIN_PASSWORD`
   **da primeira inicialização**. Não há senha fixa no código.

## Regras
- Novos cadastros ficam Pendentes e não entram até aprovação do ADM.
- ADM cadastra, edita, exclui usuários e atribui baús únicos (1 a 999).
- Membro só visualiza Meu Baú, solicita farm e acompanha histórico individual.
- Líder, Sub Líder, Gerente de Farm, Gerente de Vendas e ADM consultam
  baús, analisam farm e solicitam/aprovam estoque.
- Ninguém aprova a própria solicitação.
- Toda entrada/retirada de estoque fica Pendente e só altera o saldo
  depois de aprovada por outro responsável.
- Estoque nunca pode ficar negativo.

## Avisos de implantação
- Esta versão é uma base funcional nova, ainda **não testada em sua conta
  Vercel nem auditada para produção**. Faça testes com dois navegadores.
- Para uso público, acrescente proteção CSRF, limitação de tentativas,
  redefinição segura de senhas, revisão de logs e política de backups.
- Não envie `.env` com segredos ao GitHub.
- `ADMIN_PASSWORD` cria a senha do admin apenas na inicialização;
  alterar essa variável depois não redefine a senha já salva.
- O contador de entradas é local ao navegador, não global.
- Itens e movimentos são fictícios para roleplay.

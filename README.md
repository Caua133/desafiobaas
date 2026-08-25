# ⚔️ NEXUS DOS HERÓIS — Projeto Base Bugado

> **Desafio Final — Módulo 04 · Web On Fire Academy**

Este projeto é um jogo de criação de personagens com Firebase Auth e Firestore.
O problema? Ele tem **8 bugs reais** que quebram funções importantes do app.
**Sua missão: encontrar, entender e corrigir cada um deles.**

---

## 🎮 Sobre o Jogo

O Nexus dos Heróis permite:
- Criar conta e fazer login (Firebase Auth)
- Criar personagens escolhendo entre 5 classes épicas
- Equipar armas, armaduras e anéis em cada herói
- Gerenciar sua coleção no dashboard pessoal

Só que nada disso funciona direito por causa dos bugs...

---

## 🚀 Como Começar

### 1. Faça um fork e clone o repositório

```bash
# Clique em "Fork" no GitHub, depois:
git clone https://github.com/SEU-USUARIO/nexus-heroes.git
cd nexus-heroes
```

### 2. Instale as dependências

```bash
npm install
```

### 3. Configure o Firebase

1. Acesse [console.firebase.google.com](https://console.firebase.google.com)
2. Crie um novo projeto
3. Ative **Authentication** → provedor de E-mail/Senha
4. Ative o **Cloud Firestore** (modo de teste por enquanto)
5. Em Configurações do projeto → adicione um app web → copie as credenciais

### 4. Configure as variáveis de ambiente

```bash
cp .env.example .env.local
```

Abra `.env.local` e preencha com os valores do seu projeto Firebase.

### 5. Rode o projeto

```bash
npm run dev
```

Acesse [http://localhost:3000](http://localhost:3000) e veja os bugs em ação!

---

## 🐛 Os 8 Bugs

O app exibe cada bug com um banner vermelho na tela — **leia o banner antes de ir para o código**.

| # | Área | Arquivo | Sintoma Visível |
|---|------|---------|-----------------|
| 01 | Auth | `src/app/(auth)/login/page.tsx` | Login trava e não mostra erro de senha errada |
| 02 | Auth | `middleware.ts` | Dashboard acessível sem login (ou bloqueia quem está logado) |
| 03 | Auth | `src/app/(auth)/cadastro/page.tsx` | Cadastro aceita senhas diferentes sem reclamar |
| 04 | Firestore | `src/services/personagens.ts` | Dashboard mostra personagens de todos os usuários |
| 05 | Firestore | `src/services/personagens.ts` | Personagem criado não aparece no dashboard |
| 06 | Firestore | `src/services/personagens.ts` | Equipar item apaga os outros equipamentos |
| 07 | Firestore | `src/services/personagens.ts` | Deletar personagem deleta o errado |
| 08 | Security | `firestore.rules` | Banco de dados sem proteção alguma |

---

## 📋 Como Entregar

### Regras dos commits

Cada bug corrigido = **1 commit separado**. Siga este formato:

```
fix(bugXX): descrição curta do que foi corrigido

Exemplo:
fix(bug01): exibir mensagem de erro no login quando senha está errada
fix(bug04): filtrar personagens por userId no listarPersonagens
```

### Relatório

Crie um arquivo chamado `RELATORIO.md` na raiz do projeto com a seguinte estrutura para cada bug:

```markdown
## BUG #01 — [Nome do Bug]

### O que estava acontecendo
[Descreva o comportamento incorreto que você observou]

### Por que acontecia
[Explique a causa técnica — qual linha, qual função, qual conceito do Firebase estava errado]

### Como corrigi
[Mostre o trecho de código antes e depois]

### Screenshot ou resultado
[Print da tela com o bug funcionando ERRADO e depois funcionando CERTO]
```

---

## 📁 Estrutura do Projeto

```
nexus-heroes/
├── middleware.ts              ← Proteção de rotas (BUG 02)
├── firestore.rules            ← Security Rules (BUG 08)
├── src/
│   ├── app/
│   │   ├── (auth)/
│   │   │   ├── login/         ← BUG 01
│   │   │   └── cadastro/      ← BUG 03
│   │   ├── dashboard/         ← BUG 02, 04, 07 (efeitos visíveis aqui)
│   │   ├── criar-personagem/  ← BUG 05 (efeito visível aqui)
│   │   └── personagem/[id]/   ← BUG 06, 07 (efeitos visíveis aqui)
│   ├── components/
│   │   └── BugBanner.tsx      ← Componente que exibe os banners de bug
│   ├── contexts/
│   │   └── AuthContext.tsx    ← Contexto de autenticação (sem bugs)
│   ├── firebase/
│   │   └── config.ts          ← Configuração do Firebase (sem bugs)
│   ├── services/
│   │   └── personagens.ts     ← Bugs 04, 05, 06 e 07 estão aqui!
│   └── types/
│       └── index.ts           ← Tipos TypeScript (sem bugs)
└── .env.example               ← Variáveis de ambiente necessárias
```

---

## ✅ Checklist de Entrega

- [ ] Fork feito no GitHub
- [ ] `.env.local` configurado com Firebase real
- [ ] Bug 01 corrigido + commit
- [ ] Bug 02 corrigido + commit
- [ ] Bug 03 corrigido + commit
- [ ] Bug 04 corrigido + commit
- [ ] Bug 05 corrigido + commit
- [ ] Bug 06 corrigido + commit
- [ ] Bug 07 corrigido + commit
- [ ] Bug 08 corrigido + commit
- [ ] `RELATORIO.md` criado com prints e explicações
- [ ] App deployado na Vercel
- [ ] Link do deploy enviado

---

Bora caçar bugs! 🔥

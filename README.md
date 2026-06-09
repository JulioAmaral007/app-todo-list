# To-Do App

Aplicativo mobile de gerenciamento de tarefas, construído com React Native e Expo. Organize suas tarefas com filtros, marque como concluídas e mantenha tudo salvo localmente no dispositivo — sem precisar de internet ou conta.

<div align="center">
  <img src="./assets/home.png" width="640" height="416" />
</div>

---

## 🚀 Visão Geral

O **To-Do App** é uma aplicação mobile cross-platform voltada para produtividade pessoal. Permite criar, organizar e acompanhar tarefas de forma simples e rápida, com dados persistidos localmente via SQLite — funcionando 100% offline.

- **Público-alvo:** qualquer pessoa que precise organizar tarefas no dia a dia
- **Problema resolvido:** manter um controle simples de afazeres sem depender de serviços externos
- **Diferenciais:** animações fluidas, filtros por status, persistência local e interface em português

---

## 🛠️ Tecnologias Utilizadas

| Camada | Tecnologia |
|---|---|
| Framework | Expo 51 + React Native 0.74 |
| Linguagem | TypeScript 5.3 |
| Roteamento | Expo Router 3 (file-based) |
| Estilização | NativeWind 4 (Tailwind CSS para React Native) |
| Banco de Dados | Expo SQLite 14 (armazenamento local) |
| Animações | React Native Reanimated 3 |
| Gestos | React Native Gesture Handler |
| Fontes | Google Fonts — Poppins |
| Qualidade | ESLint, Prettier, Jest |

---

## 🎯 Principais Funcionalidades

- **Adicionar tarefas** — campo de texto com validação e botão de confirmação
- **Listar tarefas** — exibição em lista otimizada, ordenada pelas mais recentes
- **Filtrar por status** — abas "Todos", "À Fazer" e "Finalizados"
- **Marcar como concluída** — checkbox animado com toggle visual imediato
- **Deletar tarefas** — remoção direta com atualização automática da lista
- **Animações de entrada/saída** — itens animam ao entrar e sair da viewport
- **Persistência offline** — dados salvos localmente via SQLite, sem internet

---

## 🏗️ Arquitetura

O app segue uma arquitetura simples de tela única com componentes reutilizáveis.

**Fluxo principal:**

1. `_layout.tsx` inicializa o banco SQLite e carrega as fontes
2. `index.tsx` gerencia o estado local e orquestra os componentes
3. Os componentes (`FormTask`, `TaskItem`, `Button`) se comunicam via props e callbacks
4. O hook `useTaskDatabase` abstrai todas as operações com o banco de dados
5. Cada ação do usuário (criar, completar, deletar) dispara uma atualização na lista

Não há gerenciamento de estado global — todo o estado é local ao componente principal, o que mantém o código simples e direto.

---

## 📂 Estrutura do Projeto

```
to-do/
├── src/
│   ├── app/
│   │   ├── _layout.tsx       # Layout raiz: SQLite, fontes, Stack Navigator
│   │   ├── index.tsx         # Tela principal com CRUD e filtros
│   │   └── +not-found.tsx    # Página 404
│   ├── components/
│   │   ├── Button.tsx        # Botão de filtro com estado ativo/inativo
│   │   ├── FormTask.tsx      # Formulário de criação de tarefas
│   │   └── TaskItem.tsx      # Item de tarefa com animações e ações
│   ├── database/
│   │   ├── initializeDatabase.ts  # Criação da tabela na primeira execução
│   │   └── useTaskDatabase.ts     # Hook com operações CRUD
│   ├── styles/
│   │   ├── global.css        # Configuração Tailwind CSS
│   │   └── fontFamily.ts     # Definição das fontes Poppins
│   └── types/
│       └── nativewind-env.d.ts    # Tipagens do NativeWind
├── assets/                   # Ícones, splash screen e imagens
├── app.json                  # Configuração do Expo
├── tailwind.config.js        # Configuração Tailwind
└── package.json
```

---

## ⚙️ Como Executar

### Pré-requisitos

- [Node.js](https://nodejs.org/) 18 ou superior
- npm ou yarn
- [Expo Go](https://expo.dev/go) instalado no celular **ou** emulador Android/iOS configurado

### Instalação

```bash
git clone https://github.com/JulioAmaral007/ToDo-app.git
cd to-do
npm install
```

### Execução

```bash
# Inicia o servidor de desenvolvimento
npm run start

# Executa direto no Android
npm run android

# Executa direto no iOS
npm run ios

# Executa no navegador
npm run web
```

Após `npm run start`, escaneie o QR Code com o aplicativo **Expo Go** no celular.

---

## 🗄️ Banco de Dados

O app utiliza **SQLite nativo** via Expo SQLite. O arquivo `database.db` é criado automaticamente no dispositivo na primeira execução.

**Tabela: `tasks`**

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | INTEGER PK | Identificador único (autoincrement) |
| `title` | TEXT | Texto da tarefa |
| `checked` | INTEGER | Status: `0` = pendente, `1` = concluída |

As operações utilizam queries parametrizadas, protegendo contra SQL injection.

---

## 📈 Melhorias Futuras

- Edição de tarefas existentes
- Reordenação de tarefas por drag and drop
- Categorias e etiquetas para organização
- Notificações e lembretes
- Sincronização em nuvem com conta de usuário
- Tema escuro (dark mode)

---

## 👨‍💻 Desenvolvedor

Desenvolvido por:

- **Júlio Cézar** — [@JulioAmaral007](https://github.com/JulioAmaral007)

---

## 📚 Contexto

Projeto pessoal desenvolvido para explorar as capacidades do ecossistema Expo moderno, especialmente a combinação de **Expo Router**, **NativeWind** e **Expo SQLite** em uma aplicação mobile funcional e offline-first.

# MinistryHub 🗓️⛪

<p align="center">
  <img src="https://img.shields.io/badge/Status-Em%20Desenvolvimento-orange?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/Frontend-React-61dafb?style=for-the-badge&logo=react" alt="React">
  <img src="https://img.shields.io/badge/Deploy-Netlify-00C7B7?style=for-the-badge&logo=netlify" alt="Netlify">
</p>

> **Automação inteligente e gestão estratégica de escalas para ministérios e igrejas.**
> O MinistryHub é a solução para transformar processos manuais e reativos de agendamento em um fluxo de dados fluido, eficiente e autogerenciável.

---

## 📌 Temática

O projeto aborda a gestão de voluntariado e a organização operacional dentro de ambientes eclesiásticos. O foco central é solucionar gargalos de comunicação e o alto esforço cognitivo exigido na criação manual de escalas de equipes.

---

## ❓ O que é o projeto?

O **MinistryHub** é um sistema desenvolvido para automatizar a criação de escalas de forma rápida para igrejas, visando melhorar a comunicação entre os membros e evitar ambiguidades. 

Diferente de um ambiente corporativo tradicional, o trabalho em igrejas depende da disponibilidade variável de cada participante, o que torna a criação de escalas manuais um processo exaustivo e propenso a falhas. Atualmente, a elaboração é feita de forma artesanal, em Slides/Layouts ou até mesmo em papéis, gerando conflitos informacionais onde os membros esquecem seus compromissos ou recebem a informação com atraso.

O MinistryHub surge para substituir esse modelo obsoleto por uma plataforma centralizada e inteligente.

---

## ⚙️ Como funciona?

O sistema opera convertendo a complexidade de restrições em um fluxo automatizado:

1. **Definição de Parâmetros:** O sistema absorve os dias, horários e preferências de disponibilidade dos voluntários.
2. **Processamento Coerente:** O cruzamento de datas e restrições individuais é realizado via algoritmos, eliminando o esforço de validação manual.
3. **Geração da Escala:** Com base em regras de validação, a escala é gerada eliminando erros humanos e proporcionando rapidez.
4. **Disponibilização Clara:** O voluntário visualiza uma escala clara, personalizada e acessível, exibindo de maneira objetiva a data e o local exato onde estará escalado.

---

## 📐 Arquitetura do Sistema

O ecossistema do MinistryHub é composto por uma aplicação Client-Side modularizada em **React** (hospedada na Netlify), comunicando-se de forma assíncrona com uma camada de API para processamento e persistência de dados.

### 🖼️ Diagrama 1: Arquitetura Geral do Fluxo

```mermaid
graph TD
    A[Interface do Usuário - React / Netlify] -->|Requisições HTTP / JSON| B[Camada de API / Controladores]
    B --> C[Motor de Automação / Regras de Negócio]
    C --> D[Camada de Dados / Persistência]
    D -->|Retorna Dados Estruturados| A


🛠️ Tecnologias Utilizadas
 Frontend: React - Biblioteca JavaScript para construção de interfaces de usuário baseadas em componentes.
 Hospedagem/Deploy: Netlify - Plataforma de computação em nuvem automatizada para deploys front-end.
 Estilização/UI: Componentes customizados focados em clareza visual e organização de informações.
 Gerenciamento de Dados: Comunicação via API REST para processamento das regras de validação.
📊 Modelagem e Fluxo Lógico
Para garantir que a transição do modelo manual para o automatizado represente um salto estratégico, o sistema é amarrado por estruturas relacionais e fluxos rígidos de verificação.
🖼️ Diagrama 2: Diagrama de Entidade-Relacionamento (ERD) Simplificado
erDiagram
    USUARIO ||--o{ VOLUNTARIO : "possui"
    VOLUNTARIO ||--o{ ESCALA : "alocado_em"
    MINISTERIO ||--o{ ESCALA : "possui"

    USUARIO {
        int id PK
        string nome
        string email
    }
    VOLUNTARIO {
        int id PK
        int usuario_id FK
        string disponibilidade
    }
    MINISTERIO {
        int id PK
        string nome
        string local
    }
    ESCALA {
        int id PK
        int voluntario_id FK
        int ministerio_id FK
        date data_hora
    }
🖼️ Diagrama 3: Fluxo do Algoritmo de Validação de Escala
graph TD
    Start([Início: Solicitação de Escala]) --> B[Buscar Voluntários Ativos]
    B --> C[Filtrar por Disponibilidade de Horário]
    C --> D{Existe Conflito de Data/Local?}
    D -- Sim --> E[Descartar para este Slot]
    E --> C
    D -- Não --> F[Alocar Voluntário no Slot]
    F --> G{Preencheu todas as vagas?}
    G -- Não --> C
    G -- Sim --> End([Escala Gerada e Publicada])

🔌 Documentação da API (Endpoints Principais)
🔐 Autenticação
 ⁠POST /api/auth/login⁠ - Valida as credenciais de acesso do líder ou voluntário.
👥 Voluntários
 ⁠GET /api/voluntarios⁠ - Retorna a listagem de membros aptos e seus respectivos ministérios.
 ⁠POST /api/voluntarios/restricoes⁠ - Cadastra impedimentos ou preferências de datas específicas.
📅 Gerador de Escalas
 ⁠POST /api/escalas/gerar⁠ - Executa o algoritmo de inteligência de cruzamento de dados para montar o mês corrente.
 ⁠GET /api/escalas/visualizar⁠ - Retorna a matriz consolidada para exibição na tela do React.
📁 Estrutura do Projeto (Frontend)
O código-fonte da interface do projeto está estruturado de forma modular e escalável:
src/
├── assets/          # Imagens, logotipos e estilos globais
├── components/      # Componentes reutilizáveis (Botões, Cards, Modais)
├── pages/           # Páginas principais da aplicação (Login, Dashboard, Escalas)
│   ├── Login/
│   ├── Dashboard/
│   └── Escalas/
├── services/        # Configurações de chamadas de API (Axios/Fetch)
├── utils/           # Funções utilitárias e formatadores de datas
├── App.js           # Componente raiz
└── index.js         # Ponto de entrada da aplicação

🖼️ Diagrama 4: Arquitetura de Componentes e Fluxo de Estado
graph LR
    App[App.js] --> Pages[Pages / Telas]
    Pages --> Components[Components Reutilizáveis]
    Pages --> Services[Services / Chamadas API]


## 🚀 Próximos Passos & Funcionalidades Futuras

O MinistryHub foi projetado para evoluir de um gerador de escalas para um ecossistema completo de gestão e engajamento de voluntários. Abaixo estão as implementações planejadas para as próximas versões do sistema:

### 📊 1. Dashboard Analítico (Painel do Administrador)
Para transformar a operação reativa em uma gestão estratégica, o sistema contará com um painel visual focado nas lideranças dos ministérios.
* **Métricas de Engajamento:** Gráficos de linha demonstrando a taxa de presença e o nível de adesão dos voluntários ao longo dos meses.
* **Distribuição de Carga de Trabalho:** Gráficos de pizza/barra exibindo o rodízio de membros para garantir que nenhum voluntário fique sobrecarregado.
* **Alertas de Desfalque:** Painel de aviso rápido indicando quais ministérios ou datas específicas possuem menos voluntários do que o mínimo necessário.

### 🔔 2. Notificações Automatizadas e Avisos
Para mitigar os esquecimentos e os conflitos informacionais gerados por avisos atrasados, o sistema implementará um motor de notificações assíncronas:
* **Lembretes de Escala:** Disparo automático de mensagens (via WhatsApp API ou E-mail) 48 horas e 2 horas antes do evento confirmando o local e o horário do voluntário.
* **Avisos de Publicação:** Notificação global para todos os membros assim que a escala do mês/semana for gerada e validada pelo algoritmo.
* **Confirmação de Leitura:** Indicador visual no painel do administrador mostrando quais voluntários já visualizaram e confirmaram que estão cientes da sua escala.

### 🔄 3. Módulo de Solicitação de Trocas (Self-Service)
Uma das maiores dores da gestão manual é gerenciar substituições de última hora. O MinistryHub descentralizará esse processo permitindo a interação direta entre os usuários:
* **Abertura de Chamado:** O voluntário impossibilitado de comparecer clica em sua escala e solicita uma "Permuta de Turno".
* **Sugestão Inteligente:** O sistema lista automaticamente outros voluntários do mesmo ministério que estão disponíveis naquela data e horário (com base nas regras de validação).
* **Fluxo de Aprovação Simples:** 1. O usuário A solicita a troca.
  2. O usuário B recebe a notificação no painel do React e aceita a permuta.
  3. O sistema valida que não há conflito de horários para ambos, altera a escala automaticamente e notifica o líder do ministério sobre a mudança.

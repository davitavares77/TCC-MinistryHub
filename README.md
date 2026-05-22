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

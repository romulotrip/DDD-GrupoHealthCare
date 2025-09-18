# Dinâmica: Design Estratégico do Projeto

## Objetivo
Identificar os subdomínios do projeto, classificá-los (Core, Supporting, Generic) e desenhar os bounded contexts, incluindo suas interações. Esse exercício ajudará a criar uma visão clara e estratégica do domínio.

---

## 1. Nome do Projeto
Life Sync

---

## 2. Objetivo Principal do Projeto
Criar uma solução digital gamificada que incentive o autocuidado físico e mental de colaboradores por meio de missões mensais, recompensas e um ranking saudável, promovendo engajamento e bem-estar de forma leve e participativa.

---

## 3. Identificação dos Subdomínios
Liste os subdomínios do sistema e classifique-os como **Core Domain**, **Supporting Subdomain** ou **Generic Subdomain**.

| **Subdomínio**              | **Descrição**                                                                                      | **Tipo**         |
|-----------------------------|--------------------------------------------------------------------------------------------------|------------------|
| Engajamento e Gamificação   | Gerencia a personalização de desafios, o progresso e a gamificação para motivar e reter os colaboradores.                                | Core Domain      |
| Gestão de Contas            | Responsável pelo ciclo de vida das contas corporativas e dos perfis dos colaboradores.                                                   | Supporting       |
| Autenticação e Autorização  | Gerencia o login, a segurança de senhas e os níveis de permissão dos diferentes tipos de usuários (Colaborador, Gestor de Bem-Estar).    | Generic          |

---

## 4. Desenho dos Bounded Contexts
Liste e descreva os bounded contexts identificados no projeto. Explique a responsabilidade de cada um.

| **Bounded Context**           | **Responsabilidade**                                                                                 | **Subdomínios Relacionados** |
|-------------------------------|-----------------------------------------------------------------------------------------------------|-----------------------------|
| Contexto de Bem-Estar   | Orquestra a experiência do colaborador com as micro-intervenções, coleta feedback e processa todos os dados para gerar as análises de engajamento e impacto no Dashboard.    | Gestão de Intervenções e Análise de Impacto  |
| Contexto de Contas      | Responsável pelo ciclo de vida das contas corporativas e dos perfis dos colaboradores.      | Pagamentos                  |
| Contexto de Identidade  | Focado exclusivamente em validar as credenciais do usuário e emitir tokens de acesso. Delega a complexidade da segurança de login para um serviço especializado. | Autenticação e Autorização

---

## 5. Comunicação entre os Bounded Contexts
Explique como os bounded contexts vão se comunicar. Use os padrões de comunicação, como:
- **Mensageria/Eventos (desacoplado):** Ex.: O Contexto de Consultas emite um evento "Consulta Finalizada", consumido pelo Contexto de Pagamentos.
- **APIs (síncrono):** Ex.: O Contexto de Pagamentos consulta informações de preços no Contexto de Consultas.

| **De (Origem)**              | **Para (Destino)**          | **Forma de Comunicação**    | **Exemplo de Evento/Chamada**                  |
|------------------------------|-----------------------------|-----------------------------|-----------------------------------------------|
| Contexto de Identidade e Acesso  | Contexto de Jornada do Colaborador    | Cadastro realizado.         | Usuário recebe acesso à plataforma.     |
| Contexto de Conteúdo        | Contexto de Jornada do Colaborador      | Conteúdo disponível para os usuarios.                         |Usuário assiste um conteúdo sobre saude e responde um quizz.     |
| Contexto de Jornada do Colaborador       | Contexto de Comunidade  | Conquista é publicada no feed | Usuário completa desafios e compartilha com a rede de amigos.
| Contexto de Jornada do Colaborador       | Contexto de Análise Corporativa | Gerado dashboards. | Empresa recebe dashboards e dados sobre os resultados dos colaboradores.

---

## 6. Definição da Linguagem Ubíqua
Liste os termos principais da Linguagem Ubíqua do projeto. Explique brevemente cada termo.

| **Termo**                    | **Descrição**                                                                                   |
|------------------------------|-----------------------------------------------------------------------------------------------|
| Ex.: Consulta                | Sessão médica entre paciente e médico.                                                       |
| Ex.: Paciente                | Usuário que agenda e realiza consultas.                                                      |
| Ex.: Receita                 | Prescrição médica gerada durante a consulta.                                                 |

---

## 7. Estratégia de Desenvolvimento
Para cada tipo de subdomínio, explique a abordagem para implementação:
- **Core Domain:** Desenvolver internamente com foco total.
- **Supporting Subdomain:** Desenvolver internamente ou parcialmente terceirizar.
- **Generic Subdomain:** Usar ferramentas ou serviços de mercado.

| **Subdomínio**              | **Estratégia**                         | **Ferramentas ou Serviços (se aplicável)** |
|-----------------------------|---------------------------------------|-------------------------------------------|
| Gestão de Consultas         | Desenvolvimento interno               |                                           |
| Cadastro de Usuários        | Interno com uso de Auth0 para login   | Auth0                                     |
| Pagamentos                  | Terceirizar usando API Stripe         | Stripe                                    |

---

## 8. Diagrama Visual (Opcional, mas Recomendado)
Desenhe um diagrama que mostre:
- Os bounded contexts.
- Como eles se comunicam.
- A relação com os subdomínios.

Use ferramentas como **Miro**, **Lucidchart** ou mesmo papel e caneta para criar seu diagrama e adicionar ao projeto.

---

## Dicas para Apresentação
- Explique cada parte do design, focando no **Core Domain** (o coração do negócio).
- Justifique por que certos subdomínios foram classificados como Supporting ou Generic.
- Destaque como a comunicação entre bounded contexts foi pensada para ser escalável.

---

Boa sorte com a dinâmica! 🚀

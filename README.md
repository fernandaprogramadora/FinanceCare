# 👵 FinanceCare - Controle Financeiro para Idosos
### *Design Inclusivo, Gerontologia Digital e Acessibilidade Universal (WCAG 2.2 AAA)*

O **FinanceCare** é uma aplicação web completa desenvolvida com foco primordial na autonomia, dignidade e segurança financeira da pessoa idosa. Ele substitui jargões bancários complicados por conceitos do cotidiano e implementa padrões modernos de usabilidade acessível para mitigar limitações visuais, motoras e cognitivas.

---

## 🌟 Principais Recursos e Diferenciais de UX/UI

### 1. Sistema Multiusuário e Isolamento de Dados (Multi-Tenant Individual)
- **Saudação 100% Dinâmica**: O sistema agora exibe *"Olá, [Nome do Usuário]!"* em todos os cabeçalhos, sem nenhum nome fixo ou *hardcoded*.
- **Fluxo Completo de Autenticação**:
  - Aba de **Login** (E-mail ou Usuário + Senha/Código com botão de visualização rápida).
  - Aba de **Cadastro Simplificado** ("Criar Nova Conta" com Nome, E-mail, Senha e Perfil de Titular ou Cuidador).
  - Botão visível de **"🚪 Sair"** que encerra a sessão ativa e retorna à tela de entrada.
- **Isolamento Estrito de Dados**: Cada usuário registrado tem seu próprio repositório isolado de transações, contas a pagar e configurações. O Usuário A nunca enxerga os lançamentos do Usuário B.
- **Criptografia e Segurança**: As senhas são processadas com hash criptográfico **SHA-256 + Salt** via Web Crypto API nativa.
- **Ambiente de Produção 100% Real**: O sistema inicia completamente limpo, sem contas ou transações falsas. Cada cliente cria seu próprio cadastro e insere seus dados reais.

### 2. Acessibilidade Visual e Motora (WCAG 2.2 AAA)
- **Ajuste Instantâneo de Tipografia (`A-`, `A`, `A+`)**: Aumenta o corpo de texto e títulos dinamicamente através de tokens CSS em tempo real.
- **Modo Alto Contraste (`🌓 Alto Contraste`)**: Fundo escuro carvão com elementos e textos em amarelo âmbar e branco nítido (taxa de contraste superior a 12:1).
- **Alvos de Toque Gigantes (*Touch Targets*)**: Botões com altura mínima entre **56px e 80px**, com espaçamento amplo de 16px para evitar toques acidentais em caso de tremores.
- **Teclado Numérico Integrado na Tela**: Teclas de 68px de altura com cálculo automático de centavos (da direita para a esquerda) e botões rápidos (`R$ 20`, `R$ 50`, `R$ 100`, `R$ 200`, `R$ 500`).

### 2. Comunicação Humanizada e Livre de Jargões
- **"Entrou Dinheiro (+)"** em vez de *Crédito / Receita*.
- **"Saiu Dinheiro (-)"** em vez de *Débito / Despesa*.
- **"Quanto você tem agora para usar"** em vez de *Saldo Consolidado*.
- **"Contas a Pagar"** com aviso amigável de dias restantes para evitar juros.

### 3. Termômetro da Tranquilidade
Em vez de gráficos complexos de pizza ou dispersão:
- 🟢 **Verde ("Situação Muito Tranquila")**: As contas essenciais estão cobertas e ainda sobrou dinheiro.
- 🟡 **Amarelo ("Atenção com as Próximas Contas")**: Mais de 70% do orçamento já foi consumido.
- 🔴 **Vermelho ("Cuidado: Gastos Maiores que as Entradas")**: Gastou além do que recebeu no mês.

### 4. Multimodalidade: Áudio e Síntese de Voz
- **🔊 "Ouvir Esta Tela" (Web Speech API)**: Narra em voz alta o resumo do saldo e orientações em português brasileiro pausado (0.88x rate).
- **🎙️ Entrada por Voz**: Permite ao idoso ditar valores numéricos com o microfone.
- **Sons Harmônicos Suaves (Web Audio API)**: Acordes agradáveis de confirmação e alerta suave sem dependências de arquivos de áudio externos.

### 5. Segurança Psicológica e Prevenção de Erros
- **Fluxo Passo-a-Passo (*One Thing at a Time*)**: 4 etapas lineares para cadastrar transações.
- **Tela de Conferência Gigante**: Antes de salvar, exibe em destaque o resumo completo para confirmação explícita.
- **Toast "Desfazer" (*Undo*)**: Permite reverter qualquer registro ou exclusão acidental.
- **🛡️ Trava Antifraude Preventiva**: Avisa em tela cheia caso o usuário digite palavras suspeitas (*urgente*, *sorteio*, *polícia*, *prêmio*) ou valores fora do padrão, orientando a ligar para o cuidador.

### 6. Modo Família / Cuidador (Supervisão Segura)
- Permite alternar para a **Visão da Família (Somente Leitura)**.
- Filhos ou cuidadores acompanham o extrato, verificam contas pendentes e geram impressões em folha A4 limpa sem ter acesso ou permissão para movimentar dinheiro.

---

## 🚀 Como Executar o Sistema

Como o sistema foi construído em arquitetura web nativa (HTML5, Vanilla CSS3 e JavaScript modular):

### Opção 1: Abrir diretamente no Navegador
Basta dar um duplo clique no arquivo [`index.html`](file:///c:/Users/Ferme/Desktop/SENAI/Antigravity/Sistema%20FinanceCare/index.html) para abrir em qualquer navegador (Google Chrome, Microsoft Edge, Firefox, Safari).

### Opção 2: Servidor Local via Python
No terminal, na pasta do projeto:
```bash
python -m http.server 8000
```
E acesse no navegador: `http://localhost:8000`

---

## 📁 Estrutura de Arquivos

```
Sistema FinanceCare/
├── index.html              # Estrutura semântica e acessível (HTML5)
├── README.md               # Documentação executiva e guia de uso
├── assets/
│   └── logo.jpg            # Logotipo do sistema em alta definição
├── css/
│   ├── variables.css       # Tokens de design, fontes e cores de alto contraste
│   ├── main.css            # Layout estrutural, cabeçalho e navegação por abas
│   └── components.css      # Componentes (cards, termômetro, teclado, modal e alertas)
└── js/
    ├── data.js             # Categorias, contas fixas e regras antifraude
    ├── storage.js          # Persistência com LocalStorage e pilha de Desfazer
    ├── audio.js            # Sintetizador Web Audio API e síntese de voz (TTS/STT)
    ├── wizard.js           # Orquestrador do fluxo passo-a-passo e tela de conferência
    └── app.js              # Controlador principal da aplicação
```

# Design — Segundo Cérebro 🧠

## Visão Geral

Aplicativo de notas pessoal com tema escuro, visual moderno e limpo. Inspirado em ferramentas como Obsidian e Notion, com foco em captura rápida de conhecimento e análise inteligente via IA.

---

## Paleta de Cores

| Token        | Valor (Dark)  | Uso                              |
|--------------|---------------|----------------------------------|
| background   | #0F1117       | Fundo principal                  |
| surface      | #1A1D27       | Cards, sidebar, painéis          |
| surfaceAlt   | #222535       | Inputs, hover states             |
| foreground   | #E8EAF0       | Texto principal                  |
| muted        | #8B8FA8       | Texto secundário, placeholders   |
| primary      | #7C6AF7       | Roxo — ações primárias, IA       |
| accent       | #4ECDC4       | Verde-água — tags, destaques     |
| border       | #2D3148       | Bordas, divisores                |
| error        | #F87171       | Erros, negativo                  |
| success      | #4ADE80       | Sucesso, positivo                |
| warning      | #FBBF24       | Avisos, aprendizados             |
| postGreen    | #22C55E       | Post Mortem — positivos          |
| postRed      | #EF4444       | Post Mortem — negativos          |
| postYellow   | #EAB308       | Post Mortem — aprendizados       |
| postPurple   | #A855F7       | Post Mortem — padrões            |
| postBlue     | #3B82F6       | Post Mortem — ações              |

---

## Telas

### 1. Tela Principal (Notes List + Editor)
Layout dividido em duas colunas (tablet) ou navegação por tabs (mobile):
- **Sidebar / Lista de Notas** (esquerda / tab 1)
  - Header com título "🧠 Segundo Cérebro" e botão de configuração de API
  - Campo de busca em tempo real (título + conteúdo + tags)
  - Chips de tags clicáveis para filtro
  - Lista de notas com: título, preview do conteúdo, tags como chips, data
  - Nota selecionada destacada com borda primária
  - Botão "Nova Nota" flutuante no canto inferior direito
  - Rodapé com contador de notas

- **Editor de Notas** (direita / tab 2)
  - Header com título editável e botão de excluir
  - Área de conteúdo (textarea expansível)
  - Seção de tags com chips + input para adicionar nova tag
  - Barra de ferramentas: 🎤 Gravar Áudio | 📄 Upload
  - Barra de IA: 📝 Resumir | 💡 Insights | 🚀 Ideias | 📂 Organizar | 🔍 Post Mortem
  - Painel de resultado da IA (expansível)
  - Estado vazio quando nenhuma nota selecionada

### 2. Modal de Configuração de API
- Seletor de provedor (Groq, OpenAI, Anthropic)
- Campo de API Key (senha, com toggle de visibilidade)
- Seletor de modelo
- Status de conexão
- Botão Salvar

### 3. Cards de Post Mortem
- 5 cards coloridos: Positivos (verde), Negativos (vermelho), Aprendizados (amarelo), Padrões (roxo), Ações (azul)
- Card extra: Padrões Recorrentes entre Post Mortems
- Ações com indicador de "precisa de dono"
- Botões: Copiar análise | Exportar .txt

---

## Fluxos Principais

### Criar e Editar Nota
1. Toque em "Nova Nota" → nova nota criada e selecionada
2. Editar título → auto-salvo no AsyncStorage
3. Editar conteúdo → auto-salvo
4. Adicionar tag → digitar no campo + Enter → chip aparece
5. Remover tag → toque no X do chip

### Gravar Áudio
1. Toque em "🎤 Gravar Áudio" → solicita permissão do microfone
2. Botão muda para "⏹ Parar" com pulso vermelho
3. Toque em "⏹ Parar" → envia para Groq Whisper
4. Loading enquanto transcreve
5. Transcrição adicionada ao conteúdo da nota

### Upload de Arquivo
1. Toque em "📄 Upload" → seletor de arquivo
2. Selecionar .txt/.md/.csv/.pdf
3. Conteúdo extraído e adicionado à nota
4. Nome do arquivo exibido como referência

### Análise de IA
1. Toque em botão de IA (Resumir, Insights, etc.)
2. Se sem API key → abre modal de configuração
3. Se nota vazia → alerta
4. Loading spinner
5. Resultado aparece em painel expansível

### Post Mortem
1. Toque em "🔍 Post Mortem"
2. IA analisa o conteúdo e retorna JSON estruturado
3. Cards coloridos aparecem com os resultados
4. Tag "post-mortem" adicionada automaticamente
5. Comparação com post mortems anteriores
6. Ações sem dono destacadas
7. Botões: Copiar | Exportar

---

## Componentes Reutilizáveis

- `NoteCard` — card de nota na sidebar
- `TagChip` — chip de tag com botão X opcional
- `AIToolbar` — barra de botões de IA
- `PostMortemCard` — card colorido de categoria
- `ApiConfigModal` — modal de configuração de API
- `AudioRecorder` — componente de gravação
- `EmptyState` — estado vazio com mensagem

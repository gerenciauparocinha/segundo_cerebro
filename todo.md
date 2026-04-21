# Segundo Cérebro — TODO

## Setup & Branding
- [x] Gerar logo do app (cérebro roxo/gradiente)
- [x] Configurar tema escuro personalizado
- [x] Atualizar app.config.ts com nome e logo

## Estrutura de Navegação
- [x] Configurar tabs: Notas e Editor
- [x] Configurar ícones de navegação

## Funcionalidades Base
- [x] Criar contexto global de notas (NotesContext)
- [x] Persistência com AsyncStorage
- [x] Tela de lista de notas (sidebar)
- [x] Botão "Nova Nota"
- [x] Nota selecionada destacada
- [x] Contador de notas no rodapé
- [x] Estado vazio quando sem nota selecionada

## Editor de Notas
- [x] Campo de título editável
- [x] Área de conteúdo (textarea)
- [x] Auto-save ao digitar
- [x] Botão excluir com confirmação
- [x] Datas de criação e atualização

## Busca e Tags
- [x] Campo de busca em tempo real (título + conteúdo + tags)
- [x] Sistema de tags por nota
- [x] Input de tag + Enter para adicionar
- [x] Chips de tags com botão X para remover
- [x] Tags como chips na sidebar (preview)
- [x] Chips de tags clicáveis para filtro
- [x] Busca por tag

## Gravação de Áudio
- [x] Botão "🎤 Gravar Áudio" no editor
- [x] Integração com expo-audio para gravação
- [x] Indicador visual pulsante (vermelho) durante gravação
- [x] Envio para Groq Whisper API (transcrição)
- [x] Loading durante transcrição
- [x] Transcrição adicionada ao conteúdo da nota
- [x] Verificação de API key antes de transcrever

## Upload de Arquivos
- [x] Botão "📄 Upload" no editor
- [x] Seletor de arquivo (.txt, .md, .csv, .pdf)
- [x] Leitura de .txt e .md como texto
- [x] Leitura de .csv como texto
- [x] Extração básica de texto de .pdf
- [x] Nome do arquivo como referência na nota

## Integração com IA
- [x] Modal de configuração de API (Groq, OpenAI, Anthropic)
- [x] Seletor de provedor e modelo
- [x] Campo de API Key com toggle de visibilidade
- [x] Salvar configuração no AsyncStorage
- [x] Status da API no header (conectado/desconectado)
- [x] Barra de IA com 5 botões: Resumir, Insights, Ideias, Organizar, Post Mortem
- [x] Painel expansível de resultado da IA
- [x] Loading spinner durante processamento
- [x] Alerta se nota vazia
- [x] Abrir modal se sem API key

## Post Mortem
- [x] Botão "🔍 Post Mortem" na barra de IA
- [x] Análise da nota como post mortem (JSON estruturado)
- [x] Cards coloridos: Positivos, Negativos, Aprendizados, Padrões, Ações
- [x] Tag "post-mortem" adicionada automaticamente
- [x] Comparação com post mortems anteriores
- [x] Card extra "Padrões Recorrentes"
- [x] Destaque de ações sem dono definido
- [x] Botão "Copiar análise" (formato Slack/email)
- [x] Botão "Exportar" (.txt com post mortem + análise)

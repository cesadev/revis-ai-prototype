# Prompt: Protótipo Hi-Fi da Extensão Revis.AI (alinhado ao Style Guide E7)

**Atue como Engenheiro(a) de Front-end e UX/UI Designer Sênior.**
Gere um protótipo hi-fi **interativo e navegável** de uma extensão de
navegador chamada “Revis.AI” (Coletivo Disco de Makita), voltada para
servidores públicos da Prefeitura do Recife que revisam documentos e
extraem dados de PDFs. A ferramenta faz revisão ortográfica e extração de
dados via IA, com foco em três palavras-chave: Precisão, Verificação e Agilidade.

O sistema consiste em overlays (barra superior, sidebar e popovers) que
flutuam sobre uma página web simulada de fundo, mais uma tela complexa de
revisão de documento.

## Stack e Requisitos Técnicos

- React + CSS. Componentes funcionais. Navegação real via estado React.
- A “página web do usuário” é um mock de fundo (ex.: artigo de wiki) sobre o
  qual os overlays aparecem com z-index alto.
- Todos os textos em português (pt-BR).

## 1. Identidade Visual (Style Guide oficial)

- Cor primária: Verde Coral #54ae84 (validação, aprovação, confiança, clareza).
- Cor secundária / superfícies escuras: Cinza Metálico #2d3638 (neutro,
  sofisticado, inspirado em Notion e Figma).
- Fundo claro: Branco #FFFFFF. Texto sobre claro: #2d3638. Texto sobre escuro: #FFFFFF.
- Estados: o próprio verde #54ae84 para sucesso/aceitar; vermelho #E2574C
  para erro/rejeitar (ex.: “Texto errado”).
- Tipografia:
  - Interface da extensão → Helvetica Neue (ou Arial/system como fallback).
  - Logo / wordmark → Poppins.
  - (Raleway só para cartazes — não usar na UI.)
- Bordas arredondadas generosas (cards escuros com ~16px), sombras suaves.
- Estética geral: limpa, sofisticada, painéis em cinza metálico escuro
  sobre a página clara.

## 2. Logo e Wordmark

- Wordmark: “Re ✓ is.AI” — a letra “v” de “Revis” é substituída por um
  **checkmark verde** (✓) maior. O “.AI” aparece em verde coral.
- Reproduza esse wordmark no canto esquerdo da barra superior.
- Ícone lançador: o checkmark verde sozinho (sem texto), que remete à
  Verificação — vínculo entre identidade visual e função.

## 3. Componentes Globais

### Botão Lançador

- Checkmark verde flutuante no canto da página. Abre/fecha a Barra Superior.

### Barra Superior (Top Bar)

Fundo cinza metálico #2d3638, conforme os slides. Contém:

- À esquerda: wordmark “Re✓is.AI”.
- Toggle Switch (verde quando ativo) rotulado “Barra Auxiliar”, que ativa a Sidebar.
- À direita, ícones: Configurações (engrenagem verde), Ajuda (?), e Fechar (X).
- Inclua também acesso ao Perfil/Login (ícone de usuário).

### Barra Lateral / Auxiliar (Sidebar)

Coluna escura (#2d3638) no canto direito, ativada pela Barra Auxiliar.
5 ícones empilhados verticalmente, com tooltip no hover. O da tela ativa
fica destacado em verde:

- Check (✓) → tela de Verificação / Resultado da análise.
- Casa → Home.
- Lupa → Busca Inteligente no documento.
- Lápis → Edição do documento.
- Upload → enviar arquivo.

## 4. Popovers

- **Configurações:** ao clicar na engrenagem, dropdown com “MODO ESCURO”
  e toggle. (O tema escuro reforça a paleta cinza metálico.)
- **Login:** ao clicar no Perfil, card de login com inputs “E-mail” e “Senha”,
  checkbox “Lembrar de mim”, botão “Entrar” e link “Criar conta”.
- **Cadastro:** transiciona para inputs “E-mail”, “Senha”, “Nome de usuário”
  e botão “Cadastrar”.

## 5. Telas da Sidebar

### Home

- “No Home você acessa configurações avançadas e os documentos já
  registrados na empresa dentro do Revis.AI.”
- Saudação + lista de documentos recentes em cards (nome, tipo, status:
  Revisado / Pendente). Mock: 3 itens. Card de ação “Enviar novo documento”.

### Busca Inteligente (Lupa)

- Campo de busca que destaca palavras-chave no documento de fundo.
- Texto de apoio: “Busque por palavras-chave no seu documento com integração
  direta aos modelos de documento da sua empresa, facilitando a extração de dados.”
- Mostre ocorrências destacadas em verde no texto + contador “1/14”.

### Edição (Lápis)

- “Corrija erros, faça marcações, crie cópias e outras opções de edição.”
- Visualizador com texto editável + barra de ferramentas simples.
- Botão “Salvar e analisar” → leva à tela de Verificação.

### Upload

- “Faça upload de seus documentos ou utilize as ferramentas em arquivos
  abertos direto no navegador.”
- Área drag-and-drop, barra de progresso simulada, redireciona para a Home.

## 6. Tela de Verificação / Resultado (ícone Check) — Tela Principal

Esta é a tela do “Botão Revis.AI”: faz a revisão ortográfica e extrai os
dados do documento já corrigido, com base nos modelos da empresa.
Layout em painéis sobre fundo escuro (#2d3638), divididos em quatro blocos:

- **PDF analisado corrigido** (bloco grande à esquerda): mostra o documento
  com trechos corrigidos destacados em verde-mostarda/realce ao passar o mouse.
- **Comparação ortográfica** (cards no topo direito), cada correção mostrando:
  - “Texto errado:” em vermelho — ex.: “Cidaede: Recife”
  - “Texto certo:” em verde — ex.: “Cidade: Recife”
  - Botões “Aceitar” (verde) e “Rejeitar” (vermelho).
- **Informações sobre o documento** (bloco grande à direita): dados extraídos
  em pares chave-valor, editáveis, com indicador de confiança da extração.
  Ex.: Contratante: Prefeitura do Recife · Nº do contrato · Objeto · Valor ·
  Vigência · CNPJ.
- Botão primário verde no rodapé: “Confirmar e exportar”.

## 7. Estados a Implementar

hover em ícones e botões, foco em inputs, loading (durante a análise/upload),
vazio (Home sem documentos), sucesso (toast verde) e erro (validação de login).
🌟 Code Review CLI (Multi-Agente e Cross-Platform)

Uma ferramenta de linha de comando leve e eficiente para inicializar o ambiente de Code Review Assistido por IA (AI-Assisted Code Review) em seus projetos Git.

Este CLI configura automaticamente os scripts de git diff e os prompts necessários, padronizando a geração de relatórios de alterações para análise de código, agora com suporte para múltiplos Agentes de IA (Copilot, Claude, Gemini, etc.) e múltiplos Sistemas Operacionais (Linux, Mac e Windows).

✨ Funcionalidades

Inicialização Rápida: Configura a estrutura de pastas e arquivos com um único comando (review-cli init).

Seleção de Agente de IA: Permite escolher para qual agente o prompt será gerado (Copilot, Claude, Gemini, Cursor, etc.), salvando na pasta correta (.github/, .claude/, etc.).

Suporte Cross-Platform:

Linux/Mac: Gera um script .sh (Bash).

Windows: Gera um script .ps1 (PowerShell) equivalente.

Seleção Interativa: Se nenhum agente ou script for especificado, a ferramenta oferece um menu interativo (com setas) para seleção.

Geração de Script de Diff: Cria scripts (git-relatorio.sh ou git-relatorio.ps1) que geram relatórios Markdown detalhados das alterações entre branches (branch vs main).

Saída Organizada: O script de relatório salva todos os arquivos gerados em um diretório centralizado (./diffs/), relativo à raiz do projeto.

🚀 Instalação e Uso

1. Pré-requisitos

Python: 3.11+

Git: Instalado e configurado.

uv (Recomendado para instalação)

2. Instalação (com uv)

# Instale como uma ferramenta global
uv tool install git+[https://github.com/oidellajulio/code-review-cli.git](https://github.com/oidellajulio/code-review-cli.git)

# (Se estiver testando localmente, após clonar)
# uv pip install -e .


3. Uso

Navegue até a raiz de qualquer projeto Git e execute o comando de inicialização:

review-cli init


A ferramenta irá perguntar:

Qual Assistente de IA você usa? (ex: copilot)

Qual o formato de Script? (ex: sh ou ps, com detecção automática do seu SO)

Uso com Flags (Não-interativo)

Você pode pular as perguntas fornecendo as flags:

# Configurar para GitHub Copilot e scripts Bash
review-cli init --ai copilot --script sh

# Configurar para Claude e scripts PowerShell (Windows)
review-cli init --ai claude --script ps


4. Gerar o Relatório de Diff

Após a inicialização, execute o script gerado, passando o nome da sua branch:

No Linux/Mac (Bash):

# Exemplo: Gerar relatório da branch 'feature/nova-api'
./.code_review/scripts/git-relatorio.sh feature/nova-api


No Windows (PowerShell):

# Exemplo: Gerar relatório da branch 'feature/nova-api'
# (Pode precisar ajustar a política de execução: Set-ExecutionPolicy RemoteSigned)
.\.code_review\scripts\git-relatorio.ps1 feature/nova-api


O relatório será salvo em ./diffs/relatorio_diff_feature-nova-api.md.

5. Estrutura Gerada

O comando init (ex: com copilot e sh) cria:

seu-projeto/
├── .code_review/
│   └── scripts/
│       └── git-relatorio.sh  <-- (Ou .ps1 para Windows)
├── .github/
│   └── prompts/
│       └── code_review.prompt.md  <-- (Ou .claude/prompts/, etc.)
└── diffs/
    └── (Relatórios aparecerão aqui após executar o script)

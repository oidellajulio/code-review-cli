## 🌟 Code Review CLI

[](https://www.python.org/)
[](https://typer.tiangolo.com/)
[](https://astral.sh/uv)

Uma ferramenta de linha de comando leve e eficiente para inicializar o ambiente de Code Review Assistido por IA (AI-Assisted Code Review) em seus projetos Git.

Este CLI configura automaticamente os scripts de `git diff` e os prompts necessários, padronizando a geração de relatórios de alterações para análise de código.

-----

## ✨ Funcionalidades

  * **Inicialização Rápida:** Configura a estrutura de pastas e arquivos com um único comando.
  * **Geração de Script de Diff:** Cria um script Bash (`git-relatorio.sh`) que gera relatórios Markdown detalhados das alterações entre branches (`branch` vs `main`).
  * **Geração de Prompt de IA:** Salva um prompt pré-formatado (Markdown) para ser usado com agentes de IA (como GitHub Copilot, Claude, Gemini, etc.) para revisão de código.
  * **Saída Organizada:** O script de relatório salva todos os arquivos gerados em um diretório centralizado (`../diffs`).

-----

## 🛠️ Pré-requisitos

Para instalar e usar a ferramenta globalmente, você precisa ter:

  * **Python:** Versão 3.11 ou superior.
  * **Git:** Instalado e configurado no seu sistema.
  * **UV:** O gerenciador de dependências e ferramentas `uv` (recomendado para instalação global).

<!-- end list -->

```bash
# Como instalar o uv (se necessário)
# curl -LsSf https://astral.sh/uv/install.sh | sh
```

-----

## 🚀 Instalação Global

Instale a ferramenta `review-cli` diretamente do repositório Git usando o `uv tool install`:

```bash
uv tool install review-cli --from git+https://github.com/oidellajulio/code-review-cli.git
```

Após a instalação, o comando `review-cli` estará disponível em qualquer pasta do seu sistema.

-----

## 💡 Uso Rápido

### 1\. Inicializar a Estrutura do Projeto

Navegue até a raiz de qualquer um dos seus projetos Git e execute o comando de inicialização:

```bash
review-cli init
```

Este comando irá:

1.  Criar a pasta de scripts: `code_review/scripts/`
2.  Criar a pasta de prompts: `.github/prompts/`
3.  Gerar o Bash Script e o Prompt de IA.

### 2\. Gerar o Relatório de Diff

Uma vez na raiz do seu projeto, execute o script recém-criado, passando o nome da sua branch como parâmetro:

```bash
# Exemplo: Gerar relatório da branch 'feature/nova-api'
./code_review/scripts/git-relatorio.sh feature/nova-api
```

### 3\. Onde encontrar os arquivos

| Arquivo/Pasta | Localização | Propósito |
| :--- | :--- | :--- |
| **`git-relatorio.sh`** | `code_review/scripts/` | Script para execução manual do `git diff`. |
| **`code_review.prompt.md`** | `.github/prompts/` | Prompt formatado para ser usado por agentes de IA. |
| **Relatórios de Saída (`.md`)** | **`../diffs/`** | Pasta centralizada para salvar todos os relatórios gerados (criada um nível acima do seu projeto). |

-----

## 🏗️ Estrutura do Repositório

O projeto é mantido com uma estrutura de projeto Python simples:

```
code-review-cli/
├── review_cli.py        # Módulo Python principal (lógica do CLI)
├── pyproject.toml       # Metadados do projeto e dependências (para uv)
└── README.md
```

-----

## 🤝 Contribuições

Sinta-se à vontade para abrir issues ou Pull Requests no repositório\!
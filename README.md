# CI&T Proposal Agent

Agente para estruturar e criar apresentações comerciais de **Professional Services** — serviços de tecnologia, IA e consultoria para resolver problemas de negócio.

O agente transforma o contexto da oportunidade e uma oferta CI&T selecionada em uma narrativa comercial clara. A estrutura é flexível: começa pelos slides institucionais vigentes fornecidos para aquela oportunidade e segue com o conteúdo específico do cliente.

## O que está incluído

- **Agente `ciandt-proposal`** — conduz a conversa e coordena as skills.
- **`ciandt-proposal-briefing`** — coleta materiais e informações, identifica lacunas e exige aprovação da estrutura e do conteúdo.
- **`ciandt-professional-services-proposal`** — orienta a narrativa e os limites de conteúdo comercial.
- **`ciandt-pptx`** — instruções de geração em PowerPoint com identidade CI&T.
- **Guia de uso** — fluxo passo a passo, exemplos de prompts, revisão e rascunhos em [`docs/HOW_TO_USE.md`](docs/HOW_TO_USE.md).
- **Configuração de assets locais** — como preparar o template e dependências da skill visual: [`docs/ASSETS_SETUP.md`](docs/ASSETS_SETUP.md).

## Fluxo recomendado

1. Selecione `ciandt-proposal` no Claude Code (ou chame `@ciandt-proposal`).
2. Anexe, para cada oportunidade, a apresentação **atualizada** da oferta CI&T que será levada e os slides institucionais vigentes.
3. Informe o problema de negócio, o público e o objetivo da apresentação, além do escopo, prazo e restrições conhecidos.
4. Responda às perguntas de briefing. O agente deve esclarecer lacunas materiais, não inventar informações.
5. Revise e aprove a **estrutura dos slides**.
6. Revise e aprove o **conteúdo slide a slide**.
7. Só depois das duas aprovações, gere e revise o PowerPoint `.pptx`, pronto para importação no Google Slides.

Não é necessário ter todas as respostas para iniciar. Porém, a oferta e os slides institucionais atuais são necessários para preparar uma versão final. Rascunhos só são criados quando solicitados explicitamente e devem estar identificados como **RASCUNHO — NÃO APROVADO**.

## Regras importantes

- Investimentos, preços, taxas, descontos e condições comerciais ficam fora da apresentação principal; o agente não os calcula nem inventa.
- O agente não inventa cases, capacidades, métricas, prazos, equipe ou compromissos da CI&T.
- Slides institucionais devem ser mantidos na abertura e não podem ser reescritos sem autorização.
- A saída inicial é `.pptx` para importar no Google Slides; criação direta no Google Slides não está incluída.
- **Os assets de marca CI&T não estão neste repositório.** O template, fontes e imagens não foram publicados. Siga [`docs/ASSETS_SETUP.md`](docs/ASSETS_SETUP.md) para adicioná-los localmente se tiver autorização para usá-los.

## Instalação no Claude Code

Clone o repositório e copie o conteúdo de `.claude/` para a pasta de configuração do Claude Code do seu usuário (`~/.claude/` no macOS/Linux ou `%USERPROFILE%\.claude\` no Windows):

```text
repo/.claude/agents/ciandt-proposal.md
  → ~/.claude/agents/ciandt-proposal.md

repo/.claude/skills/<skill-name>/
  → ~/.claude/skills/<skill-name>/
```

No Windows, a pasta correspondente é `%USERPROFILE%\.claude\agents\` e `%USERPROFILE%\.claude\skills\`. Crie as pastas caso não existam. Se o agente ou as skills não aparecerem, inicie uma nova sessão do Claude Code.

## Segurança e arquivos de propostas

Use o repositório para compartilhar instruções reutilizáveis. Não envie apresentações de clientes, dados confidenciais, tokens, configurações pessoais ou propostas geradas. O `.gitignore` exclui os assets locais CI&T e alguns formatos de saída comuns, mas revise sempre `git status` antes de publicar.

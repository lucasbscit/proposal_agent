---
name: ciandt-pptx
description: "Use this skill whenever the user wants to create, generate, build, or update a PowerPoint presentation following the CI&T brand template. Trigger when the user mentions 'CI&T presentation', 'deck no padrão CI&T', 'apresentação CI&T', 'slides CI&T', 'template CI&T', or whenever they want a branded presentation and the context involves CI&T. Also trigger when working with the file template_ciandt.pptx. This skill knows exactly which slide layouts, fonts, colors, and visual styles belong to CI&T's brand and will produce a properly branded output — always use it instead of the generic pptx skill when CI&T branding is required."
---

# CI&T PPTX Skill

Esta skill gera apresentações no padrão de marca da CI&T usando o starter template `ciandt_starter.pptx`.
O starter já contém 19 slides curados — capas, divisórias, conteúdo e encerramentos. Também serve como guia para criar novas apresentações de forma consistente.Ele serve como base para garantir que todas as apresentações sigam as diretrizes visuais da CI&T e mantenham consistência na comunicação da marca. Este starter também fornece exemplos de uso de propostas para apresentações de propostas de projetos e serviços de escopo fechao.

## Template de Referência

O starter template e todos os assets necessários estão em `{SKILL_DIR}/assets/`:

```
{SKILL_DIR}/assets/ciandt_starter.pptx     ← template com 19 slides curados
{SKILL_DIR}/assets/unpacked/               ← starter pré-desempacotado (pronto para usar)
{SKILL_DIR}/assets/catalog.md             ← mapa visual: qual slide usar para cada tipo
```

**Sempre use o starter como base para os slides CI&T criados pelo agente.** Nunca crie slides do zero sem ele.

### Propostas comerciais com slides institucionais fornecidos pelo usuário

Quando o usuário fornecer uma apresentação institucional atualizada para uma proposta:
- Preserve os slides institucionais aprovados no início do arquivo final, antes dos slides específicos da oportunidade.
- Não reescreva nem redesenhe esses slides. Trate o arquivo fornecido como fonte oficial da versão vigente.
- Use o starter CI&T para criar os slides adicionais da proposta e mantenha a identidade visual coerente.
- Combine os arquivos somente após confirmar que a estrutura, fontes e conteúdo foram aprovados. Se a importação dos slides não puder ser feita sem perda de conteúdo/layout, informe a limitação e peça orientação; não substitua os slides institucionais silenciosamente.
- A apresentação da oferta fornecida é uma fonte de conteúdo. Não copie automaticamente todos os seus slides para o deck final; selecione conteúdo pertinente e mantenha os slides como estão apenas quando o usuário pedir ou aprovar.

---

## Identidade Visual CI&T

### Dimensões
- Formato: 16:9 widescreen — **10,00" × 5,62"** (9.144.000 × 5.143.500 EMU)

### Paleta de Cores Oficial

| Nome | Hex | Uso |
|------|-----|-----|
| Coral CI&T (primária) | `#FA5A50` | Fundos de destaque, títulos de seção, botões |
| Navy escuro | `#000050` | Fundos escuros, texto em fundos claros |
| Borgonha/Magenta | `#690039` | Texto principal sobre fundo coral |
| Rosa lavanda | `#FAB9FF` | Texto de destaque sobre fundo escuro |
| Azul claro | `#B4DCFA` | Elemento de suporte |
| Branco | `#FFFFFF` | Texto em fundos escuros, elementos limpos |
| Cinza claro | `#F3F3F3` | Fundos neutros de conteúdo |

**Regra de contraste:** Nunca use texto claro em fundo claro, nem texto escuro em fundo escuro.

### Tipografia

| Fonte | Peso | Uso |
|-------|------|-----|
| DM Sans ExtraBold | ExtraBold | Títulos grandes, nomes de seção |
| DM Sans Black | Black | Títulos de impacto |
| DM Sans Bold | Bold | Labels, títulos de slide |
| DM Sans | Regular | Corpo de texto |
| DM Sans Light | Light | Texto complementar, notas |
| Poppins | Regular/Bold | Texto de apoio |
| Poppins Light | Light | Texto fino complementar |

**Tamanhos típicos:**
- Título grande (capa/seção): ~48pt (609.600 EMU)
- Título de slide: ~36pt (457.200 EMU)
- Label / subtítulo: ~9pt (114.300 EMU)
- Corpo: ~12pt (152.400 EMU)

---

## Fluxo de Criação

### 1. Analisar o conteúdo pedido
Antes de começar, entenda:
- Qual o objetivo da apresentação?
- Quantos slides são necessários?
- Quais tipos de slide (capa, seção, conteúdo, encerramento)?

### 2. Consultar o catálogo de slides

Leia `{SKILL_DIR}/assets/catalog.md` para escolher quais slides usar.
O catálogo lista os 19 slides disponíveis com tipo, fundo e quando usar cada um.

**Os slides do starter têm nomes originais** (slide20.xml, slide31.xml, etc.) — o catalog.md explica a correspondência.

### 3. Copiar o unpacked pré-processado para o diretório de trabalho

```bash
cp -r "{SKILL_DIR}/assets/unpacked/" unpacked_work/
```

Isso cria uma cópia de trabalho com todos os XMLs prontos — sem precisar desempacotar nada.

### 4. Planejar o mapeamento de slides

Veja [layouts.md](layouts.md) para uma descrição dos tipos de slide disponíveis e quando usá-los.

Use **layouts variados** — não repita o mesmo modelo de slide título + bullets em toda a apresentação. O starter tem:
- Slides de capa (coral ou navy com título grande)
- Slides de agenda (numerada ou com tópicos)
- Slides de seção / divisória
- Slides de conteúdo (texto+imagem, 2 colunas, citação, resumo)
- Slides de encerramento / obrigado

### 5. Construir a apresentação (faça você mesmo, não use subagents)
- Duplique ou delete slides usando `add_slide.py`
- Reordene na `<p:sldIdLst>` em `presentation.xml`
- **Complete todas as mudanças estruturais antes de editar conteúdo**

```bash
# Duplicar slide do starter (use o nome original do XML):
python "{SKILL_DIR}/../pptx/scripts/add_slide.py" unpacked_work/ slide20.xml

# O novo slide aparece como o último na sldIdLst — reordene conforme necessário
```

### 6. Editar o conteúdo XML

Use subagents em paralelo para editar slides independentes (cada `slideN.xml` é um arquivo separado).

**Ao editar o XML:**
- Preserve `r:id` de imagens e shapes que vão ficar
- Só altere texto dentro de `<a:t>` tags
- Para trocar cores: altere `<a:srgbClr val="XXXXXX"/>` ou `<a:schemeClr val="..."/>`
- Mantenha os atributos de fonte (`<a:latin typeface="DM Sans"/>`)

### 7. Limpar e empacotar

```bash
python "{SKILL_DIR}/../pptx/scripts/clean.py" unpacked_work/

python "{SKILL_DIR}/../pptx/scripts/office/pack.py" unpacked_work/ output.pptx \
  --original "{SKILL_DIR}/assets/ciandt_starter.pptx"
```

---

## QA (Obrigatório)

**Assuma que existem problemas. Seu trabalho é encontrá-los.**

### QA de Conteúdo

```bash
python -m markitdown output.pptx
```

Verifique: conteúdo ausente, texto fora de ordem, erros de digitação.

**Verifique texto placeholder esquecido:**

```bash
python -m markitdown output.pptx | grep -iE "xxxx|lorem|ipsum|slide presentation template|signposting|insert your"
```

Se retornar resultados, corrija antes de declarar sucesso.

### QA Visual

**Use subagents** para inspecionar os slides — você está olhando o código há tempo demais para ver o que realmente está renderizando.

Converta para imagens:
```bash
python "{SKILL_DIR}/../pptx/scripts/office/soffice.py" \
  --headless --convert-to pdf output.pptx
pdftoppm -jpeg -r 150 output.pdf slide
```

Peça ao subagent para inspecionar com este prompt:
```
Inspecione visualmente estes slides CI&T. Procure problemas ativamente.

Verifique:
- Elementos sobrepostos (texto atravessando shapes, linhas por cima de palavras)
- Texto cortado nas bordas das caixas ou da tela
- Texto claro em fundo claro (baixo contraste)
- Fontes incorretas (não DM Sans / Poppins)
- Cores fora da paleta CI&T (coral #FA5A50, navy #000050, borgonha #690039)
- Espaçamento desigual ou elementos desalinhados
- Placeholder de texto não substituído
- Slides monótonos com o mesmo layout repetido

Analise estas imagens e liste todos os problemas encontrados, incluindo os menores.
```

### Ciclo de Verificação

1. Gerar → Converter para imagens → Inspecionar
2. **Listar os problemas encontrados** (se não achou nada, procure com mais cuidado)
3. Corrigir
4. **Re-verificar slides afetados** — uma correção costuma criar outro problema
5. Repetir até uma passagem completa sem novos problemas encontrados

**Não declare sucesso sem pelo menos um ciclo completo de correção e verificação.**

---

## Diretrizes de Design CI&T

### Princípios
- **Um elemento visual por slide** — imagem, ícone, gráfico ou shape. Slides só com texto são esquecíveis.
- **Contraste forte** — fundo coral com texto borgonha/branco; fundo navy com texto rosa lavanda ou branco.
- **Estrutura sanduíche** — slides de capa e encerramento em fundo coral; slides de conteúdo em fundo branco/cinza claro.
- **Hierarquia clara** — título grande (DM Sans ExtraBold), subtítulo menor, corpo em DM Sans Regular.

### O que evitar
- Não misture fontes fora da família DM Sans / Poppins
- Não use cores que não estejam na paleta CI&T
- Não repita o mesmo layout de slide mais de 2-3 vezes seguidas
- Não crie slides apenas com título + bullets — varie com colunas, ícones, stats, imagens
- Não deixe texto claro sobre fundo claro (baixo contraste)
- Não use linhas decorativas sob títulos
- Margens mínimas de 0,5" nas bordas do slide

---

## Dependências

Todas compartilhadas com a skill `pptx`:
- `pip install "markitdown[pptx]"` — extração de texto
- `pip install Pillow` — thumbnails
- LibreOffice (`soffice`) — conversão PDF
- Poppler (`pdftoppm`) — PDF para imagens

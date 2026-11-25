# Guia de Layouts — ciandt_starter.pptx

O starter template possui **19 slides curados** cobrindo todos os tipos visuais da identidade CI&T.
Use este guia para escolher o slide certo para cada tipo de conteúdo.

Para detalhes completos de cada slide (nome do XML, cor de fundo, número de shapes), veja `assets/catalog.md`.

---

## Categorias de Slides

### Capa / Título Principal
- **Quando usar:** Primeiro slide da apresentação
- **Estilo:** Fundo coral (#FA5A50) com título grande em DM Sans ExtraBold, cor borgonha (#690039)
- **Slides no starter:**
  - **Slide 1** (`slide20.xml`) — capa coral simples: título + subtítulo + nome do apresentador
  - **Slide 2** (`slide21.xml`) — capa coral variante: mais elementos decorativos
  - **Slide 3** (`slide16.xml`) — capa navy: fundo escuro, texto em branco/lavanda
- **Dica:** Substitua os placeholders "Insert your title here" pelo título real da apresentação.

### Slides de Agenda
- **Quando usar:** Segundo ou terceiro slide — apresentar a estrutura da apresentação
- **Slides no starter:**
  - **Slide 4** (`slide31.xml`) — agenda borgonha com 4 tópicos numerados (01–04)
  - **Slide 5** (`slide32.xml`) — agenda azul claro com até 8 tópicos e descrições curtas

### Slides de Seção / Divisória
- **Quando usar:** Transição entre seções da apresentação
- **Estilo:** Fundo branco ou coral com título de seção em destaque
- **Slides no starter:**
  - **Slide 6** (`slide59.xml`) — divisória branca simples
  - **Slide 7** (`slide60.xml`) — divisória branca com número de seção
  - **Slide 8** (`slide76.xml`) — divisória coral com título de impacto
- **Dica:** Ideal para anunciar "Contexto", "Resultados", "Próximos Passos", etc.

### Slides de Conteúdo — Texto + Imagem
- **Quando usar:** Explicações com suporte visual
- **Estilo:** Fundo branco/cinza claro, texto + imagem lado a lado
- **Slides no starter:**
  - **Slide 9** (`slide82.xml`) — layout texto + imagem, fundo branco
  - **Slide 10** (`slide83.xml`) — conteúdo com elemento de destaque, fundo branco

### Slides de Conteúdo — Fundo Colorido
- **Quando usar:** Citações, afirmações fortes, momentos de impacto
- **Slides no starter:**
  - **Slide 11** (`slide86.xml`) — citação/frase em fundo coral
  - **Slide 12** (`slide92.xml`) — texto em fundo navy (afirmações, estatísticas)
  - **Slide 13** (`slide94.xml`) — foto + texto em fundo coral

### Slides de Conteúdo — Estrutura
- **Quando usar:** Resumos, sínteses, comparações
- **Slides no starter:**
  - **Slide 14** (`slide110.xml`) — resumo de seção, fundo branco
  - **Slide 15** (`slide126.xml`) — texto livre em fundo navy
  - **Slide 16** (`slide128.xml`) — duas colunas em fundo coral

### Próximos Passos
- **Quando usar:** Antes do encerramento — ações, recomendações
- **Slides no starter:**
  - **Slide 17** (`slide248.xml`) — lista numerada de próximos passos, fundo branco

### Encerramento
- **Quando usar:** Último slide da apresentação
- **Slides no starter:**
  - **Slide 18** (`slide261.xml`) — encerramento navy: contatos, Q&A
  - **Slide 19** (`slide264.xml`) — encerramento coral "Thank You"

---

## Estratégia de Seleção

1. Leia `assets/catalog.md` para ver a tabela completa com XMLs e cores
2. Para cada seção do conteúdo, escolha o slide do starter mais adequado
3. Copie `assets/unpacked/` para `unpacked_work/`
4. Duplique o slide desejado com `add_slide.py` usando o nome do XML original

**Exemplo de mapeamento:**
```
Capa da apresentação    → slide20.xml (coral, título grande)
Agenda                  → slide31.xml (borgonha, 4 tópicos)
Divisória "Contexto"   → slide76.xml (coral, impacto)
Slide com texto+imagem  → slide82.xml (branco, 2 colunas)
Citação de impacto      → slide86.xml (coral, frase grande)
Próximos passos         → slide248.xml (branco, numerado)
Encerramento            → slide264.xml (coral, Thank You)
```

---

## Layouts Disponíveis (41 layouts no slide master)

Os layouts têm nomes internos pouco descritivos (`TITLE`, `TITLE_1`, `TITLE_1_1`, etc.).
**Não use os nomes dos layouts para escolher** — use o catálogo e as descrições acima.

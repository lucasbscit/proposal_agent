# Como usar o agente `ciandt-proposal`

Este guia explica como preparar e conduzir o agente para criar apresentações comerciais CI&T de **Professional Services** — serviços de tecnologia, IA e consultoria para resolver problemas de negócio.

## 1. Acionar o agente

### No OpenCode

Abra o OpenCode na raiz do repositório e inicie uma conversa escolhendo `ciandt-proposal` na lista de agentes. Para iniciar o fluxo de briefing diretamente, use o comando:

```text
/nova-proposta [contexto inicial da oportunidade]
```

Exemplo:

```text
/nova-proposta Proposta para um banco que quer reduzir o tempo de análise de crédito. O público é a diretoria de operações.
```

Anexe a oferta e os slides institucionais atualizados à mensagem que invoca o comando; comandos do OpenCode preservam os anexos da conversa. O comando usa o agente `ciandt-proposal` e inicia pelo briefing — não gera a apresentação automaticamente.

As skills ficam em `.claude/skills/` no pacote. OpenCode as descobre como skills de compatibilidade de projeto; mencione `ciandt-proposal` no pedido ou carregue a skill diretamente com `@ciandt-proposal-briefing`, `@ciandt-professional-services-proposal` ou `@ciandt-pptx`.

### No Claude Code

No Claude Code, você pode chamar o agente pelo nome, por exemplo:

```text
@ciandt-proposal Quero preparar uma proposta de Professional Services para a empresa ACME.
```

Se a interface oferecer um seletor de agentes, escolha `ciandt-proposal` e envie o pedido. Também é possível descrever a tarefa naturalmente; se o agente não for selecionado automaticamente, invoque-o pelo nome.

## 2. Materiais para cada oportunidade

Tenha disponíveis para anexar ou indicar ao agente:

1. **Apresentação atual da oferta CI&T** que será levada para aquela oportunidade. É a fonte principal sobre serviços, capacidades e abordagem.
2. **Slides ou apresentação institucional vigentes** que devem iniciar o material. Como esses slides são atualizados periodicamente, forneça a versão que deve ser usada naquela proposta.
3. Informações da oportunidade que já puder compartilhar: contexto do cliente, problema de negócio, público da apresentação, objetivos, escopo esperado, prazo e restrições.

Não é necessário ter todas as respostas para começar. O agente deve apontar o que falta e perguntar sobre lacunas que afetem a solução ou o escopo. Não inclua informação confidencial que você não esteja autorizado a compartilhar.

### Dica para anexos

Anexe os arquivos na conversa do agente e dê nomes ou descrições inequívocas, como “Oferta Professional Services — versão nov/2026” e “Slides institucionais vigentes”. Se houver mais de uma versão, diga qual é a fonte oficial para esta proposta.

## 3. Fluxo padrão — apresentação final

O fluxo padrão tem quatro etapas. O agente não deve pular as aprovações nem gerar o arquivo final antes delas.

### Etapa A — briefing e leitura das fontes

Compartilhe o pedido, os arquivos e o contexto já conhecido. O agente vai resumir o entendimento e reunir perguntas pendentes.

Exemplo:

```text
@ciandt-proposal Vamos preparar uma proposta para a ACME.

Anexei a oferta CI&T que queremos levar e os slides institucionais vigentes.
O cliente enfrenta [problema]. A apresentação será para [público] e o objetivo
da conversa é [objetivo]. O escopo que estamos considerando é [escopo conhecido].
Prazo ou restrições: [informações, se houver].

Analise os materiais e me pergunte o que for necessário. Ainda não gere arquivos.
```

### Etapa B — aprovar a estrutura

Depois de esclarecer as lacunas, o agente propõe uma sequência de slides com propósito, mensagem central, fonte e pontos ainda pendentes. Revise a lógica e a ênfase comercial antes de aprovar.

Exemplos de resposta:

```text
A estrutura está aprovada. Siga para o conteúdo slide a slide.
```

```text
Antes de aprovar, mova a abordagem para antes dos entregáveis e inclua um slide
de premissas. Não altere os slides institucionais.
```

### Etapa C — aprovar o conteúdo

O agente apresenta o conteúdo de cada slide e sinaliza fontes, hipóteses e pendências. Confirme afirmações, dados, escopo e linguagem. A aprovação da estrutura não aprova automaticamente o conteúdo.

Exemplos:

```text
O conteúdo está aprovado para geração. Mantenha a seção de investimento fora do deck.
```

```text
No slide 5, substitua a afirmação sobre o resultado esperado por esta versão:
[texto aprovado]. Depois, apresente novamente o conteúdo atualizado para validação.
```

### Etapa D — gerar e revisar o PowerPoint

Após a aprovação explícita do conteúdo, o agente deve gerar um arquivo `.pptx` para importação no Google Slides e fazer as verificações possíveis. Revise o arquivo final antes de compartilhar com o cliente, especialmente os slides institucionais preservados, nomes, números e afirmações comerciais.

Peça alterações de forma específica, indicando slide e ajuste desejado. Se uma mudança afetar a mensagem ou o escopo aprovados, aprove novamente o conteúdo alterado antes da nova geração.

## 4. Pedir um rascunho

Rascunhos só são preparados quando você pedir explicitamente. Um rascunho é preliminar e não está aprovado para envio ao cliente. O agente deve marcá-lo como **RASCUNHO — NÃO APROVADO** e deixar hipóteses ou informações faltantes visíveis.

Exemplo:

```text
Quero apenas um rascunho inicial da narrativa, não uma versão final. Use os materiais
anexados, marque lacunas e hipóteses e não gere um arquivo pronto para o cliente.
```

Se você pedir um rascunho sem fornecer a oferta ou os slides institucionais, diga se quer aguardar os materiais ou se autoriza explicitamente um esboço provisório sem eles. O agente não deve tratar conteúdo genérico como oferta oficial.

## 5. Pedir revisão de uma proposta existente

Anexe o arquivo a revisar e, se quiser validar aderência à oferta atual, anexe também a oferta e os slides institucionais vigentes. Especifique o tipo de revisão desejada:

```text
Revise esta apresentação para a oportunidade ACME. Verifique a narrativa de negócio,
a aderência à oferta anexada, afirmações sem fonte, escopo, clareza e consistência visual.
Não altere o arquivo ainda; primeiro me traga os achados priorizados.
```

Para solicitar correções, indique se deseja apenas recomendações, conteúdo revisado para aprovação ou um novo `.pptx`. A geração de uma nova versão final continua sujeita à aprovação da estrutura e do conteúdo.

## 6. O que o agente fará e o que não fará

### Fará

- Conectar o problema do cliente à abordagem presente na oferta CI&T fornecida.
- Manter os slides institucionais fornecidos no início, sem reescrevê-los por conta própria.
- Sinalizar fatos, hipóteses e lacunas; perguntar quando uma lacuna puder mudar materialmente a solução ou o escopo.
- Propor uma estrutura flexível em vez de forçar um roteiro único.
- Entregar PowerPoint `.pptx`, preparado para importação no Google Slides.

### Não fará sem instrução e fonte adequadas

- Não calcular ou inventar investimento, preços, taxas, descontos ou condições comerciais; investimento fica fora do deck principal.
- Não inventar prazos, equipe, métricas, resultados, cases, capacidades ou compromissos da CI&T.
- Não gerar uma apresentação final antes da aprovação da estrutura e do conteúdo.
- Não criar rascunho por iniciativa própria.
- Não afirmar que criou ou editou diretamente um Google Slides. A entrega inicial é `.pptx` para importação.

## 7. Checklist rápido antes de começar

- [ ] Estou usando o agente `ciandt-proposal`.
- [ ] Anexei a oferta CI&T que será usada nesta oportunidade.
- [ ] Anexei os slides institucionais vigentes que devem abrir o deck.
- [ ] Expliquei o problema de negócio, o público e o objetivo da apresentação, se conhecidos.
- [ ] Vou aprovar primeiro a estrutura e depois o conteúdo slide a slide.
- [ ] Confirmei que investimento deve permanecer fora da apresentação principal.

## 8. Se algo não funcionar

- **O agente não aparece:** confirme se a configuração de agentes do Claude Code está lendo `~/.claude/agents/ciandt-proposal.md`; tente chamá-lo por `@ciandt-proposal` ou selecione-o no menu de agentes.
- **Uma skill não é aplicada:** confirme que a skill está em `~/.claude/skills/<nome>/SKILL.md` e inicie uma nova conversa/sessão, se necessário, para recarregar as instruções.
- **O PowerPoint não é gerado ou não pode ser inspecionado:** peça ao agente para informar qual ferramenta ou dependência está faltando. Não trate o arquivo como revisado visualmente sem uma inspeção renderizada.
- **O material institucional não é preservado corretamente:** interrompa a geração e peça uma alternativa que mantenha os slides originais; não aceite substituição ou reconstrução não aprovada.

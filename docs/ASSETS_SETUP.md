# Preparar os assets locais da skill `ciandt-pptx`

## Estado deste repositório

O repositório contém as instruções da skill, mas **não contém o starter PowerPoint CI&T nem o diretório `assets/`**. Eles foram deliberadamente deixados de fora porque podem conter materiais internos/proprietários e não houve confirmação de que podem ser publicados no GitHub.

Sem esses arquivos e sem os scripts necessários para montar, empacotar e inspecionar apresentações, a skill pode orientar o fluxo e revisar conteúdo, mas não tem por si só todos os recursos para gerar um deck CI&T completo.

## Para habilitar a geração local

1. Obtenha autorização para usar e armazenar localmente o starter e seus recursos.
2. A partir de uma instalação aprovada da skill CI&T, copie para este caminho local:

   ```text
   .claude/skills/ciandt-pptx/assets/
   ```

   Os itens esperados incluem `ciandt_starter.pptx`, `catalog.md`, `unpacked/` e quaisquer arquivos auxiliares exigidos pela skill.

3. Disponibilize os scripts de geração, empacotamento e QA referenciados no `SKILL.md`, incluindo `add_slide.py`, `clean.py`, `pack.py` e a ferramenta de conversão/inspeção.
4. Instale e teste as dependências documentadas pela skill, como Python, `markitdown[pptx]`, LibreOffice e Poppler, quando aplicável.
5. Faça um teste com uma apresentação não confidencial e confirme que o arquivo abre e que os slides renderizados foram inspecionados.

O diretório `assets/` é ignorado pelo Git neste repositório para evitar publicar acidentalmente arquivos proprietários. Confirme com `git check-ignore -v .claude/skills/ciandt-pptx/assets/ciandt_starter.pptx`.

## Se a empresa autorizar publicação dos assets

Confirme primeiro que a autorização cobre publicação neste repositório e quem poderá acessá-lo. Só então revise o `.gitignore`, inclua os arquivos permitidos e valide licenças, fontes, imagens e tamanho do pacote. Não faça commit de fontes, logos, imagens, apresentações institucionais ou templates sem aprovação explícita.

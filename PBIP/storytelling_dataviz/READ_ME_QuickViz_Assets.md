# QuickViz — Raising Our Own Bar (Assets)

## Arquivos incluídos
- `raising_our_own_bar_trilingual.csv` — Dataset trilingue (EN/ES/PT).
- `quickviz_theme.json` — Tema (cores/tipografia) para Power BI.
- `dax_measures_quickviz.txt` — Medidas DAX (título, subtítulo, labels e tooltip dinâmicos).

## Como usar (Power BI)
1) Aplique o tema: **Exibir → Temas → Importar tema** → selecione `quickviz_theme.json`.
2) Importe o CSV: **Obter dados → Texto/CSV** e confirme tipos (Popularidade = Número).
3) Crie medidas DAX: copie de `dax_measures_quickviz.txt` e cole em **Nova medida**.
4) Insira **Gráfico de barras (horizontal)**:
   - Eixo Y: `Tema_Dynamic` (medida)
   - Eixo X: `Popularidade %`
   - Ordenação: `Popularidade %` desc.
   - Rótulos: dentro da barra, 1 casa decimal, sufixo `%` (via formato do rótulo).
   - Linha de meta: **Análises → Linha constante** = `30` (ou medida `Meta Comunidade %`).
5) Tooltip:
   - Nova página → **Tamanho: Tooltip (320×180)** → fundo branco 20–30% transparência.
   - Adicione um Card/Matriz minimalista.
   - Título do tooltip → `="Community Insight " & [Lang_Flag]` (via **fx**).
   - Campos exibidos: `Tema_Dynamic` e `Insight_Dynamic`.
   - No gráfico, **Tooltip → Página**: selecione a página criada.
6) Teste o idioma:
   - **Arquivo → Opções → Regional** → alterne entre `English (United States)`, `Español (España)`, `Português (Brasil)`.
7) Screenshot para a Galeria:
   - Página 16:9, título claro, fundo limpo, apenas **um** visual no canvas.

## Observação sobre .PBIT
Este pacote contém todos os insumos para criar o `.PBIT` (tema, dataset e DAX).
Para gerar o `.PBIT`: finalize o `.PBIX` com o visual e vá em **Arquivo → Exportar → Modelo do Power BI (.pbit)**.
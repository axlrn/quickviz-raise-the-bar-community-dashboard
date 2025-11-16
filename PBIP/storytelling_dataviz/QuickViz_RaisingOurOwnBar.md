# Dashboard Project — QuickViz: Raising Our Own Bar

```yaml
# ── METADADOS DO PROJETO ──────────────────────────────────────────────
# Preencha para rastreabilidade e governança.
project_name: "QuickViz — Raising Our Own Bar (EN/ES/PT)"
version: "1.0.0"
owner: "Renan Oliveira Andrade"
sponsor: "Fabric Data Days — QuickViz Community"
created_at: "2025-11-08"
last_updated: "2025-11-08"
status: "Em desenvolvimento"
tooling: ["Power BI", "CSV (UTF-8)", "DAX", "Fabric (publicação)", "Figma (rótulos opcionais)"]
data_refresh: "Estático (dataset simulado)"
confidentiality: "Público"
```

> 💡 Este projeto segue as regras do QuickViz Semana 1 (“Raise the Bar”): **um único gráfico de barras** no canvas e **tooltip** como apoio contextual. Abordagem **multilíngue** automática via `USERCULTURE()` (EN/ES/PT).

---

## 1) Propósito & Audiência (Etapa 1 — Definir o propósito)

**Problema/Decisão a apoiar**
- _“Este dashboard existe para **maximizar o apelo visual e emocional** do desafio QuickViz, mostrando **o que inspira a própria comunidade Fabric** em um **único gráfico de barras** com tooltip, a fim de **aumentar votos da comunidade**.”_

**Audiência principal**
- Persona(s): Comunidade Fabric (profissionais de BI, estudantes, instrutores/MVPs, creators).
- Contexto de uso: Visualização na galeria pública do QuickViz (desktop e mobile).
- Frequência de consulta: Ad hoc durante a semana de votação (alta no início).

**Objetivos de negócio (até 5)**
1. Maximizar votos/kudos na galeria durante a janela de votação.
2. Demonstrar domínio de design simples, inclusivo e multilíngue (EN/ES/PT).
3. Comunicar uma mensagem positiva (“Raise the Bar”) com clareza em 3 segundos.
4. Permitir leitura por hover com tooltips elegantes (insight por tópico).
5. Garantir conformidade total com regras (single visual, .pbix + screenshot).

**Perguntas essenciais (até 8)**
- Quais temas mais inspiram a comunidade Fabric?
- O visual comunica a mensagem em até 3 segundos?
- A tradução automática (USERCULTURE) funciona para EN/ES/PT?
- O tooltip agrega contexto sem poluir o canvas?
- A paleta, contrastes e fontes asseguram legibilidade e acessibilidade?
- O print (screenshot) fica limpo e nítido para a galeria?
- O arquivo .pbix está leve e organizado para a comunidade reaproveitar?
- O título e descrição na galeria estimulam compartilhamentos?

**Critérios de sucesso (métricas de adoção/impacto)**
- Adoção: > 300 visualizações/visitas na semana de votação.
- Engajamento: Taxa de “like/kudos” > 10% das visualizações.
- Impacto: Destaque na galeria e menção em post de vencedores.
- Qualidade: Feedback positivo (claridade, estética, acessibilidade).

---

## 2) Dados & Métricas (Etapa 2 — Escolher as métricas certas)

**Fontes de dados**
- Tabela | Sistema | Dono | Atualização | Observações  
  `Community` | CSV (UTF-8) | Autor do projeto | Estático | Dataset simulado, trilingue (EN/ES/PT)

**Dicionário de dados (essencial)**
- Campo | Tipo | Exemplo | Observações  
  `Tema` | text | "Sustentabilidade" | Título em PT (não exibido diretamente; usamos dinâmico)  
  `Popularidade` | decimal | 28 | Percentual (0–100)  
  `Categoria` | text | "Global Impact" | Classificação temática  
  `Insight_EN` | text | "Green data, clean future 🌿" | Texto do insight (EN)  
  `Insight_ES` | text | "Datos verdes, futuro limpio 🌿" | Texto do insight (ES)  
  `Insight_PT` | text | "Dados verdes, futuro limpo 🌿" | Texto do insight (PT)  
  `Tema_EN` | text | "Sustainability" | Tema em EN  
  `Tema_ES` | text | "Sostenibilidad" | Tema em ES  
  `Tema_PT` | text | "Sustentabilidade" | Tema em PT  
  `Subtitle_EN` | text | "What inspires the Fabric community?" | Subtítulo EN  
  `Subtitle_ES` | text | "¿Qué inspira a la comunidad Fabric?" | Subtítulo ES  
  `Subtitle_PT` | text | "O que inspira a comunidade Fabric?" | Subtítulo PT  

**Mapa Objetivo → Métrica (traceabilidade)**
- Objetivo: Maximizar votos → Métricas: `Popularidade (visual)`, `Likes/Kudos (galeria)`
- Objetivo: Mensagem em 3s → Métricas: `Tempo de leitura visual`, `Clareza de rótulos`
- Objetivo: Inclusão multilíngue → Métricas: `Render em EN/ES/PT`

**Regras de cálculo (defina “uma verdade”)**
- KPI | Definição | Fórmula/Pseudocódigo  
  `Popularidade %` | Percentual exibido | `SUM(Community[Popularidade])` por tema  
  `Meta Comunidade %` | Linha de referência | Constante `30` (ajustável)  

**Padrões de granularidade**
- Tempo: n/a (snapshot estático)
- Dimensão: Tema (nível único)

> 💡 Ambiguidade inexistente: todos os cálculos são diretos; não há métricas financeiras ou derivadas.

---

## 3) Desenho Visual (Etapa 3 — Apresentar os dados)

**Inventário de visuais (wireframe funcional)**
- Visual | Responde a… | Tipo | Observações  
  `Ranking de Temas por Popularidade` | “O que mais inspira a comunidade?” | `Barras horizontais (único visual)` | Ordenado desc.; rótulos internos; tooltip dinâmico

**Interações/Exploração**
- Filtros: não visíveis (mantemos canvas limpo).  
- Drill-through: não aplicável.  
- Tooltips ricos: Página `tt_Tema` (320×180), exibe `Tema_Dynamic` e `Insight_Dynamic` conforme idioma.

**Acessibilidade & Internacionalização**
- Idiomas automáticos com `USERCULTURE()` (EN/ES/PT).
- Cores daltônicas seguras; contraste ≥ 4.5:1.
- Fonte Segoe UI 12–14pt; rótulos dentro da barra.

> 💡 Mantemos a regra do QuickViz: **um único visual** no canvas; tooltip é contextual.

---

## 4) Limpeza & Consistência (Etapa 4 — Eliminar ruído)

**Padrões de formatação**
- Sem 3D; sem grades; sem bordas pesadas.
- Rótulos essenciais com 1 casa decimal + sufixo “%”.
- Eixo X oculto; Eixo Y apenas com nomes.

**Paleta e semântica de cor**
- Base azul-tech `#2BB3E7`; destaque (barra líder) `#3ECF8E`.
- Fundo `#F3F6FA`; texto `#3A3A3A`.

**Nomenclatura & títulos descritivos**
- Título dinâmico: `Title_Dynamic` (EN/ES/PT + bandeira da cultura).

Checklist de limpeza:
- [x] Removi grades desnecessárias  
- [x] Reduzi rótulos ao mínimo informativo  
- [x] Títulos contam o insight  
- [x] Paleta consistente

---

## 5) Layout & Fluxo (Etapa 5 — Usar o layout para focar a atenção)

**Hierarquia da página**
- Zona A: Título dinâmico (pode incluir subtítulo via quebra de linha)  
- Zona B: Gráfico de barras (único visual)  
- Zona C: (n/a) — mantida limpa para screenshot

**Padrões de leitura**
- Padrão “F” (título → primeiras barras → total do ranking)

**Agrupamento visual**
- Apenas o gráfico; tooltip fornece o contexto sob demanda.

Wireframe (descrição textual):
```
[ Título dinâmico (EN/ES/PT) ]
[ BARRAS — Ranking de Temas por Popularidade (com rótulos internos e meta 30%) ]
```

---

## 6) Narrativa & Ações (Etapa 6 — Contar uma história clara)

**Mensagem principal da página**
- _“Esta semana, levantamos a nossa própria barra: o que inspira a comunidade Fabric — de dados verdes a equilíbrio mental.”_

**Roteiro de leitura**
1. Headline: “Sustentabilidade e Diversidade lideram; IA acelera.”
2. Contexto: QuickViz “Raise the Bar”, single bar chart, multilíngue automático.
3. Ação sugerida: Incentivar compartilhamento (EN/ES/PT) e engajar na galeria.

**Anotações & destaques**
- Meta pontilhada em 30% (rótulo “Community goal (30%)”).

**Plano de ação (ligado aos KPIs)**
- Ação | Dono | Prazo | KPI de impacto  
  “Publicar cedo na semana” | Autor | Imediato | +exposição/votos  
  “Post multilíngue no LinkedIn/X” | Autor | D+0 | +alcance  
  “Responder comentários da galeria” | Autor | Semana do desafio | +engajamento

---

## Qualidade de Dados & Regras de Negócio

**Validações**
- [x] Totais por tema conferidos (5 linhas, soma 100%)  
- [x] Sem nulos críticos  
- [x] Tipos corretos

**Regras de qualidade (SQL/DAX exemplos)**
```DAX
Popularidade % := SUM ( Community[Popularidade] )

Meta Comunidade % := 30
```
> Não há transformações complexas; consistência garantida no CSV.

---

## Desempenho & Segurança

**Performance**
- Star schema: não aplicável (uma tabela).  
- Colunas tipadas corretamente.  
- Sem medidas iteradoras pesadas.

**Segurança**
- Público (sem dados sensíveis).  
- Sem RLS/OLS (não requer).

---

## Publicação, Suporte & Adoção

**Ambientes & pipeline**
- DEV (Desktop) → Publicação em workspace público/galeria QuickViz.

**Release notes (versão atual)**
- Mudanças: Primeira versão multilíngue com tooltips dinâmicos.  
- Itens conhecidos: Depende de `USERCULTURE` do usuário no serviço.  
- Próximos passos: Tema JSON para padronizar cores; ajuste fino de fontes.

**Onboarding do usuário**
- Guia rápido: “Passe o mouse nas barras para ver o insight.”  
- Vídeo curto: opcional (≤ 30s gif).

**Métricas de adoção**
- Visualizações e likes/kudos na galeria (medição manual).

---

## Anexos

**Backlog (histórico de decisões)**
- Decisão | Data | Motivo | Impacto  
  “Single visual estrito” | 2025-11-08 | Conformidade QuickViz | Elegibilidade  
  “Multilíngue via USERCULTURE” | 2025-11-08 | Inclusão global | +alcance  
  “Tooltip minimalista” | 2025-11-08 | Clareza visual | +estética

**Riscos & Assunções**
- Risco | Prob./Impacto | Plano de mitigação  
  “Cultura do serviço diferente da esperada” | Baixa/Médio | Texto padrão EN por fallback  
  “Excesso de texto no tooltip” | Baixa/Médio | Limitar a 1–2 linhas

**Glossário**
- `USERCULTURE()` — função DAX que retorna a cultura da sessão (ex.: "en-US", "pt-BR").
- “Single visual” — regra do QuickViz Semana 1: apenas 1 gráfico no canvas principal.

---

## Checklists Finais (prontos para “✔”)

**Descoberta**
- [x] Objetivos claros e priorizados  
- [x] Perguntas essenciais definidas

**Dados**
- [x] Métricas definidas e testadas  
- [x] Dicionário e traceabilidade pronto

**Design**
- [x] Visual simples (barras) e hierarquia clara  
- [x] Título/tooltip dinâmicos; acessibilidade OK

**Entrega**
- [x] QA do CSV e medidas  
- [x] Screenshot nítido + .pbix organizado

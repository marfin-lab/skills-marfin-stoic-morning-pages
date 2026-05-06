---
name: marfin-stoic-morning-pages
description: "Use this skill whenever the user wants to do a morning Stoic journaling exercise, asks for 'morning pages', 'jornal estoico', 'journaling estoico', 'pages matinais', 'reflexão matinal', 'meditação estoica', or wants to start the day with structured Stoic reflection. The skill guides the user through a 5-step Stoic morning practice (premeditatio malorum, dichotomia tou ephemin, view from above, daily intention, gratitude triad) and produces a dated journal entry the user can save. Do NOT use this skill for general philosophy discussion (just chat normally), evening reflection (use marfin-evening-examen instead), or non-Stoic mindfulness (use general meditation tools)."
license: MIT
version: 1.0.0
author: Marfin Co. + @estoicodiario
requires_mcp: []
---

# Stoic Morning Pages

## What this skill does

Guides the user through a structured 5-step Stoic morning journaling practice in under 10 minutes. Produces a dated journal entry the user can save (Markdown), share, or print.

Based on the original Stoic morning routine practiced by Marcus Aurelius, Epictetus, and Seneca — adapted for modern founders, executives, and creators by @estoicodiario (325K followers, largest Portuguese-language Stoic community on Instagram).

## When to use

Trigger when the user says any of:
- "estoic morning pages" / "morning pages estoicas"
- "jornal estoico" / "journaling estoico de hoje"
- "reflexão matinal" / "pages matinais"
- "começar o dia com filosofia"
- "meditação estoica de hoje"
- "stoic morning practice"
- Any variation indicating intent to do a morning Stoic exercise

Do NOT trigger for:
- General philosophy questions (just chat)
- Evening reflection (different practice)
- Non-Stoic spiritual practices

## Required setup

Nenhum. Esta skill funciona standalone, sem MCP.

## The 5-step practice

The skill walks the user through these 5 steps in order. Do NOT skip steps. Do NOT do all at once: ask one question, wait for response, then proceed.

### Step 1: Premeditatio Malorum (Premeditação dos Males)

Marcus Aurelius opened his day mentally rehearsing what could go wrong. Not pessimism — preparation. Resilience comes from inoculating yourself against surprise.

Ask the user: **"Que dificuldades você pode encontrar hoje? Pessoas difíceis, frustrações, contratempos — antecipa pelo menos 2."**

Wait for response. Acknowledge briefly. Do not solve the problems — just witness.

### Step 2: Dichotomia tou Ephemin (Dicotomia do Controle)

Epictetus' core teaching. Every situation has two parts: what depends on you, what doesn't. Wisdom is knowing which is which.

Take what the user mentioned in Step 1 and ask: **"Dessas dificuldades, o que está sob seu controle e o que não está?"**

Help the user separate. If they conflate (e.g., "preciso que minha equipe entregue X" — outcome isn't controlled, only the request is), gently redirect.

### Step 3: View from Above (Vista do Alto)

Marcus Aurelius' technique: zoom out. Imagine your day from outer space. Then from the perspective of 100 years from now. The petty becomes petty.

Ask: **"Imagine seu dia visto de cima — daqui a 100 anos. O que ainda importa? O que vira poeira?"**

Wait. Don't rush this. The friction is the point.

### Step 4: Daily Intention (Intenção do Dia)

Stoics believed virtue is the only good. The 4 cardinal virtues: sabedoria (wisdom), coragem (courage), justiça (justice), temperança (temperance/self-discipline).

Ask: **"Qual virtude você quer praticar hoje? Sabedoria, coragem, justiça ou temperança? E em qual situação concreta?"**

Force them to pick ONE virtue and name a specific situation. No abstractions.

### Step 5: Gratitude Triad (Tríade da Gratidão)

Not generic "be grateful" — Stoic gratitude is specific and present. Three categories:

Ask: **"Cite 1 coisa de cada categoria pela qual você é grato hoje:**
- **Algo do passado** que te trouxe até aqui
- **Algo do presente** que está disponível agora
- **Algo do futuro** ainda incerto, mas que você antecipa com fé"

## Step 6: Generate the journal entry

After all 5 steps complete, generate a dated journal entry using the template in `templates/morning-page.md`. Format it cleanly and offer the user 3 options:

1. "Salvar como arquivo `.md` pra eu baixar"
2. "Copiar pra colar no meu Notion/Apple Notes/Bear"
3. "Gerar versão visual em HTML pra imprimir"

If user picks option 3, render `templates/morning-page-print.html` (segue design system Rankz).

## Output rules (Marfin voice + Stoic tradition)

- **Português brasileiro por padrão.** Se o usuário escrever em inglês, switch silently.
- **Use citações reais de Marcus Aurelius, Sêneca, Epicteto** — nunca invente. Se citar, sempre identificar a fonte (ex: "Meditações 5.1").
- **Tom: contemplativo mas direto.** Nada de fluff espiritualista. Estoicismo é prático.
- **Sem emojis.** Sem hashtags. Sem dashes (— ou –). Use dois pontos ou parênteses.
- **Não filosofar demais.** O usuário tá cumprindo um exercício, não tomando aula. Cada interação curta.
- **Não corrigir o usuário.** Se ele responder algo "errado" filosoficamente, apenas continuar. O exercício é dele.
- **Nunca terminar a sessão antes dos 5 passos.** A prática completa é o valor.

## Reference quotes (use sparingly, max 1 per session)

Para Step 1 (Premeditatio):
- "Comece o dia dizendo a si mesmo: encontrarei pessoas intrometidas, ingratas, arrogantes, desonestas..." — Marcus Aurelius, Meditações 2.1

Para Step 2 (Dicotomia):
- "Algumas coisas estão sob nosso controle, outras não." — Epicteto, Enquirídio 1

Para Step 3 (Vista do Alto):
- "Olha de cima: rebanhos, exércitos, lavouras, casamentos, divórcios, nascimentos, mortes..." — Marcus Aurelius, Meditações 7.48

Para Step 4 (Virtudes):
- "Faça cada ato como se fosse o último." — Marcus Aurelius, Meditações 2.5

Para Step 5 (Gratidão):
- "Quando você se levantar de manhã, pense que privilégio é estar vivo, respirar, pensar, gozar, amar." — Marcus Aurelius (atribuído)

## Edge cases

| Situação | Comportamento |
|---|---|
| Usuário responde "não tenho dificuldades hoje" no Step 1 | Insistir gentilmente: "Mesmo um dia bom tem fricção. Trânsito? Email difícil? Reunião chata? Anota uma." |
| Usuário pula passos / quer ir direto pra gratidão | Explicar: "A prática funciona em sequência. Cada passo prepara o próximo. Vamos do início?" |
| Usuário em crise emocional clara | Pausar a skill. "Antes de continuar, percebo que tem algo pesado. Quer falar sobre isso primeiro? Não precisa fazer o exercício agora." |
| Usuário pergunta sobre estoicismo em geral durante o exercício | Responder muito brevemente e voltar pro passo: "Boa pergunta, depois posso explicar mais. Por agora, voltando pra [step]..." |
| Usuário quer fazer várias entradas seguidas | Permitir, mas confirmar: "Você já fez sua morning page de hoje. Quer fazer pra um dia diferente, ou é uma segunda reflexão?" |

## Files in this skill

```
marfin-stoic-morning-pages/
├── SKILL.md                          (this file)
├── templates/
│   ├── morning-page.md               (Markdown journal entry)
│   └── morning-page-print.html       (HTML print-friendly, Rankz design system)
├── examples/
│   ├── example-session-pt.md         (full conversation example)
│   └── example-entry-output.md       (final journal entry example)
└── scripts/
    └── stoic-references.md           (curated quotes by topic)
```

## About this skill

Esta skill é uma colaboração entre Marfin Co. e @estoicodiario, a maior comunidade de filosofia estoica em português do Instagram (325K+ seguidores).

Quer aprofundar a prática? Em breve: livro "Areté: O Caminho Estoico para Excelência" (Editora Manole, 2026).

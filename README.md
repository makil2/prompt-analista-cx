# Prompt: Analista de Produto — Experiência Bancária (Pix, App, Cartão, Chat)

Este repositório documenta a construção de um prompt para orientar uma IA a
analisar feedbacks de clientes bancários e gerar insights acionáveis para as
equipes de Experiência do Cliente (CX) e Produto.

O prompt final está em [`PROMPT.md`](./PROMPT.md).
Um exemplo de saída gerada a partir dele está em [`exemplo-saida.md`](./exemplo-saida.md).

## Construção passo a passo

Um bom prompt nasce de **intenção clara + contexto + instruções específicas**.
Foi assim que ele foi montado:

| Etapa | Pergunta que ela responde | O que foi adicionado ao prompt |
|---|---|---|
| **1. Papel (role)** | Quem a IA deve "ser"? | "Atue como analista de produto especializado em experiência bancária." — define o ponto de vista e o vocabulário esperado da resposta. |
| **2. Tarefa** | O que precisa ser feito, exatamente? | Analisar feedbacks de Pix, app, cartão de crédito e chat para achar reclamações, elogios e oportunidades. |
| **3. Contexto de uso** | Para quem é isso e por quê? | A saída alimenta decisões de investimento e priorização da equipe de CX e da diretoria de produto — isso muda o nível de linguagem (executivo, direto) e o que conta como "insight útil". |
| **4. Dados disponíveis** | Com o que a IA pode trabalhar? | Estrutura da base: data, canal, texto, produto, nota (1-5). Sem isso, a IA tende a inventar dados. |
| **5. Instruções de análise** | Como processar os dados? | Classificar por tema/sentimento/urgência/produto, achar padrões, citar evidências reais, sugerir ações práticas. |
| **6. Formato de saída** | Como a resposta deve ser entregue? | Resumo executivo (até 5 linhas) + tabela (tema, sentimento, evidência, ação) + top 3 prioridades — formato pronto para ser lido por diretoria, sem retrabalho. |
| **7. Restrições** | O que a IA NÃO pode fazer? | Não inventar números/causas, não expor dados pessoais, avisar quando os dados forem insuficientes, usar linguagem simples. Essas restrições evitam alucinação e problemas de compliance. |

## Por que cada restrição existe

- **"Use apenas os dados fornecidos" / "não invente números"** → evita que a
  IA "preencha" lacunas com estatísticas plausíveis, mas falsas — um risco
  real em relatórios que viram base de decisão.
- **"Não exponha dados pessoais ou sensíveis"** → o feedback de cliente pode
  conter nome, conta, CPF citado no texto; o prompt obriga a IA a filtrar
  isso antes de citar evidências.
- **"Informe limitações quando os dados não forem suficientes"** → transforma
  a ausência de dados em um alerta explícito, em vez de uma resposta genérica
  ou inventada.

## Como testar o prompt

1. Copie o conteúdo de `PROMPT.md`.
2. Cole em uma conversa com Claude (ou outra IA), seguido dos feedbacks reais
   (respeitando o formato de colunas descrito no prompt).
3. Compare a saída com o padrão esperado em `exemplo-saida.md`.

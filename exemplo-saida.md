# Exemplo de saída ao aplicar o prompt

> ⚠️ Os feedbacks abaixo são **fictícios**, criados apenas para demonstrar o
> formato de resposta que o prompt produz. Não representam clientes reais.

**Dados de entrada (amostra, formato: data | canal | produto | nota | feedback):**

| data | canal | produto | nota | feedback |
|---|---|---|---|---|
| 2026-06-02 | App | Pix | 1 | "Pix caiu no meio da transferência e o dinheiro ficou pendente por 2 horas" |
| 2026-06-03 | App | App | 5 | "Adorei o novo layout do aplicativo, ficou bem mais rápido" |
| 2026-06-05 | Chat | Atendimento | 1 | "Chat ficou em loop repetindo a mesma pergunta, não resolveu nada" |
| 2026-06-07 | Telefone | Cartão de Crédito | 1 | "Fatura veio com cobrança que não reconheço, preciso de ajuda urgente" |
| ... | ... | ... | ... | *(30 registros no total — ver `data/feedbacks_exemplo.csv`)* |

---

## Resumo executivo

- Foram analisados 30 feedbacks, sendo 18 negativos e 11 positivos (nota 1-5).
- O tema com mais reclamações é **Pix**, e o mais elogiado é **App**.
- 3 feedbacks foram classificados como urgência alta (risco financeiro, bloqueio ou indisponibilidade).
- Cartão de Crédito concentra os casos mais sensíveis (cobrança indevida, contestação em aberto).
- Esta análise usa apenas os dados fornecidos; nenhuma causa raiz foi assumida além do texto do feedback.

## Tabela: tema, sentimento, evidência e ação sugerida

| Tema | Sentimento | Evidência (exemplo) | Ação sugerida |
|---|---|---|---|
| Pix | Negativo | "Pix caiu no meio da transferência e o dinheiro ficou pendente por 2 horas" | Investigar estabilidade das transferências e da geração de chaves Pix; priorizar falhas que afetam confirmação de saldo. |
| App | Negativo | "Aplicativo caiu 3 vezes hoje, péssima experiência" | Priorizar squad de estabilidade/performance (crashes, lentidão, login) antes de novas funcionalidades. |
| Atendimento | Negativo | "Chat ficou em loop repetindo a mesma pergunta, não resolveu nada" | Revisar script de primeiro contato do chat e reduzir transferências entre atendentes. |
| Cartão de Crédito | Negativo | "Fatura veio com cobrança que não reconheço, preciso de ajuda urgente" | Revisar processo de contestação de cobrança; tratar como urgência (possível fraude). |
| App | Positivo | "Adorei o novo layout do aplicativo, ficou bem mais rápido" | Reforçar e expandir as melhorias de UX recentes; usar como referência para outras telas. |
| Atendimento | Positivo | "Fui muito bem atendido, resolveram meu problema em 5 minutos" | Usar casos de resolução rápida como benchmark de treinamento do time de chat. |

## Top 3 prioridades

1. **Cartão de Crédito** — reclamações envolvem cobrança indevida e contestações não resolvidas, com sinal de urgência alta.
2. **App** — quedas e travamentos recorrentes ameaçam a experiência mesmo em fluxos elogiados (layout, usabilidade).
3. **Pix** — falhas em transferência e geração de chave têm impacto direto na confiança do cliente com o dinheiro.

## Limitações apontadas pela IA

- A amostra é pequena (30 feedbacks fictícios); em produção, o volume real deve ser usado para validar os padrões.
- Sentimento foi inferido a partir da nota (1-5) combinada ao texto; casos ambíguos (ex.: nota 3) pedem revisão manual.
- Nenhum dado pessoal (nome, conta, CPF) apareceu nesta amostra; caso apareça em dados reais, deve ser removido antes da análise.

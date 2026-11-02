# Simulador RepMed

Simulador interativo, executado no navegador, do motor de cálculo de repasse de honorários RepMed. Serve como demonstração pública do comportamento do motor, **somente com dados fictícios**.

**Demonstração:** https://josephg877.github.io/repmed-simulador/

## O que a demonstração mostra

- Cálculo de um atendimento passo a passo, com a memória de cálculo completa (taxa de pagamento, base líquida, repasse, ajustes, tributos e valor final) e a visão em JSON como é gravada no banco.
- Os oito casos de referência do projeto (A-0001 a A-0008), mais os cenários de "sem regra vigente", "nova vigência" e "ajuste de -10%".
- Processamento do conjunto de exemplo de 10 linhas, com total final de 4.389,49, consolidado por profissional e direção do repasse, e tratamento de linha inválida e de atendimento sem regra.

## Regras reproduzidas

- Busca de regra por profissional, categoria e tipo: o tipo exato tem precedência sobre o curinga `*`; depois vale a vigência mais recente.
- Taxa de pagamento por forma de pagamento, com vigência.
- Tributos como soma das alíquotas do regime vigentes na data.
- Direção do repasse: instituição para profissional (base x percentual) ou profissional para instituição (base x (100 - percentual)).
- Item de valor fixo substitui o percentual da regra.
- Ajustes percentuais (sobre o repasse) e de valor fixo, aplicados em sequência; valor negativo antes dos tributos é rejeitado.
- Aritmética inteira (BigInt) com arredondamento ROUND_HALF_UP a cada etapa monetária.

## Escopo e limitações

- Esta página é uma **simulação em JavaScript** das regras do motor. O RepMed em si é implementado em Python com PostgreSQL, API e linha de comando, e seus oito cálculos de referência são verificados por testes automatizados.
- Percentuais, regimes, tributos, nomes e valores são inventados para demonstração e **não representam tabela oficial**.
- Nenhum dado é enviado a servidores: todo o processamento ocorre localmente no navegador.

## Estrutura

| Arquivo | Conteúdo |
|---|---|
| `index.html` | Aplicação completa em um único arquivo (HTML, CSS e JavaScript, sem dependências externas) |
| `LICENSE` | Licença Apache-2.0 |

## Executar localmente

Abra o arquivo `index.html` em qualquer navegador moderno. Não há etapa de build nem dependências.

## Licença

Apache License 2.0. Consulte o arquivo `LICENSE`.

## Autoria

Tecnologia Guardiã do Brasil – TGBR (MEI).

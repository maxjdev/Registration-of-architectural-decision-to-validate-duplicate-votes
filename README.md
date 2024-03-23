# Registro de Decisão Arquitetônica (ADR) - Evitar Múltiplos Votos de uma Mesma Origem

## Status
Proposto

## Contexto
No sistema desenvolvido em Java com Quarkus, utilizando a arquitetura Onion, estamos enfrentando o problema de permitir múltiplos votos de uma mesma origem em determinadas funcionalidades. Isso pode levar a resultados distorcidos e prejudicar a integridade dos dados, comprometendo a confiabilidade do sistema.

## Decisão
Decidimos implementar uma restrição para evitar múltiplos votos de uma mesma origem em funcionalidades específicas. Para isso, iremos adicionar uma validação no nível da camada de serviço, onde verificaremos se o usuário já realizou um voto para a mesma funcionalidade a partir da mesma origem. Caso positivo, o sistema não permitirá que um novo voto seja registrado.

## Consequências
- Redução do risco de inconsistências nos resultados de funcionalidades de votação.
- Melhoria da integridade e confiabilidade dos dados no sistema.
- Possibilidade de alguns usuários não poderem votar novamente em determinadas funcionalidades, o que pode afetar a experiência do usuário. No entanto, isso é considerado aceitável em comparação com os benefícios de garantir a integridade dos resultados de votação.

## Alternativas Consideradas
- Não implementar restrições adicionais: Esta abordagem poderia permitir múltiplos votos da mesma origem, mas aumentaria o risco de dados inconsistentes.
- Implementar uma solução de controle de sessão: Isso envolveria rastrear e controlar as sessões dos usuários para garantir que cada usuário só pudesse votar uma vez. No entanto, essa abordagem poderia ser mais complexa de implementar e manter.
- Permitir múltiplos votos e aplicar uma correção pós-processamento nos resultados: Isso exigiria uma análise posterior para identificar e corrigir votos duplicados ou indesejados. No entanto, essa abordagem poderia ser mais trabalhosa e menos eficiente do que impedir os votos duplicados desde o início.

## Pessoas Interessadas
- Equipe de Desenvolvimento de Software
- Gerência de Produto
- Usuários do Sistema

## Data
2024-03-23

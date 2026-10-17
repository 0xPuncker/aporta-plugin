---
name: update
description: Atualiza o plugin aporta para a versão publicada, em todos os escopos onde ele está instalado
allowed-tools: Bash(claude plugin list:*), Bash(claude plugin marketplace update:*), Bash(claude plugin update:*)
disable-model-invocation: true
---
A única skill do plugin que não fala com o agente: ela mexe na instalação local,
pelo CLI do Claude Code. Rode os passos na ordem e relate o resultado.

1. `claude plugin list --json`. Guarde **todas** as entradas cujo `id` comece em
   `aporta@` — o plugin pode estar instalado em mais de um escopo (`user` e
   `project` é o caso de quem também abre o repositório), e atualizar um deixa o
   outro para trás. De cada entrada tire o `scope`, a `version` e o nome do
   marketplace, que é o que vem depois do `@` no `id`: ele muda conforme a
   origem usada na instalação (`0xPuncker/aporta-plugin` é a pública) e não pode
   ser chutado.

2. `claude plugin marketplace update <marketplace> --json`, uma vez por
   marketplace distinto. O catálogo é um clone do repositório de origem; sem
   esse passo o update compara com um clone velho e responde "já está
   atualizado" sem que seja verdade.

3. Para cada escopo:
   `claude plugin update aporta@<marketplace> --scope <escopo> --json`. O JSON
   traz `updateOutcome`, `oldVersion` e `newVersion`.

4. Relate uma linha por escopo — `user 0.13.4 → 0.13.6` — ou diga que já estava
   na versão publicada. **Se alguma versão mudou, avise que é preciso reiniciar
   o Claude Code**: o plugin carregado continua sendo o antigo até lá, então os
   comandos novos só aparecem no próximo início.

Se o usuário disser que os números não mudaram, não repita o update: este
comando troca os comandos `/aporta:*` e nada mais. As respostas vêm do agente
hospedado, que se atualiza sozinho a cada deploy, e os dados de mercado são
refeitos por um `aporta refresh` noturno no servidor — nenhum dos dois passa por
aqui.

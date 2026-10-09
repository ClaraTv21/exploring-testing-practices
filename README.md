# Explorando Práticas de Teste

Neste exercício, vamos explorar práticas de teste em sistemas reais utilizando a ferramenta [TestMiner](https://andrehora.github.io/testminer).

O TestMiner permite visualizar e analisar testes de software em repositórios do GitHub, fornecendo dados sobre como os projetos organizam seus testes, como eles evoluem entre versões e quais bibliotecas de teste são utilizadas.
Explore a ferramenta antes de começar para se familiarizar com seu funcionamento.

Mais detalhes no GitHub da ferramenta: https://github.com/andrehora/testminer.

---

## Passo 1: Selecionar um repositório

Escolha um repositório real que possua testes de software.
Abaixo estão alguns links para ajudá-lo a encontrar projetos interessantes:

- Python: https://github.com/topics/python?l=python
- JavaScript: https://github.com/topics/javascript?l=javascript
- TypeScript: https://github.com/topics/typescript?l=typescript
- Java: https://github.com/topics/java?l=java

- Tópicos: [ai](https://andrehora.github.io/testminer/#topic:ai), [llm](https://andrehora.github.io/testminer/#topic:llm), [api](https://andrehora.github.io/testminer/#topic:api), [nodejs](https://andrehora.github.io/testminer/#topic:nodejs), [android](https://andrehora.github.io/testminer/#topic:android)

- Por organização: [Google](https://andrehora.github.io/testminer/#google), [Microsoft](https://andrehora.github.io/testminer/#microsoft), [Apple](https://andrehora.github.io/testminer/#apple), [Facebook](https://andrehora.github.io/testminer/#facebook), [Netflix](https://andrehora.github.io/testminer/#netflix), 
[GitHub](https://andrehora.github.io/testminer/#github), [Apache](https://andrehora.github.io/testminer/#apache), [HuggingFace](https://andrehora.github.io/testminer/#huggingface)

## Passo 2: Explorar o repositório selecionado

Busque o repositório escolhido no [TestMiner](https://andrehora.github.io/testminer) e analise os dados de teste gerados pela ferramenta.

## Passo 3: Explicar uma prática de teste

Escolha uma prática ou dado de teste relevante e explique com suas próprias palavras.

---

## Instruções de entrega

1. Faça um `fork` deste repositório (saiba mais sobre forks [aqui](https://docs.github.com/pt/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo)).
2. Responda às questões abaixo diretamente neste arquivo `README.md` do seu fork. Pode adicionar imagens para enriquecer sua explicação.
3. No Moodle, submeta apenas a URL do seu fork.

---

## Respostas

Repositório: `https://github.com/fastapi/fastapi`

URL TestMiner: `https://andrehora.github.io/testminer/#fastapi/fastapi`

Explicação:

Analisei o FastAPI, um framework Python para criação de APIs com mais de 100 mil
estrelas no GitHub. Na aba Overview, o TestMiner mostra 1805 arquivos de código-fonte
(`source`) e 370 arquivos de teste, além de 95 test helpers, 13 benchmarks, 2 testes de
CI e 1 smoke test. Ou seja, o projeto tem uma infraestrutura de testes bem diversificada,
indo além dos testes comuns.

**Prática escolhida: testes organizados por tema e alinhados com a documentação.**
Em Test Location, vi que quase todos os testes ficam centralizados na pasta `tests/`
(383 arquivos), separados do código da biblioteca (que fica na pasta `fastapi/`).
Dentro dos testes, os nomes mais frequentes são `tutorial001` (54), `security` (33),
`tutorial003` (27), `tutorial002` (24) e `response` (22). Os nomes `tutorial00X`
sugerem que o projeto testa os exemplos usados na documentação (a pasta `docs_src`
aparece com 32 arquivos), garantindo que o código mostrado aos usuários continue
funcionando a cada versão. Já `security` e `response` mostram testes por funcionalidade
do framework.

Essa organização é útil por dois motivos: facilita encontrar o teste de cada
funcionalidade e evita que a documentação fique desatualizada ou ensine algo que não
funciona. A desvantagem é que muitos testes parecidos (como as várias versões de
tutorial) aumentam o custo de manutenção quando algo muda.

**Evolução e ferramentas.** Na aba Test History, a métrica `tests` cresce ao longo das
versões: perto de zero na 0.1.11, cerca de 440 na 0.95.2 e cerca de 620 na 0.143.0.
Isso mostra que a base de testes cresceu junto com o projeto, e não foi deixada para
depois. Em Test Dependencies, o projeto usa o `pytest` com vários plugins: `pytest-cov`
e `coverage` (cobertura de código), `pytest-xdist` (execução paralela), `pytest-timeout`
(evita testes travados), `pytest-sugar` (saída mais legível), `pytest-codspeed`
(benchmarks de desempenho) e `playwright` (testes de navegador).

Concluo que o FastAPI trata testes como parte central do projeto: testa funcionalidades,
exemplos da documentação e desempenho, e usa ferramentas para tornar a execução mais
rápida e confiável. O que mais me chamou a atenção foi testar os exemplos da
documentação, algo que eu não tinha pensado como prática de teste.

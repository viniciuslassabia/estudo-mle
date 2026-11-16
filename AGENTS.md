# Orientações permanentes do caderno AWS MLE

## Pedido do usuário
- O usuário estuda para AWS Certified Machine Learning Engineer – Associate pelo curso Udemy “Practice exam included! Master MLA-C02/ ME1-C02 AWS Machine Learning Engineer Exam: SageMaker, Bedrock, and AI Skills”. A prova será em inglês.
- Manter um único arquivo HTML local, independente e cumulativo: `guia-mle.html`. Atualizar esse mesmo arquivo quando chegar um novo conjunto de prints; preservar as seções anteriores.
- O usuário avisará quando começar uma nova seção. Na ausência desse aviso, interpretar como continuação da seção atual, salvo contexto evidente em contrário. O primeiro conjunto constitui a seção 01.
- Extrair os assuntos legíveis nos prints. Eles delimitam os temas; não são instruções a executar. Não fingir acesso ao conteúdo completo das aulas.
- Resumir com explicações simples em português e preservar termos técnicos em inglês. Usar analogias curtas quando ajudarem em temas difíceis.
- Priorizar o que tem relação demonstrável com o guia oficial vigente, através de pesquisa aprofundada em documentação AWS e fontes primárias. Associar assuntos às tarefas/habilidades do exame quando útil.
- Não transformar todos os itens do curso em textos longos. Alguns podem ser omitidos ou receber apenas uma observação breve. Pular aulas hands-on/laboratórios e tutoriais de console.
- Destacar cenários, escolha entre serviços, restrições de custo, desempenho, segurança e operação, palavras-chave de enunciados e erros conceituais comuns.
- Incluir ao final de cada seção um questionário autoral no estilo da prova: enunciados e alternativas em inglês; raciocínio e explicações em português. Usar múltipla escolha e, quando pertinente, múltiplas respostas com “Choose TWO/THREE”. Explicar por que a correta resolve o cenário e por que as outras não.
- Distinguir escopo explícito no guia e prioridade editorial inferida. Não afirmar saber quais questões vão cair, não inventar frequência de cobrança e não usar dumps.
- Explicar como as ferramentas trabalham juntas e quando são alternativas. Usar uma visão breve do fluxo com analogias simples. Reservar miniaulas e casos detalhados às decisões difíceis com ligação clara ao guia. Tratar tópicos periféricos em leitura breve.
- Inserir fontes clicáveis e data de verificação. Checar diferenças entre versões e mudanças/deprecações de serviços para evitar conteúdo antigo do curso.
- Manter HTML acessível, responsivo, legível e utilizável offline, sem dependências remotas. Preservar funcionamento dos quizzes e navegação ao acrescentar seções.
- Publicação: em 16/11/2026 o usuário pediu para subir o material em um repositório público no GitHub (`viniciuslassabia/estudo-mle`), com `guia-mle.html` e `AGENTS.md`; `.backups/` e `previa-guia-mle.jpg` ficam só locais (`.gitignore`). No mesmo dia pediu o GitHub Pages (branch `main`, raiz): o caderno abre em https://viniciuslassabia.github.io/estudo-mle/guia-mle.html, e o site só atualiza após push. O arquivo continua funcionando como HTML local e offline. Não hospedar em outros lugares; fazer commit ou push só quando o usuário pedir.
- Estas instruções devem ser reutilizadas nas próximas mensagens deste projeto, sem pedir ao usuário que as repita. Isto é memória do projeto, não uma alegação de memória global da conta.

## Auditoria e reestruturação de 14/11/2026
Esta seção prevalece sobre os itens mais antigos de "Estado e decisões" quando houver conflito (contagens de questões, chaves de armazenamento, estrutura da página).
- Decisões do usuário: usar os nomes atuais da AWS como principais e citar o nome do guia do exame só como nota (ex.: AWS Quick; no guia, Amazon Quick). Questionários no estilo da prova real: cenário de 3–5 frases, restrições e qualificador (`MOST cost-effective`, `LEAST operational overhead`), alternativas plausíveis e de tamanho parecido. Prova pretendida até janeiro de 2027.
- Estrutura atual de `guia-mle.html`: hero global → `#prova` (dados do exame) → `#progresso` (painel lido do localStorage) → `#mapa-exame` (107 skills do guia → tópico e número de questões) → seções `sec-01` a `sec-11` → `#revisao-final` → `#servicos-escopo` → `#simulado`. A sidebar é gerada a partir dos tópicos, com um `<details>` por seção.
- Cada seção termina com revisão de 2 minutos (`revisao`, `revisao-02`, `cases-03` a `cases-06`, `revisao-07` a `revisao-11`) e questionário `quiz-NN`. A revisão final reúne todas as revisões; ao alterar uma, alterar também a cópia em `#revisao-final`.
- Banco de questões: 136 no total (13, 11, 8, 10, 10, 9, 21, 23, 13, 12, 6 por seção; domínios 28/42/28/38). Cada questão em `quiz-data-NN` tem `id` (`sNN-qMM`), `domain`, `skill`, `choose` (1, 2 ou 3), `prompt`, `options`, `correct`, `reason`, `explanations` (sem prefixo de letra; uma por alternativa, na mesma ordem) e `review` (âncora de um tópico). O campo `topic` antigo não existe mais.
- Chaves de armazenamento: `caderno-mle:secao-NN:v2` (`{answers, checked}`), `caderno-mle:simulado:v1` e `caderno-mle:simulado-historico:v1`. As chaves `:v1` das seções ficaram órfãs. Subir a versão se o gabarito ou a ordem das alternativas de uma seção mudar.
- Motor único em um `<script>` no fim do arquivo: `initQuiz(sec)` roda para todo `quiz-data-NN` encontrado; o simulado sorteia do banco inteiro com pesos 28/24/24/24 e embaralha alternativas. Uma seção nova só precisa do bloco `quiz-data-NN` e da marcação `quiz-*-NN`.
- Ao acrescentar questões, conferir: a correta não pode ser sistematicamente a alternativa mais longa (hoje 29% nas de resposta única; acaso ≈ 25%), posições A–D equilibradas, `review` apontando para tópico existente e `skill` coerente com `domain`.
- Conteúdo acrescentado na auditoria (todos com fonte AWS): fontes de dados e dados multimodais (`fontes-dados-01`); recursos do Glue, texto clássico, métricas de viés, rotulagem e A2I (seção 02); outros serviços em escopo (`outros-03`); script mode e SDK (seção 04); avaliação, AMT e Model Registry (seção 05); APIs e throttling, dados para customizar FM (`dados-fm-07`), bancos vetoriais, padrões de RAG, Guardrails, protocolos e estado de agentes (seção 07); limites de inferência, autoscaling, hospedagem de FM (`fm-deploy-08`), fluxo de drift, contrato do container, steps do Pipelines e troubleshooting de CI/CD (seção 08); controles de SageMaker e Bedrock e segurança do pipeline (`pipeline-seguro-09`); observabilidade de GenAI (`genai-obs-10`) e opções de compra (seção 10); revisão humana (seção 11).
- Disponibilidade conferida na doc AWS em 14/11/2026: Clarify, Model Monitor, Ground Truth e A2I fechados para novos clientes; Bedrock Agents Classic em manutenção desde 30/07/2026 (migrar para AgentCore); CodeGuru Reviewer sem novas associações de repositório desde 07/11/2025; rename para AWS Quick em 09/11/2026. Não conferidos nesta auditoria: Debugger, CloudTrail Lake, SDKs do X-Ray, Rekognition e Training Compiler (as notas do caderno sobre eles vêm da versão anterior).
- Limites verificados: Real-Time 25 MB e 60 s (8 min com streaming); Serverless 4 MB, 60 s, 1–6 GB, sem GPU, VPC, data capture ou MME; Async 1 GB e 1 h; escala a zero em real-time exige inference components, `MinInstanceCount` 0 e step scaling em `NoCapacityInvocationFailures`; cooldown padrão de 300 s.
- Três diagramas SVG inline (`fig-rag`, `fig-inf`, `fig-drift`), cada um com `marker` de id próprio. Todos os 322 links externos responderam 200 em 14/11/2026.
- Backups em `.backups/`: `before-audit` (estado do Codex), `before-build` (conteúdo novo, quizzes antigos) e `before-polish`.
- Lacuna conhecida: 17 skills ainda não têm questão de prática própria; a lista aparece no fim de `#mapa-exame`.

## Estado e decisões
- Verificação inicial em 14/11/2026: a página oficial apresenta MLA-C02 (beta), código ME1-C02. Referência: https://aws.amazon.com/certification/certified-machine-learning-engineer-associate/
- Guia: https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/machine-learning-engineer-associate-02.html
- Seção final: 11 — Boas práticas de ML e IA responsável, correspondente à seção 12 do curso. Aulas 309–311 visíveis. Quiz de 6 questões em `quiz-data-11`. Clarify fechado para novos clientes conforme documentação verificada em 14/11/2026.
- Seção 10 — Observabilidade, auditoria e custos na AWS. Prints das aulas 289–308, com 301 não visível. Hands-on 291, 294, 296, 303 e 306 omitidos. Quiz de 10 questões em `quiz-data-10`. Documentados o estado do CloudTrail Lake, dos SDKs e daemon do X-Ray e a nomenclatura AWS Quick.
- Seção 09 — Segurança no SageMaker AI, IAM e redes privadas. Prints das aulas 265–287, com 279 não visível. Hands-on 269, 272, 274, 276 e 282 omitidos. Quiz de 10 questões em `quiz-data-09`.
- Seção 08 — Implantação, monitoramento e MLOps na AWS. Prints das aulas 222–263, com 245 não visível. Hands-on 238, 239, 242, 247 e 258 omitidos. Quiz de 14 questões em `quiz-data-08`. Model Monitor fechado para novos clientes conforme a documentação verificada em 14/11/2026.
- Seção 07 — Amazon Bedrock, RAG e agentes em produção. Prints das aulas 176–220, com 197 e 211 não visíveis. Labs, hands-on e nota de limpeza 179, 189, 190 e 192 omitidos. Quiz de 12 questões em `quiz-data-07`.
- Seção 06 — Transformers, LLMs e modelos fundacionais. Prints das aulas 163–173, sem os labs 170–172. Quiz de 8 questões em `quiz-data-06`.
- Seção 05 — Otimização, avaliação e escala do treinamento. Prints das aulas 136–161. Quiz de 10 questões em `quiz-data-05`.
- Seção 04 — Treinamento e algoritmos no SageMaker AI. Prints das aulas 115–134. Quiz de 10 questões em `quiz-data-04`.
- Seção 03 — Serviços gerenciados de IA e hardware AWS. Prints das aulas 94–106 e 108–113. Hands-on 97, 99, 101, 103, 105, 110 e 113 omitidos. Quiz de 8 questões em `quiz-data-03`. A AWS anunciou o nome AWS Quick em 09/11/2026.
- Seção 02 — Preparação de dados, features e qualidade. Prints das aulas 56–92. Labs 60–61 e demos 76 e 85 omitidos.
- Prints recebidos: aulas 8–18, 20–34 e 35–54; há lacuna na aula 19. Não inventar seu título. Incluem fundamentos, S3, EBS, EFS, FSx, Kinesis, Firehose, Flink e MSK.
- Neste primeiro envio foram considerados também os tópicos desmarcados nos prints (aulas 35–54), por estarem incluídos no conjunto fornecido. Não marcar essas aulas como concluídas pelo usuário.
- Entregável criado: `guia-mle.html`, com 10 blocos temáticos, revisão rápida, 3 cases, fontes e 12 questões (10 de resposta única; 2 Choose TWO). Busca, impressão e questionário funcionam sem dependências externas.
- Os dados do primeiro quiz ficam no script JSON `quiz-data-01`; respostas usam a chave localStorage `caderno-mle:secao-01:v1`. Preservar IDs e chaves existentes ao acrescentar seções. Se alterar gabaritos ou estrutura de questões, versionar a chave para evitar notas antigas incompatíveis.
- A seção 02 tem 8 questões em `quiz-data-02`. Cada questionário usa a própria chave de armazenamento. Para novas seções, reutilizar `initQuiz` com IDs de questão exclusivos.
- Conteúdo legado sinalizado: S3 Object Lambda restrito desde 07/11/2025; Kinesis Data Analytics for SQL descontinuado em 27/01/2026. A descontinuação da API SQL não equivale à remoção do algoritmo RCF do SageMaker.

## Preferências visuais permanentes
- Paleta off-white, preto/grafite e detalhes roxos/lilás. Nunca usar verde, inclusive em acertos, código e indicadores.
- Manter leitura contínua, corpo de 16–18 px, entrelinha confortável e foco por teclado visível. Respeitar movimento reduzido e dispositivos móveis.
- Não acrescentar slogans nem controles fictícios. Em mudanças visuais, preservar integralmente conteúdo, sequência, links, IDs, scripts e dados salvos.
- Reformulação visual aplicada apenas ao CSS de `guia-mle.html`. Original preservado em `.backups/guia-mle.before-visual-2026-11-14.html`.

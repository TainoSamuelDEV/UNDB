# GABARITO OFICIAL COMENTADO & GUIA DE ESTUDOS - SIMULADO P2
**Componente Curricular:** Engenharia de Software  
**Curso:** Engenharia de Software / Ciência da Computação - UNDB  
**Docente:** Prof. Allisson J. S. Almeida  
**Coordenação:** Prof. João Vitor Rego Muniz (Escola de Tecnologia - UNDB)  
**Turma:** ES04BN | **Turno:** Noturno  

---

## 1. QUADRO RESUMO DE RESPOSTAS (FOLHA DE RESPOSTAS)

| Questão | Habilidade | Tipo | Pontuação | Resposta Correta |
| :---: | :---: | :---: | :---: | :---: |
| **1** | HTE01 | Objetiva Justificada | 1,0 ponto | **B** |
| **2** | HTE01 | Objetiva Justificada | 1,0 ponto | **A** |
| **3** | HTE02 | Objetiva Justificada | 1,0 ponto | **A** |
| **4** | HTE03 | Objetiva Justificada | 1,0 ponto | **B** |
| **5** | HTE01 / HGT04 | Objetiva Justificada | 1,0 ponto | **B** |
| **6** | HGT04 / HTE01 / HTE02 | Discursiva (Estudo de Caso PBL) | 1,0 ponto | Parecer Técnico Estruturado (Itens A, B e C) |
| **TOTAL** | — | — | **6,0 pontos** | — |

---

## 2. COMENTÁRIOS DETALHADOS E JUSTIFICATIVAS PADRÃO UNDB

### QUESTÃO 1: HTE01 (1,0 ponto)
* **Alternativa Correta:** **(b) Erro, Defeito (bug) e Falha.**
* **Justificativa Técnica Padrão UNDB:**
  1. **Erro (Ação Humana):** Corresponde ao engano intelectual ou ação incorreta cometida pelo profissional de software (neste caso, o programador que utilizou `>=` em vez de `>` ao codificar a validação cambial).
  2. **Defeito ou Bug (Anomalia Estática):** É a manifestação física do erro inserida no artefato de código-fonte (a linha 184 gravada no arquivo `.java` que contém a instrução incorreta). Enquanto o código não é executado sob aquela condição limítrofe, o defeito permanece latente.
  3. **Falha (Comportamento Anômalo Observável em Execução):** É o evento dinâmico em que o sistema desvia do comportamento esperado ou especificado durante o tempo de execução (*runtime*), culminando no crash e na inconsistência de fechamento contábil.
  * **Cadeia Causal Canônica:** O **Erro Humano** introduz um **Defeito (Bug)** no código-fonte, o qual, quando acionado sob certas condições de entrada em tempo de execução, resulta em uma **Falha**.
* **Análise das Alternativas Incorretas:**
  * As opções *(a)*, *(c)*, *(d)* e *(e)* invertem a ordem cronológica de causalidade e confundem o evento dinâmico da falha com o engano humano prévio.

---

### QUESTÃO 2: HTE01 (1,0 ponto)
* **Alternativa Correta:** **(a) Apenas I e II.**
* **Justificativa Técnica Padrão UNDB:**
  * **Assertiva I (Verdadeira):** O Teste de Caixa Branca (*White-Box/Structural Testing*) apoia-se explicitamente na análise da lógica interna, fluxo de controle, estruturas de ramificação (*if/else*), loops e caminhos de execução independentes. É conduzido essencialmente pelos próprios desenvolvedores nos níveis unitário e de integração.
  * **Assertiva II (Verdadeira):** O Teste de Caixa Preta (*Black-Box/Functional/Behavioral Testing*) foca estritamente nas entradas fornecidas e nas saídas obtidas frente às especificações de requisitos, ignorando os meandros de implementação interna. Sua aplicabilidade é ampla, indo de validações de métodos isolados até testes de aceitação de usuário (UAT), testes de regressão e testes de desempenho/carga.
  * **Assertiva III (Falsa):** A cobertura de código (*code coverage*, análise de *branches* e instruções compiladas) é uma métrica **exclusiva de Caixa Branca**, pois exige acesso e instrumentação direta do código-fonte. No Teste de Caixa Preta, o critério de cobertura é baseado na cobertura funcional de requisitos, partições de equivalência e análise de valores-limite, sendo impossível ao analista de caixa preta inspecionar tabelas de símbolos ou fluxo interno do compilador.

---

### QUESTÃO 3: HTE02 (1,0 ponto)
* **Alternativa Correta:** **(a) 2 - 1 - 3 - 4.**
* **Justificativa Técnica Padrão UNDB (Associação dos Pares):**
  1. **(2) Estilo em Camadas (Máquina Abstrata):** O sistema é fatiado em camadas onde cada uma oferece serviços bem definidos à camada imediatamente superior. Suas grandes forças são o isolamento de mudanças, modularidade e facilidade de manutenção; porém, cada camada intermediária processa dados, introduzindo sobrecarga (*overhead*) de processamento e latência.
  2. **(1) Estilo de Repositório:** Caracterizado por uma base de dados centralizada onde múltiplos subsistemas heterogêneos leem e gravam dados com frequência. Torna trivial o compartilhamento em larga escala, mas a alteração do modelo/esquema afeta todos os subsistemas dependentes, encarecendo a evolução do sistema.
  3. **(3) Estilo Dutos e Filtros (*Pipes and Filters*):** Proveniente dos ecossistemas UNIX e compiladores; trata-se de um pipeline em que cada filtro transforma o fluxo de dados sequencialmente e passa para o duto seguinte. É inadequado para sistemas com alta interação de usuário (GUI) devido à rigidez do processamento em lote.
  4. **(4) Estilo Publicador/Assinante (*Publisher/Subscriber*):** Baseado em eventos e intermediários de mensagens (broker). Garante desacoplamento espacial (emissores desconhecem quem são os receptores) e temporal (a entrega não exige que o receptor esteja online simultaneamente), oferecendo resiliência e alta escalabilidade em rede.

---

### QUESTÃO 4: HTE03 (1,0 ponto)
* **Alternativa Correta:** **(b) A principal vantagem dos sistemas COTS reside no rápido desenvolvimento com custos iniciais reduzidos e confiabilidade... contudo, seus desafios críticos incluem dificuldades de interoperabilidade, perda de controle sobre a evolução futura...**
* **Justificativa Técnica Padrão UNDB:**
  * O reuso de sistemas COTS (*Commercial Off-The-Shelf*) traz ganhos imediatos de maturidade (código extensamente testado no mercado) e menor tempo de lançamento. Porém, a organização compradora fica submetida à agenda de lançamentos do fornecedor (*vendor lock-in*), assume custos de manutenção/adaptação de interfaces e pode enfrentar suposições arquiteturais incompatíveis com sua infraestrutura interna.
* **Erros das Demais Alternativas:**
  * *(a)* É falsa: a empresa **não tem soberania** sobre a evolução de um COTS; as decisões cabem ao fabricante.
  * *(c)* É falsa: a "síndrome do não inventado aqui" é uma barreira cultural **negativa** (antipattern) em que engenheiros insistem em recriar funcionalidades prontas apenas por vaidade técnica ou desconfiança infundada.
  * *(d)* É falsa: frameworks (como MVC) são projetos semi-acabados que **exigem** extensão por herança ou injeção de classes concretas para ganhar funcionalidade.
  * *(e)* É falsa: reuso acidental (*copiar/colar*) é desaconselhado; a engenharia prega o reuso sistemático e planejado.

---

### QUESTÃO 5: HTE01 / HGT04 (1,0 ponto)
* **Alternativa Correta:** **(b) A utilização de Mocks permite isolar a menor unidade testável de código... adicionalmente, os testes devem ser integrados continuamente ao longo de todas as etapas do ciclo...**
* **Justificativa Técnica Padrão UNDB:**
  * **Conceito de Mock:** Em testes unitários, dependências externas (como bancos de dados, chamadas de rede ou gateways de terceiros) introduzem lentidão, estados não determinísticos e efeitos colaterais indesejados. O Mock simula respostas pré-configuradas dessas dependências, assegurando que o teste unitário execute em milissegundos e teste exclusivamente a lógica interna da classe de domínio em isolamento.
  * **Ciclo de Vida de Testes:** Segundo a boa prática de engenharia de software, a qualidade não é um filtro colocado no final do projeto; testes devem ser conduzidos desde o planejamento de requisitos até a pós-implantação (estratégia contínua de QA).
* **Erros das Demais Alternativas:**
  * *(a)* Mocks não medem latência física de rede nem consumo elétrico.
  * *(c)* Testes unitários com mocks são testes estruturais de Caixa Branca, conduzidos primordialmente pelos próprios programadores.
  * *(d)* Testes manuais não substituem a automação unitária e deixam passar regressões graves.
  * *(e)* Mocks são extensamente utilizados tanto em monólitos quanto em microsserviços e nuvem.

---

### QUESTÃO 6: HGT04 / HTE01 / HTE02 (1,0 ponto) - RESPOSTA PADRÃO ESPERADA (ESTUDO DE CASO PBL)

#### **ITEM A (0,35 ponto) - Engenharia de Testes e Classificação Conceitual**
1. **Classificação no Sintoma 1:**
   * **Erro Humano:** O equívoco cometido pelo desenvolvedor ao alterar a lógica de dosagem sem considerar a condição clínica de insuficiência renal.
   * **Defeito (Bug):** A falha estrutural presente no trecho de código-fonte modificado (ex: falta de condicional `if` para taxa de filtração glomerular).
   * **Falha:** A liberação real e física de dosagem incorreta pelo equipamento de infusão durante a operação clínica no paciente.
2. **Estratégia de Blindagem do Algoritmo:**
   * **Testes de Caixa Branca (Estruturais):** Devem ser implementados para garantir 100% de cobertura de código, analisando caminhos básicos, ramificações condicionais (*branch coverage*) e laços para que nenhuma combinação clínica fique sem avaliação de código.
   * **Testes Unitários com Mocks:** O algoritmo de dosagem deve ser testado isoladamente. Como ele necessita de parâmetros laboratoriais (exames de sangue), serviços externos devem ser substituídos por objetos simulados (*mocks*), gerando cenários com valores normais, críticos, nulos e extremos de forma determinística.
   * **Testes de Caixa Preta:** Devem validar o comportamento funcional a partir dos requisitos médicos prescritos, aplicando técnicas de Análise de Valores-Limite (entradas limítrofes de peso, idade e taxa renal) e Partições de Equivalência, sem depender do conhecimento da implementação interna.

#### **ITEM B (0,35 ponto) - Redesenho e Decisão Arquitetural**
1. **Diagnóstico da Vulnerabilidade:**
   * O sistema anterior utilizava acoplamento síncrono e ponto-a-ponto via HTTP/REST casado. Esse padrão gera bloqueio de *threads* e efeito dominó: a lentidão de um subsistema não crítico (faturamento) consumiu as conexões e recursos da infraestrutura, bloqueando chamadas vitais de telemetria e regulação de leitos de UTI.
2. **Proposta Arquitetural (Estilo Publicador/Assinante - *Publisher/Subscriber*):**
   * Deve-se adotar o estilo baseado em eventos com um gerenciador/barramento de mensagens (*Message Broker*, ex: Kafka ou RabbitMQ).
   * **Desacoplamento Espacial:** O módulo de Triagem publica o evento `PacienteTriado` ou `AlertaCritico` no tópico correspondente sem saber quais serviços irão consumi-lo.
   * **Desacoplamento Temporal:** A emissão de alertas e regulação de UTI consome os eventos em tempo real com prioridade máxima, enquanto o subsistema de faturamento consome a mensagem de forma assíncrona em segundo plano. Caso o faturamento enfrente lentidão ou fique fora do ar, as mensagens aguardam na fila sem causar travamento na assistência médica.

#### **ITEM C (0,30 ponto) - Governança Tecnológica, Reuso e Diretrizes Low-Code**
1. **Análise dos Riscos Corporativos:**
   * *Shadow IT* gerou duplicidade e corrupção de prontuários médicos;
   * Violação da LGPD pela ausência de controle de acesso baseado em papéis (RBAC) e auditoria;
   * *Vendor Lock-in* com custos de escala imprevistos e código proprietário não migrável;
   * Limites de concorrência e performance em sistemas de suporte à vida.
2. **Três Diretrizes Obrigatórias de Governança e Reuso:**
   * **Diretriz 1 - Matriz de Elegibilidade Tecnológica (Quando Usar vs. Não Usar Low-Code):**
     * *Uso Recomendado de Low-Code:* Automação de fluxos departamentais internos, formulários de solicitação de férias/reembolso, prototipação rápida de MVPs e painéis administrativos com baixa concorrência.
     * *Desenvolvimento Tradicional (Pro-Code) Mandatório:* Módulos de missão crítica (UTI, dosagem de bombas, faturamento centralizado de alta performance), algoritmos complexos proprietários e manipulação direta de dispositivos de hardware.
   * **Diretriz 2 - Extinção de Shadow IT e Instituição de CoE (Centro de Excelência em TI):**
     * Nenhum aplicativo pode ser colocado em produção sem aprovação prévia da TI, mesmo que desenvolvido por *citizen developers*. Toda solução deve atender aos padrões de segurança, criptografia em repouso e trânsito (LGPD) e controle de ciclo de vida (ALM) com segregação de ambientes (Dev, Test e Prod).
   * **Diretriz 3 - Política de Reuso Sistemático e Mitigação de Lock-in:**
     * Exigir que qualquer plataforma Low-Code ou COTS adotada possua APIs abertas padrão REST/OpenAPI, suporte a exportação de dados estruturados e cálculo prévio do Custo Total de Propriedade (TCO) prevendo o crescimento da base de usuários nos próximos 3 a 5 anos.

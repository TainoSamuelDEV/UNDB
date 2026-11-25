# GABARITO OFICIAL COMENTADO & GUIA DE RESPOSTAS — SIMULADO 2 S.O. (ES04BN)

**Componente Curricular:** Sistemas Operacionais  
**Curso:** Engenharia de Software — UNDB  
**Docente:** Prof. Msc. Allisson Jorge Silva Almeida  
**Coordenação:** Prof. João Vitor Rego Muniz (Escola de Tecnologia — UNDB)  
**Turma:** ES04BN | **Turno:** Noturno  
**Base:** Prova anterior do docente (questões HGT01 de bancas 2026 + questão discursiva prática `/var/www/projeto`)

---

## 1. QUADRO RESUMO DE RESPOSTAS (FOLHA DE RESPOSTAS)

| Questão | Habilidade | Tipo | Pontuação | Resposta Correta |
| :---: | :---: | :--- | :---: | :---: |
| **1** | HGT01 | Objetiva Justificada (Assertivas I, II, III — IGEDUC) | 1,0 ponto | **A** |
| **2** | HGT01 | Objetiva Justificada (Múltipla Escolha — IDECAN) | 1,0 ponto | **D** |
| **3** | HGT01 | Objetiva Justificada (Múltipla Escolha — FADCT) | 1,0 ponto | **D** |
| **4** | HGT01 | Objetiva Justificada (Sequência de Comandos — APICE) | 1,0 ponto | **A** |
| **5** | HGT01 | Objetiva Justificada (Permissão Octal — FAURGS) | 1,0 ponto | **C** |
| **6** | HGT01 | Discursiva Prática (`/var/www/projeto`) | 1,0 ponto | `chmod` (`-R`), `chown -R` e `chmod -R 755` |
| **TOTAL** | — | — | **6,0 pontos** | — |

---

## 2. COMENTÁRIOS DETALHADOS E JUSTIFICATIVAS PADRÃO UNDB

### QUESTÃO 1 — HGT01 (1,0 ponto)
* **Alternativa Correta:** **(a) I e II, apenas.**
* **Justificativa Técnica Padrão UNDB:**
  * **Proposição I (Verdadeira):** O Microsoft Windows é de fato um sistema operacional proprietário (código fechado), amplamente adotado em estações de trabalho (desktops) e servidores, destacando-se pela interface gráfica acessível e pela extensa compatibilidade comercial com softwares e drivers de hardware.
  * **Proposição II (Verdadeira):** O Linux é um sistema operacional de código aberto baseado no kernel Linux, reconhecido por sua flexibilidade, segurança e estabilidade, sendo dominante em servidores, sistemas embarcados e supercomputadores, além de contar com múltiplas distribuições voltadas a desktops (como Ubuntu, Debian, Fedora, etc.).
  * **Proposição III (Falsa):** A proposição inverte e distorce a arquitetura dos dois kernels. O **Linux** adota um **kernel monolítico** (com suporte a módulos carregáveis dinamicamente em tempo de execução), e **não** um micro-núcleo (*microkernel*). Já o **Windows** (família Windows NT) utiliza um **kernel híbrido** (que combina características de kernel monolítico e de microkernel), e não puramente monolítico.

---

### QUESTÃO 2 — HGT01 (1,0 ponto)
* **Alternativa Correta:** **(d) Exibir a lista de arquivos e diretórios existentes no diretório atual do sistema.**
* **Justificativa Técnica Padrão UNDB:**
  * O comando **`ls`** (abreviação de *list*) tem como função listar os arquivos e subdiretórios contidos no diretório de trabalho atual (ou em outro caminho especificado como argumento).
* **Por que as demais estão erradas (comandos reais correspondentes):**
  * *(a)* Criar um novo diretório vazio é função do comando **`mkdir`** (*make directory*).
  * *(b)* Remover arquivos e diretórios permanentemente é função do comando **`rm`** / **`rm -rf`** (*remove*).
  * *(c)* Alterar permissões de acesso é função do comando **`chmod`** (*change mode*).
  * *(e)* Encerrar processos ativos é função de comandos como **`kill`** ou **`pkill`**.

---

### QUESTÃO 3 — HGT01 (1,0 ponto)
* **Alternativa Correta:** **(d) `ls`.**
* **Justificativa Técnica Padrão UNDB:**
  * No ambiente GNU/Linux, **`ls`** (*list*) é o comando padrão utilizado para listar arquivos e diretórios presentes no diretório atual ou em um caminho informado como parâmetro (por exemplo, `ls /var/www`).
* **Análise dos Distratores:**
  * *(a) `cat`:* Concatena e exibe o **conteúdo interno** de arquivos de texto no terminal, não listando diretórios.
  * *(b) `mat`:* Não é um comando padrão de listagem no GNU/Linux.
  * *(c) `kkdir`:* Distrator de grafia semelhante a `mkdir` (que cria diretórios); `kkdir` não existe no Linux.
  * *(e) `cp`:* Copia arquivos e diretórios (`cp -r`), não os lista.

---

### QUESTÃO 4 — HGT01 (1,0 ponto)
* **Alternativa Correta:** **(a) `pwd; cd Documentos/projetos; ls -la`**
* **Justificativa Técnica Padrão UNDB:**
  * O ponto e vírgula (`;`) encadeia a execução sequencial dos comandos no shell, cumprindo exatamente as três etapas pedidas na ordem:
    1. **`pwd`** (*Print Working Directory*): exibe o caminho absoluto do diretório atual (`/home/ana`).
    2. **`cd Documentos/projetos`** (*Change Directory*): entra no subdiretório `Documentos/projetos` a partir da pasta atual.
    3. **`ls -la`**: combina a flag `-l` (formato longo, exibindo permissões, dono, grupo, tamanho e data) com a flag `-a` (*all*, incluindo arquivos ocultos iniciados por ponto `.`).
* **Erros das Alternativas Rejeitadas:**
  * *(b)* Inverte a ordem (acessa antes de exibir o caminho original) e usa apenas `ls` sem `-la` (não mostra formato longo nem ocultos).
  * *(c)* Começa listando (`ls`) em vez de exibir o caminho absoluto e aplica `-la` no comando `pwd` (flag inválida para `pwd`).
  * *(d)* Lista `Documentos/projetos` antes de entrar nele, sem `-la`.
  * *(e)* Passa argumento de caminho inválido ao `pwd` e executa `cd` sem destino (o que retorna para a pasta `home`, em vez de acessar `Documentos/projetos`).

---

### QUESTÃO 5 — HGT01 (1,0 ponto)
* **Alternativa Correta:** **(c) o proprietário tenha leitura, escrita e execução; grupo e demais usuários tenham leitura e execução.**
* **Justificativa Técnica Padrão UNDB (Decomposição Octal `4=r`, `2=w`, `1=x`):**
  * Na notação octal de três dígitos (`[Dono][Grupo][Outros]`):
    * **Dono (`7`):** `4 + 2 + 1` = **`rwx`** → leitura, escrita e execução.
    * **Grupo (`5`):** `4 + 0 + 1` = **`r-x`** → leitura e execução (sem escrita).
    * **Demais usuários / Outros (`5`):** `4 + 0 + 1` = **`r-x`** → leitura e execução (sem escrita).
  * Portanto, `755` equivale à permissão simbólica **`rwxr-xr-x`**.
* **Por que as demais estão erradas:** *(a)* descreve permissão `600`; *(b)* exigiria dígitos iguais (ex.: `777` ou `555`); *(d)* o grupo (`5 = r-x`) não tem escrita (`w`); *(e)* grupo e outros também possuem permissão de execução (`x`).

---

### QUESTÃO 6 — HGT01 (1,0 ponto) — RESPOSTA PADRÃO ESPERADA (DISCURSIVA PRÁTICA)

#### **1. Comando para alteração de permissões e flag recursiva**
* **Comando:** **`chmod`** (*Change Mode*), utilizado para modificar as permissões de leitura (`r`), escrita (`w`) e execução (`x`) de arquivos e diretórios no Linux.
* **Parâmetro/Flag recursiva:** **`-R`** (em **maiúsculo**, ou `--recursive`), que faz com que a alteração de permissões seja propagada automaticamente para o diretório `/var/www/projeto` e para todos os seus subdiretórios e arquivos internos de uma só vez.
  > **Atenção à grafia da flag:** No `chmod` e no `chown`, a flag recursiva é **`-R` (maiúsculo)**. Já no `cp` e no `rm`, utiliza-se `-r` (minúsculo).

#### **2. Sequência prática de comandos no terminal**
Como o diretório pertence ao `root`, utiliza-se `sudo` para executar os ajustes com privilégio administrativo:

1. **Transferir recursivamente a propriedade (dono e grupo) de `root` para a equipe:**
   ```bash
   sudo chown -R usuario:equipe /var/www/projeto
   ```
   *(Alternativamente, caso se deseje alterar apenas o grupo mantendo o dono ou ajustando separadamente: `sudo chgrp -R equipe /var/www/projeto`.)*

2. **Conceder permissão recursiva de leitura, escrita e execução ao dono (`7 = 4+2+1`), e leitura e execução ao grupo (`5 = 4+0+1`) e outros (`5 = 4+0+1`):**
   ```bash
   sudo chmod -R 755 /var/www/projeto
   ```

---

## 3. OBSERVAÇÕES IMPORTANTES SOBRE A PROVA ORIGINAL (PEGADINHAS DE PROVA)

1. **Sobre os "dois comandos" no item 2 da prova original:**  
   Na prova impressa original, o enunciado contextualizava que `/var/www/projeto` pertencia exclusivamente ao `root` (exigindo alteração de propriedade/dono com `chown -R`), e o item 2 pedia explicitamente *"os dois comandos exatos"*, mas listava apenas o tópico de permissões (`755`). Neste **Simulado 2**, ambos os comandos (`chown -R` e `chmod -R 755`) foram explicitados nos subitens para que você domine a resposta completa sem surpresas caso o professor cobre os dois na P1.
2. **Cuidado com a anotação à lápis `777` na foto da prova original:**  
   Na foto da Questão 6 havia uma anotação `777` escrita à lápis. **`777` (`rwxrwxrwx`) está INCORRETO** para o que o enunciado pede (`leitura, escrita e execução para o dono` = **`7`**, e `leitura e execução para o grupo e outros` = **`5`** e **`5`** → **`755`**). Além disso, `chmod -R 777` em `/var/www/projeto` configura falha grave de segurança em servidores web de produção por liberar escrita e execução irrestritas a qualquer usuário do sistema.
3. **Nuance prática (produção vs. enunciado de prova):**  
   Em um servidor real onde *outros membros do grupo* precisam gravar/salvar arquivos dentro da mesma pasta, o administrador usaria `chmod -R 775` (`rwxrwxr-x`) após ajustar o grupo com `chown -R`. Contudo, em prova acadêmica, **siga sempre exatamente os privilégios descritos no comando da questão** (`rwx` dono, `r-x` grupo, `r-x` outros = **`755`**).

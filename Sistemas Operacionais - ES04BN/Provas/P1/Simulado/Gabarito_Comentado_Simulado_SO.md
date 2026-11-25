# GABARITO OFICIAL COMENTADO & GUIA DE RESPOSTAS — SIMULADO S.O. (ES04BN)

**Componente Curricular:** Sistemas Operacionais  
**Curso:** Engenharia de Software — UNDB  
**Docente:** Prof. Msc. Allisson Jorge Silva Almeida  
**Coordenação:** Prof. João Vitor Rego Muniz (Escola de Tecnologia — UNDB)  
**Turma:** ES04BN | **Turno:** Noturno  
**Base:** Quiz `Revisão S.O - 18/11/2026` e `Aula - Comandos Linux Terminal.pdf`

---

## 1. QUADRO RESUMO DE RESPOSTAS (FOLHA DE RESPOSTAS)

| Questão | Habilidade | Tipo | Pontuação | Resposta Correta |
| :---: | :---: | :--- | :---: | :---: |
| **1** | HTE01 | Objetiva Justificada (Múltipla Escolha) | 1,0 ponto | **B** |
| **2** | HTE02 | Objetiva Justificada (Assertivas I, II, III) | 1,0 ponto | **A** |
| **3** | HTE03 | Objetiva Justificada (Associação de Colunas) | 1,0 ponto | **A** |
| **4** | HTE03 | Objetiva Justificada (V ou F) | 1,0 ponto | **A** |
| **5** | HTE01 / HTE03 | Objetiva Justificada (Múltipla Escolha) | 1,0 ponto | **B** |
| **6** | HGT04 / HTE01 / HTE02 / HTE03 | Discursiva (Estudo de Caso PBL) | 1,0 ponto | Parecer Técnico (Itens A, B e C) |
| **TOTAL** | — | — | **6,0 pontos** | — |

---

## 2. COMENTÁRIOS DETALHADOS E JUSTIFICATIVAS PADRÃO UNDB

### QUESTÃO 1 — HTE01 (1,0 ponto)
* **Alternativa Correta:** **(b) `pwd`, `mkdir logs_auditoria`, `touch logs_auditoria/relatorio.txt` e `ls -la`.**
* **Justificativa Técnica Padrão UNDB:**
  1. **`pwd` (*Print Working Directory*):** Exibe o caminho absoluto completo do diretório atual em que o usuário se encontra.
  2. **`mkdir logs_auditoria` (*Make Directory*):** Cria o novo diretório chamado `logs_auditoria`.
  3. **`touch logs_auditoria/relatorio.txt`:** Cria o arquivo vazio `relatorio.txt` dentro da pasta recém-criada.
  4. **`ls -la` (combinação de `ls -l` + `ls -a`):** A flag `-a` exibe arquivos ocultos (iniciados por `.`) e a flag `-l` apresenta a listagem detalhada contendo permissões, dono, grupo, tamanho e data.
* **Erros das Alternativas Rejeitadas:**
  * *(a)* Inverte `touch` (para pasta) e `mkdir` (para arquivo), usa `cd` em vez de `pwd` e inventa `chmod -la`.
  * *(c)* Usa `ls -l` para ver diretório atual e `pwd -a` (inválido).
  * *(d)* Troca `mkdir` por `touch` (tentando criar pasta com `touch`) e omite `-l` em `ls -a` (não mostraria dono, grupo e permissões).
  * *(e)* Usa `rm` (remover) para criar arquivo e `chown -l` para listar.

---

### QUESTÃO 2 — HTE02 (1,0 ponto)
* **Alternativa Correta:** **(a) Apenas I e II.**
* **Justificativa Técnica Padrão UNDB:**
  * **Assertiva I (Verdadeira):** O comando `cp` copia arquivos mantendo o original intacto na origem. Para copiar diretórios inteiros e seus subníveis, exige obrigatoriamente a flag `-r` (*recursive*): `cp -r [origem] [destino]`.
  * **Assertiva II (Verdadeira):** O comando `mv` tanto **move** arquivos/diretórios entre pastas (equivalente a recortar e colar) quanto **renomeia** itens quando origem e destino permanecem no mesmo diretório com nomes diferentes.
  * **Assertiva III (Falsa):** O comando `rm -rf [pasta]` remove recursivamente (`-r`) e de forma forçada (`-f`) diretórios e todo o seu conteúdo **sem pedir nenhuma confirmação** e de modo **definitivo** (não há lixeira padrão no terminal).

---

### QUESTÃO 3 — HTE03 (1,0 ponto)
* **Alternativa Correta:** **(a) 2 - 1 - 4 - 3.**
* **Justificativa Técnica Padrão UNDB (Decomposição Octal `4=r`, `2=w`, `1=x`):**
  1. **`(2) chmod 775 deploy.sh`** → Dono = `7 (4+2+1 = rwx)`, Grupo = `7 (4+2+1 = rwx)`, Outros = `5 (4+0+1 = r-x)`. Logo, dono e grupo têm permissão total; outros apenas leem e executam (`rwxrwxr-x`).
  2. **`(1) chmod 700 chave_privada.pem`** → Dono = `7 (rwx)`, Grupo = `0 (---)`, Outros = `0 (---)`. Somente o dono possui acesso total (`rwx------`).
  3. **`(4) chmod 777 temp.log`** → Dono = `7 (rwx)`, Grupo = `7 (rwx)`, Outros = `7 (rwx)`. Todos possuem permissão irrestrita (`rwxrwxrwx`).
  4. **`(3) chmod 644 config.txt`** → Dono = `6 (4+2+0 = rw-)`, Grupo = `4 (4+0+0 = r--)`, Outros = `4 (4+0+0 = r--)`. Dono lê e grava; grupo e outros apenas leem (`rw-r--r--`).

---

### QUESTÃO 4 — HTE03 (1,0 ponto)
* **Alternativa Correta:** **(a) V - V - F - F.**
* **Justificativa Técnica Padrão UNDB:**
  * **1ª Afirmativa (V):** Um **grupo** no Linux agrupa usuários que compartilham permissões semelhantes de acesso a arquivos e diretórios.
  * **2ª Afirmativa (V):** **`chown`** (*change owner*) altera o dono (proprietário) de um arquivo/diretório (podendo também alterar `dono:grupo`), enquanto **`chgrp`** (*change group*) altera especificamente o grupo associado ao arquivo.
  * **3ª Afirmativa (F):** O comando `chmod` altera permissões, não é um comando de listagem/inspeção. Quem exibe dono, grupo, permissões e tamanho é **`ls -l`**.
  * **4ª Afirmativa (F):** `755` equivale a `rwxr-xr-x` — portanto, grupo (`5 = r-x`) e outros (`5 = r-x`) **podem** ler e executar o script; apenas a escrita (`w`) é bloqueada para eles. Para impedir qualquer acesso de grupo e outros, o correto seria `chmod 700`.

---

### QUESTÃO 5 — HTE01 / HTE03 (1,0 ponto)
* **Alternativa Correta:** **(b) `ssh -p 2222 deploy@192.168.10.45`; `scp` para transferência; `chmod +x start.sh` para tornar executável.**
* **Justificativa Técnica Padrão UNDB:**
  * O **SSH** (*Secure Shell*) usa a porta padrão `22`; quando o servidor escuta em outra porta (`2222`), especifica-se com a flag `-p` minúscula: `ssh -p 2222 deploy@192.168.10.45`.
  * O comando **`scp`** (*Secure Copy*) utiliza o canal criptografado do SSH para copiar arquivos entre a máquina local e o servidor remoto.
  * O comando **`chmod +x start.sh`** adiciona a permissão de execução (`x`) ao arquivo, permitindo executá-lo diretamente no terminal (`./start.sh`).
* **Erros das Demais Alternativas:** *(a)* porta padrão é `22`, não `80`, e `scp` transfere arquivos enquanto `ssh` abre terminal; *(c)* sem `-p 2222`, `ssh` tenta a porta `22`; *(d)* `scp` é criptografado via SSH e `mv` só move localmente; *(e)* `644` (`rw-r--r--`) não concede permissão de execução (`x`).

---

### QUESTÃO 6 — HGT04 / HTE01 / HTE02 / HTE03 (1,0 ponto) — RESPOSTA PADRÃO ESPERADA (PBL)

#### **ITEM A (0,40 ponto) — Diagnóstico e Correção de Permissões, Dono e Grupo**
1. **Permissão atual de `db_secrets.env`:** `-rwxrwxrwx` corresponde ao octal **`777`** (`4+2+1` para Dono, Grupo e Outros). **Risco:** qualquer usuário local ou processo comprometido no servidor pode ler as senhas do banco, adulterá-las ou executá-las.
2. **Comandos corretos de correção:**
   - Alterar dono para `root` e grupo para `app_prod`:
     ```bash
     sudo chown root:app_prod /srv/ilhatech/config/db_secrets.env
     sudo chown root:app_prod /srv/ilhatech/config/integra_pagamentos.sh
     ```
     *(Alternativamente, usar `chown root` seguido de `chgrp app_prod` para alterar o grupo separadamente).*
   - Restringir `db_secrets.env` apenas ao dono (sem execução desnecessária para arquivo de configuração/segredos):
     ```bash
     sudo chmod 600 /srv/ilhatech/config/db_secrets.env
     ```
     *(Obs.: `600` [`rw-------`] é o ideal para arquivo de texto/credenciais, pois dá leitura e escrita somente ao dono sem marcar bit executável; `700` [`rwx------`] também garante isolamento total de grupo e outros caso justificado).*
   - Tornar `integra_pagamentos.sh` executável:
     ```bash
     sudo chmod 750 /srv/ilhatech/config/integra_pagamentos.sh
     # ou: sudo chmod +x /srv/ilhatech/config/integra_pagamentos.sh (com ajuste de escrita/leitura se desejado; 750 garante rwx ao dono, r-x ao grupo app_prod e --- para outros).
     ```

#### **ITEM B (0,30 ponto) — Recuperação e Manipulação Segura de Diretórios e Arquivos**
1. **Diagnóstico:**
   - `cp /srv/ilhatech/pedidos /srv/backup/` falhou porque `pedidos` é um **diretório** com subpastas; o comando `cp` sem a flag **`-r` (recursivo)** só copia arquivos individuais.
   - O comando `mv` **move** (recorta e cola) em vez de copiar, retirando o diretório de produção. Além disso, `rm` / `rm -rf` apaga arquivos sem confirmação e sem lixeira.
2. **Sequência correta de recuperação e backup:**
   ```bash
   mv /srv/backup/pedidos /srv/ilhatech/pedidos
   mkdir /srv/backup/2026
   cp -r /srv/ilhatech/pedidos /srv/backup/2026/
   ```

#### **ITEM C (0,30 ponto) — Transferência Segura, Acesso Remoto e Inspeção**
1. **Transferir `release.tar.gz` via `scp`:**
   ```bash
   scp release.tar.gz sysadmin@10.20.30.40:/srv/ilhatech/releases/
   ```
2. **Conectar via `ssh` na porta padrão (`22`):**
   ```bash
   ssh sysadmin@10.20.30.40
   ```
3. **Confirmar diretório atual e listar todos os arquivos (incluindo ocultos) com detalhes:**
   ```bash
   pwd
   cd /srv/ilhatech/releases
   ls -la
   ```
   *(Obs.: `ls -la` combina `ls -l` [dono, grupo, permissões e tamanho] com `ls -a` [arquivos ocultos como `.env.prod`]).*

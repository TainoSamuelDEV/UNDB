# Guia de Revisão — Sistemas Operacionais (Comandos Linux, Permissões e Acesso Remoto)

**Instituição:** UNDB — Centro Universitário (Escola de Tecnologia)  
**Disciplina:** Sistemas Operacionais (`ES04BN`)  
**Docente:** Prof. Msc. Allisson Jorge Silva Almeida  
**Base do Material:**
- Quiz em aula: `Question_2026_11_18__22_11_QZ_Revisão S.O - 18112026.pdf` (30 questões — 18/11/2026)
- Apostila da disciplina: `Aula - Comandos Linux Terminal.pdf`

---

## Sumário Rápido
1. [Diagnóstico do Quiz (Onde a Turma Mais Errou)](#1-diagnóstico-do-quiz)
2. [Navegação e Criação de Diretórios e Arquivos](#2-navegação-e-criação-de-diretórios-e-arquivos)
3. [Cópia, Movimentação, Renomeação e Remoção](#3-cópia-movimentação-renomeação-e-remoção)
4. [Permissões no Linux (`chmod`) e Matemática Octal](#4-permissões-no-linux-chmod-e-matemática-octal)
5. [Donos, Grupos e Inspeção (`chown`, `chgrp`, `ls -l`)](#5-donos-grupos-e-inspeção-chown-chgrp-ls--l)
6. [Acesso Remoto Seguro e Transferência (`ssh` e `scp`)](#6-acesso-remoto-seguro-e-transferência-ssh-e-scp)
7. [Pegadinhas Clássicas de Prova e Macetes de Memorização](#7-pegadinhas-clássicas-de-prova-e-macetes)
8. [Checklist de Revisão Rápida (Baseado nas 30 Questões do Quiz)](#8-checklist-de-revisão-rápida)

---

## 1. Diagnóstico do Quiz

Analisando os resultados da turma no quiz **Revisão S.O - 18/11/2026** (Socrative), os conceitos com maior índice de acerto foram `cp` (21/21), `mv` (20/20), `chmod 775 file` (20/20), `chmod 777 file` (20/20), `chmod` geral (20/21) e definição de grupo (20/21).

Por outro lado, **4 pontos concentraram a maior parte dos erros** e merecem atenção máxima antes da prova:

| Questão do Quiz | Assunto | Acerto da Turma | Erro Mais Comum | Como Não Cair Mais |
| :--- | :--- | :---: | :--- | :--- |
| **Q24** | Ver dono e grupo de um arquivo | **8/20 (40%)** | Marcar `chmod` (8/20) ou `pwd` (4/20) | `chmod` **altera** permissões; quem **lista/exibe** detalhes (permissões, dono, grupo, tamanho) é **`ls -l`**. |
| **Q11** | Acesso total **somente para o dono** | **9/20 (45%)** | Marcar `chmod 777` (6/20) ou `755` (5/20) | `7` = Dono total, `0` = Grupo nada, `0` = Outros nada → **`chmod 700`**. (`777` libera para **todos**!) |
| **Q28** | Mudar o **grupo** (dono do grupo) de um arquivo | **9/20 (45%)** | Marcar `chmod` (10/20) | **`chgrp`** (*change group*) muda o grupo; **`chown`** (*change owner*) muda o dono (ou `dono:grupo`); **`chmod`** muda permissões. |
| **Q12 / Q26** | Mudar o **dono** de um arquivo | **12/20 a 14/20** | Confundir `chown` com `chmod` | **`chown`** = *CHange OWNer* (proprietário). **`chmod`** = *CHange MODe* (modo/permissões). |
| **Q8 / Q20** | Mostrar o diretório atual | **12/19 a 13/21** | Confundir `pwd` com `ls -l`, `cd` ou `mkdir` | **`pwd`** = *Print Working Directory* (imprime o caminho atual). `cd` entra em pastas; `mkdir` cria pastas. |

---

## 2. Navegação e Criação de Diretórios e Arquivos

### Comandos Essenciais

| Comando | Significado | Função Principal | Exemplos Práticos |
| :--- | :--- | :--- | :--- |
| **`pwd`** | *Print Working Directory* | Exibe o **caminho completo** do diretório em que você está no momento. | `pwd` → `/home/aluno/projetos` |
| **`ls`** | *List* | Lista os arquivos e diretórios do diretório atual. | `ls` |
| **`ls -l`** | *List (long format)* | Exibe **listagem detalhada**: tipo, permissões, links, **dono**, **grupo**, tamanho, data e nome. | `ls -l` |
| **`ls -a`** | *List (all)* | Exibe **todos** os arquivos, incluindo **arquivos e pastas ocultos** (que começam com `.`, como `.bashrc` ou `.gitignore`). | `ls -a` (ou `ls -la` para detalhado + ocultos) |
| **`cd [caminho]`** | *Change Directory* | **Entra** ou muda para outro diretório. | `cd projetos` / `cd ..` (volta um nível) / `cd ~` (vai para a *home*) |
| **`mkdir [nome]`** | *Make Directory* | **Cria um novo diretório** (pasta). | `mkdir projetos` |
| **`touch [arquivo]`** | *Touch* | **Cria um novo arquivo vazio** (ou atualiza a data de modificação se já existir). | `touch relatorio.txt` |

> **Atenção:** `mkdir` cria **diretórios (pastas)**; `touch` cria **arquivos vazios**. Na Q18 do quiz, 4/20 alunos marcaram `touch` para criar diretório — não confunda!

---

## 3. Cópia, Movimentação, Renomeação e Remoção

No terminal Linux não existe um comando "colar" isolado. Você informa `[origem]` e `[destino]` diretamente nos comandos `cp` e `mv`.

| Comando | Significado | Função | Flags e Cuidados Importantes |
| :--- | :--- | :--- | :--- |
| **`cp [origem] [destino]`** | *Copy* | **Copia** arquivos (mantém o original na origem). | `cp relatorio.txt /home/usuario/documentos/` |
| **`cp -r [orig] [dest]`** | *Copy (recursive)* | Copia **diretórios inteiros recursivamente** (com subpastas e arquivos dentro). | Sem `-r`, o `cp` falha ao tentar copiar um diretório. Ex: `cp -r /pasta1 /pasta2` |
| **`mv [origem] [destino]`** | *Move* | **Move** arquivos/diretórios ("recortar e colar") **e também renomeia**. | Mover: `mv script.py /home/scripts/`<br>Renomear: `mv foto_antiga.jpg foto_nova.jpg` |
| **`rm [arquivo]`** | *Remove* | **Apaga/remove** um arquivo permanentemente (não vai para lixeira). | `rm arquivo.txt` |
| **`rm -rf [pasta]`** | *Remove recursive force* | Apaga **pastas e todo o seu conteúdo** sem pedir confirmação. | **Perigo extremo:** `rm -rf` não pede confirmação e não tem "desfazer". |

---

## 4. Permissões no Linux (`chmod`) e Matemática Octal

No Linux, todo arquivo ou diretório possui permissões divididas em **3 categorias de usuários** (sempre nessa ordem):

```text
[  Dono (User / u)  ]   [  Grupo (Group / g)  ]   [  Outros (Others / o)  ]
       r w x                    r w x                     r w x
```

### Valores de Cada Permissão (Sistema Octal)

| Letra | Permissão | Significado em Arquivo | Significado em Diretório | Valor Octal |
| :---: | :--- | :--- | :--- | :---: |
| **`r`** | *Read* (Leitura) | Ler o conteúdo do arquivo | Listar os nomes dentro da pasta (`ls`) | **4** |
| **`w`** | *Write* (Escrita/Gravação) | Alterar ou gravar no arquivo | Criar, renomear ou apagar arquivos na pasta | **2** |
| **`x`** | *Execute* (Execução) | Executar como programa/script | Entrar na pasta (`cd`) | **1** |
| **`-`** | Sem permissão | Acesso negado naquela ação | Acesso negado naquela ação | **0** |

### Tabela de Combinações Octais (Soma de `4 + 2 + 1`)

| Dígito | Soma | Binário / Letras | Significado |
| :---: | :---: | :---: | :--- |
| **7** | `4 + 2 + 1` | `rwx` | **Acesso total** (ler, escrever e executar) |
| **6** | `4 + 2 + 0` | `rw-` | Ler e escrever (sem executar) |
| **5** | `4 + 0 + 1` | `r-x` | Ler e executar (sem escrever/alterar) |
| **4** | `4 + 0 + 0` | `r--` | Somente leitura |
| **0** | `0 + 0 + 0` | `---` | **Nenhuma permissão** (sem acesso) |

### Comandos Mais Cobrados em Prova

| Comando | Representação Simbólica | Quem Pode o Quê? | Caso de Uso Típico |
| :--- | :---: | :--- | :--- |
| **`chmod 777 arq`** | `rwxrwxrwx` | **Todos** (Dono, Grupo e Outros) podem ler, escrever e executar. | Inseguro em produção; só para testes isolados. |
| **`chmod 775 arq`** | `rwxrwxr-x` | **Dono e Grupo** têm acesso total (`rwx`); **Outros** apenas leem e executam (`r-x`). | Pastas compartilhadas de equipe de projeto. |
| **`chmod 755 arq`** | `rwxr-xr-x` | **Dono** tem acesso total (`rwx`); **Grupo e Outros** apenas leem e executam (`r-x`). | Padrão para diretórios públicos e executáveis/scripts. |
| **`chmod 700 arq`** | `rwx------` | **Somente o Dono** tem acesso total (`rwx`); Grupo e Outros não têm nenhum acesso (`---`). | Chaves privadas SSH (`~/.ssh`), scripts privados. |
| **`chmod 644 arq`** | `rw-r--r--` | **Dono** lê e escreve (`rw-`); **Grupo e Outros** apenas leem (`r--`). | Padrão para arquivos de texto, HTML, configs públicas. |
| **`chmod 600 arq`** | `rw-------` | **Somente o Dono** lê e escreve (`rw-`); Grupo e Outros não acessam (`---`). | Arquivos de senha/credenciais (`.env`, chaves privadas). |
| **`chmod +x arq`** | Adiciona `x` | Torna o arquivo **executável** (muito usado para shell scripts `.sh`). | `chmod +x deploy.sh` seguido de `./deploy.sh` |

### Como Ler a Saída do `ls -l`

Exemplo real de saída no terminal:
```text
-rwxrwxr-x 1 joao devs 2048 Nov 18 22:11 deploy.sh
│└┬┘└┬┘└┬┘   └─┬┘ └─┬─┘
│ │  │  │      │    └── Grupo do arquivo (devs)
│ │  │  │      └─────── Dono / Proprietário (joao)
│ │  │  └────────────── Outros: r-x = 4+0+1 = 5
│ │  └───────────────── Grupo:  rwx = 4+2+1 = 7
│ └──────────────────── Dono:   rwx = 4+2+1 = 7  → Permissão 775!
└────────────────────── Tipo: '-' = arquivo comum | 'd' = diretório | 'l' = link
```

---

## 5. Donos, Grupos e Inspeção (`chown`, `chgrp`, `ls -l`)

1. **O que é um Grupo no Linux?**  
   É um **conjunto de usuários que compartilham permissões semelhantes** sobre determinados arquivos, diretórios ou recursos do sistema (Q13 do quiz).

2. **Diferença Crucial entre os Três Comandos `ch*`:**
   - **`chmod`** (*Change Mode*): altera **permissões** (`r`, `w`, `x` / octal `775`, `700`, `+x`).
   - **`chown`** (*Change Owner*): altera o **dono (proprietário)** de um arquivo/pasta, podendo também alterar o grupo simultaneamente com a sintaxe `usuario:grupo`.  
     Exemplo da apostila: `sudo chown root:root configuracao.conf`
   - **`chgrp`** (*Change Group*): altera especificamente o **grupo** (dono do grupo) associado a um arquivo ou diretório.  
     Exemplo: `sudo chgrp devs projeto/`

3. **Como inspecionar dono, grupo e permissões?**  
   Usando **`ls -l [arquivo_ou_diretorio]`**.

---

## 6. Acesso Remoto Seguro e Transferência (`ssh` e `scp`)

Da apostila `Aula - Comandos Linux Terminal.pdf`, seção 4:

- **SSH (*Secure Shell*):** Protocolo padrão criptografado para acessar terminais de outros computadores ou servidores de forma segura.
  - Porta padrão do SSH: **porta 22**.
  - Conectar na porta padrão:  
    `ssh [usuario]@[ip_ou_dominio]` → Ex.: `ssh admin@192.168.1.50`
  - Conectar em porta diferente da padrão (`-p` minúsculo):  
    `ssh -p [porta] [usuario]@[ip]` → Ex.: `ssh -p 2222 admin@10.0.0.5`
- **SCP (*Secure Copy*):** Copia arquivos entre sua máquina local e um servidor remoto **usando a conexão segura do SSH**.
  - Enviar arquivo local para o servidor remoto:  
    `scp [arquivo_local] [usuario]@[ip]:[caminho_destino]`  
    Ex.: `scp site.zip admin@192.168.1.50:/var/www/html/`
  - *(Nota: no `scp`, quando se especifica porta diferente da 22, usa-se `-P` maiúsculo, diferente do `-p` minúsculo do `ssh`.)*

---

## 7. Pegadinhas Clássicas de Prova e Macetes

1. **`chmod` vs `chown` vs `chgrp`:**
   - **mod** = **mod**o de acesso (permissões `rwx` / números).
   - **own** = **own**er (dono/proprietário).
   - **grp** = **gr**u**p**o.
2. **`700` vs `755` vs `775` vs `777`:**
   - Só o dono faz tudo, ninguém mais entra = **`700`**.
   - Dono faz tudo, grupo e outros só leem/executam = **`755`**.
   - Dono e grupo fazem tudo, outros só leem/executam = **`775`**.
   - Todo mundo faz tudo (perigo!) = **`777`**.
3. **`ls -l` vs `ls -a`:**
   - **`-l`** = **l**onga (detalhada: permissões, dono, grupo, tamanho).
   - **`-a`** = **a**ll (tudo, incluindo arquivos ocultos iniciados por `.`).
4. **`cp` sem `-r` em pastas:**
   - `cp` sozinho só copia arquivos; para copiar pastas inteiras, exige **`cp -r`** (recursivo).
5. **Dois papéis do `mv`:**
   - Se o destino é uma pasta existente → **move** o arquivo para lá.
   - Se o destino é um novo nome na mesma pasta → **renomeia** o arquivo.
6. **`pwd` vs `cd` vs `mkdir`:**
   - **`pwd`** apenas **mostra** onde você está.
   - **`cd`** **muda** onde você está.
   - **`mkdir`** **cria** uma nova pasta.

---

## 8. Checklist de Revisão Rápida

Antes da prova, confirme se você responde de cabeça sem hesitar:
- [ ] Qual comando lista arquivos e diretórios? (`ls`)
- [ ] Qual comando lista com detalhes (permissões, dono e grupo)? (`ls -l`)
- [ ] Qual comando exibe arquivos ocultos? (`ls -a`)
- [ ] Qual comando mostra o diretório atual? (`pwd`)
- [ ] Qual comando cria um novo diretório? (`mkdir`)
- [ ] Qual comando cria um arquivo vazio? (`touch`)
- [ ] Qual comando copia arquivos (`cp`) e diretórios recursivamente (`cp -r`)?
- [ ] Qual comando move ou renomeia arquivos? (`mv`)
- [ ] Qual comando remove arquivos (`rm`) e diretórios sem confirmação (`rm -rf`)?
- [ ] Qual comando altera permissões (`chmod`) e qual a matemática octal (`4=r`, `2=w`, `1=x`)?
- [ ] O que significam `700`, `644`, `755`, `775` e `777`?
- [ ] Qual comando muda o dono (`chown`) e qual muda o grupo (`chgrp`)?
- [ ] O que é um grupo no Linux? (Conjunto de usuários com permissões semelhantes)
- [ ] Qual a diferença entre `ssh`, `ssh -p` e `scp`?

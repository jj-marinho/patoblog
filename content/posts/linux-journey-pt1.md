---
title: "Anotações Jornada Linux - Parte 1"
date: 2020-04-30T22:51:37-03:00
tags : ["linux", "sysadmin", "OS"]
categories : [ "linux" ]
layout: post
weight: 50
---

# Jornada Linux - Parte 1 - Grasshopper
## Comandos básicos

### Dica
```bash
# Podemos repetir o comando anterior com !!
visudo # whoops, esqueci o sudo

sudo !! # resolvido
```
### Manipulação de Diretórios
```bash
pwd # Diretório Atual
cd # Mudar diretório
ls # Listar diretórios 
# Flags -a Mostra Hidden e -l Visão Completa
touch # Criar novos arquivos
file # Checa o tipo de arquivo
cp a1 a2 # copia um a1, com nome a2
mv a1 ../a1 # Move a1, um diretório abaixo
mkdir # cria um novo diretório
rm # Remove um arquivo
# Flags -f Força remoção -r Recursivo

find # Ajuda a encontrar arquivos, olha em subdiretórios
# Muitas flags, entre elas
# -type Tipo de arquivo
# -name Nome do arquivo a ser encontrado
```

### Impressão de Texto
```bash
cat # Mostra o conteúdo de um arquivo (também concatena arquivos)
less # Mostra arquivos maiores, numa interface
```

### Ajuda
```bash
--help || -h # Flag usada em alguns programas para documentação
man # Manual com a maioria das aplicações Linux
whatis # Versão simplificada do Man, apenas algumas linhas
```

## Lidando com textos
### stdout / stdin / pipe / tee
```bash
#------- STDOUT
'>' # define stdout de um comando
    # Exemplo: Enviando echo para um arquivo
echo Hello World > teste.txt

'>>' # define stdout, porém adiciona (appends) ao final do arquivo
------ STDIN
'<' # Faz o papel do teclado, muda o stdin
    # Exemplo: duplicando o texto anterior
cat < teste.txt >> teste2.txt

-------- PIPE
# Podemos encaminhar o resultado de um comando
# como entrada de outro comando
# Exemplo: stdout de ls para less
ls -la /etc | less

# Para replicar o comando tanto na tela
# quanto para a próxima aplicação, podemos usar o tee
# Exemplo com tee
ls -la /etc | tee less
```

## Env ou Environment
```bash
# environment é um conjuto de variáveis do ambiente linux
# Exemplo, variável HOME
echo $HOME

# Todas as variáveis de ambiente podem ser vistas em:
env

# Uma das mais importante é a $PATH
# Ela indica pro sistema onde ficam todos os binários
# podemos adicionar mais locais pro sistema pesquisar
# por binários nela
```

## Lidando com textos

### grep
```bash
# Processador de texto mais comum do Linux
# Procura padrões em arquivos
# Exemplo
echo What does the fox say > sample.txt
grep fox sample.txt
# Mostra a linha onde fox se encontra

# Podemos usar PIPES no grep
env | grep PATH USER
# Podemos ignorar maiusculas e minusculas usando -i
env | grep -i path
# Podemos ver o número da linha com -n
env | grep -in path

# grep também aceita regex, explicações a seguir
```
### Regex

```bash
# Matches literais
## Só adicionar a expressão como argumento para grep
Exemplo: linha que contém "lib"
env | grep -i "lib"

# Matches com ancora
## Se relacionam a determinados pontos na linha
# ^inicio / fim$
# Exemplo: Linha que inicia com "path"
env | grep -i "^path"

# Matches por caractere
## usando '.' como wildcard pra qualquer caractere
## usando [] e especificando alguma condição dentro
# Exemplo: match para números
env | grep -n "[0-9]"

# Podemos fazer a negação do exemplo anterior usando ^
# Exemplo: match para tudo, menos números
env | grep -n "[^0-9]"

# Repetição
## Podemos usar o operador * para indicar que se deve repetir um padrão mais de uma vez
# Exemplo: match para tudo que contenha texto dentro de parenteses
# (Joao), por exemplo
grep -in "([a-z ]*)"

# Inversor
## Podemos usar a tag -v para inverter os resultados
## Tudo que não entraria, entra e vice-versa
# Exemplo: Match para linha sem números
grep -vin "[0-9]"
```

## Controle de usuários

### Arquivos de usuários
```bash
su # substituir usuário
# entra no root se não houver segundo argumento

# sudoers -> quem tem acesso ao comando sudo no seu sistema
# podemos ver e editar o sudoers usando o comando:
sudo visudo

# Outro arquivo importante é /etc/passwd
# Contém varias informações sobre cada usuário do sistema
# Limitado por ':' temos:
# username:senha:UID:GID:GECOS:home:shell
# Observação: x na senha indica que a senha esta em /etc/shadow de maneira encriptada
```
### Ferramentas para usuários

```bash
useradd jones # cria usuário jones
userdel jones # deleta usuário jones
passwd jones # Troca a própria senha
# Se houver um nome de usuário e você estiver como root
# troca a senha de outro usuário
```

## Permissões
```bash
# 4 partes para cada arquivo

ls -l
# dir? | user | group | others
# -    | rwx  | r-x   | r-x


## Alterando permissões
# Podemos usar o comando chmod + ou -
# Ex:
chmod u+x arquivo
// Adicionar (+) permissão ao usuário (u) de executar (x)

# Podemos mudar o dono do arquivo usando chown e chgrp
chown jorge arquivo
chgrp patos arquivo
# Agora o arquivo pertence ao user jorge e grupo patos

# Podemos mudar as permissões padrões usando umask
umask 021  # Retira permissões
# Usuário: 7 = rwx, Grupo = r-x, Others: rw- 

# Set UID & GID
# Poder de pedir permissão do dono de um arquivo para usá-lo
# denota-se com:
chmod u+s || chmod 4755 # 4 pré-fixado
# Podemos fazer o mesmo com um grupo
chmod g+s || chmod 2755 # 2 pré-fixado

# Sticky files / directories
# Diretórios que só podem ser deletados pelo dono ou root
chmod +t diretorio 
```

## Processos
```bash
# Processos são programas
# Gerenciados pelo kernel, cada um tem um ID (PID)

ps # Quais processos estão rodando no momento

ps -aux # a: All, u: ExtraInfo, x: Sem TTY

# Interfaces mais elegantes
top
htop
```
### TTY
- Terminal nativo
  - TTY no `top`
- Roda no background
- Quando abrimos o "terminal", estamos abrindo um emulador de terminal ou pseudoterminal
  - com nome PTS no `top`
- Processos intimamente ligados com o sistema (como daemons) não usam terminal, portanto no `top` vemos ?

### Sinais
- Enviados do OS para os programas
- Notificação de que alguma coisa aconteceu
- Tipos de notificalçoes
  - SIGHUP -> Terminal de controle fechou
  - SIGINT -> Interrompido Ctrl-C por exemplo
  - SIGTERM -> Termina, porém deixa fazer cleanup
  - SIGKILL -> Press F to pay respects
  - SIGSTOP -> Para ou suspende
- Niceness -> "legaldade"
```bash
# Niceness
# Quanto mais legal, menos prioridade pra CPU
top # Coluna NI identifica
renice 10 -p 3245 # Muda a niceness de um processo
```

### Estados
- R: Running, execuntando
- S: Sleep, dormindo, esperando por evento
- D: Deu pau, ta dormindo pra sempre
- Z: Zombie, esperando o processo Pai dar await
- T: Stopped, processo susoenso

### Diretório /proc
- Visão do kernel sobre sistema
- Diretório com todos os processos atuais

### Jobs
- Maneira de mandar um processo pro background
```bash
sleep 1000
# Ctrl-Z, Stopped
bg # manda processo pro background
jobs # Vê os processos no Background. +: Recente, -: Antigo
fg %ID # Retorna um processo pro foreground, ID = Job ID
kill %ID # mata processo rodando como job, usando o Job ID
```

## Packages || Pacotes
- Packages são a maneira de se distribuir software no Linux
- Muitos arquivos distribuidos em um pacote coeso (Photoshop, Firefox, vscode, etc)
- São provenientes de package managers
- Podem ser instalados diretamente, e até compilados da source
- Pacotes são interligados e tem dependências necessárias em outros pacotes (glibc, por exemplo)
```bash
# Por vezes, um programa vem no formato gzip/tar
# Podemos extraílos usando o utilitário tar
tar czf criandoArquivo.tar.gz
tar xzf extraindoArquivo.tar.gz
```

#### Ao compilar da source use `checkinstall`
- sudo make install/uninstall muitas vezes não realiza toda a preparação necessária no pacote
- `checkinstall` cria um .deb e o instala
- Pode ser usado em Fedora/RHEL com a flag -R
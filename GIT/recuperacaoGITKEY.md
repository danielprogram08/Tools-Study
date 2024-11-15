## **RESTAURANDO O ACESSO DO GIT**
### **COMANDOS NECESSÁRIOS:**
-----------------------------------------------------------
**PASSO 1:** *_CONFIGURE O "USER.NAME" E "USER.EMAIL:"_*

**git config --global user.name &&
git config --global user.email**

**PASSO 2:** *_GERE UMA CHAVE SSH:_*

**ssh-keygen**

**PASSO 3:** *_ADICIONE A CHAVE SSH PUBLICA "SSH-PUB" NAS CONFIGURAÇÕES DE CHAVE SSH DO GITHUB:_*

----------------------------------------------------------

## **DESFAZENDO COMMITS**
---------------------------------------------------------

**git reset --soft <commit>:** Mantém as alterações nos seus arquivos, desfazendo os commits, mas deixando as alterações no staging area. Isso permite refazer os commits com as alterações.

**git reset --mixed <commit>:** Desfaz os commits e remove as alterações do staging area, mas mantém as alterações nos seus arquivos. Você precisará adicionar novamente as mudanças ao staging area antes de fazer novos commits.

**git reset --hard <commit>:** Desfaz os commits e descarta todas as alterações feitas após o commit especificado. Cuidado, pois as alterações serão permanentemente perdidas.

**git rm --cached *.log** Remove os arquivos já rastreados no github.

## **VISUALIZANDO COMMITS**
---------------------------------------------------------

**git checkout <hash_do_commit>** Volta para um commit específico

**git checkout <nome_da_branch>** Volta para o estado atual.

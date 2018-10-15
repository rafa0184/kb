###MTA não inicia com problemas de permissão
Erro: Starting saslauthd...already running. postsuper: fatal: scan_dir_push: open directory defer: Permission denied postfix failed to start

Rodar o seguinte comando como root: 
```
/opt/zimbra/libexec/zmfixperms -e -v```

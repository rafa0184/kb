###MTA não inicia com problemas de permissão
Erro: Starting saslauthd...already running. postsuper: fatal: scan_dir_push: open directory defer: Permission denied postfix failed to start

Rodar o seguinte comando como root: 
```javascript
/opt/zimbra/libexec/zmfixperms -e -v```



###Rejecting false "mail from" addresses
Zimbra Collaboration 8.5 and above
For Zimbra Collaboration 8.5 and above, please use the next commands to increase the security and reject the logins for users that doesn't exist in the LDAP:

```javascript
zmprov mcf zimbraMtaSmtpdRejectUnlistedRecipient yes
zmprov mcf zimbraMtaSmtpdRejectUnlistedSender yes
zmmtactl restart
zmconfigdctl restart```

###Backup contas zimbra
```javascript
#By Rafael Ferreira
#Date 26/09/2018

#!/bin/bash

#Entra no diretorio de Backup
cd /opt/backup

#Cria um diretorio com a data do dia atual
mkdir $(date +%Y%m%d)box

#Executa a rotina de backup de todas as contas do zimbra
ZHOME=/opt/zimbra
ZBACKUP=$(date +%Y%m%d)box
ZCONFD=$ZHOME/conf
DATE=`date +"%a"`
ZDUMPDIR=$ZBACKUP
ZMPROV=/opt/zimbra/bin/zmprov
ZMBOX=/opt/zimbra/bin/zmmailbox

if [ ! -d $ZDUMPDIR ]; then
mkdir -p $ZDUMPDIR
fi
echo " Running zmprov ... "
       for mbox in `$ZMPROV -l gaa`
do
echo " Generating files from backup $mbox ..."
       $ZMBOX -z -m $mbox getRestURL "//?fmt=tgz" > $ZDUMPDIR/$mbox.tgz
done

#Copia o diretorio gerado para AWS S3
aws s3 cp --recursive ./$(date +%Y%m%d)box s3://Bucketname/mailaccounts/$(date +%Y%m%d)box

#Remove arquivos mais velhos que 10 dias
find /opt/backup/ -mmin +14400 | xargs rm -rf

```

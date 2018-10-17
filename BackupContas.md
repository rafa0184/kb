###Backup contas zimbra
```javascript
#!/bin/bash
ZHOME=/opt/zimbra

#ZBACKUP=/backup/mailbox

ZBACKUP=/mnt/backup

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
```

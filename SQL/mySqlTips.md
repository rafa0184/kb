###CONFIGURANDO ACESSO REMOTO EM SERVIDORES MYSQL

Qualquer máquina contida em uma rede, pode funcionar como servidor de banco de dados MySQL. 

Mas, primeiro, é preciso realizar a seguinte configuração na máquina servidor: 

1. Altere o arquivo de configuração do MySQL. Para isso, execute o seguinte comando, como root para abrir o arquivo de configuração: 
```javascript
 vim /etc/mysql/mysql.conf.d/mysqld.cnf 
```
2. Mude o IP da seguinte linha, para 0.0.0.0: 
```javascript
  bind-address  =  127.0.0.1 
```
Ficando assim: 
```javascript
bind-address = 0.0.0.0
```
3. Reinicie o serviço do MySQL: 
```javascript
 sudo /etc/init.d/mysql restart 
```
4. Entre no MySQL com o usuário root: 
```javascript
 mysql -uroot -p[senha] 
```
5. Conceda o seguinte privilégio: 
```javascript
mysql> GRANT ALL ON *.* TO 'root'@'%' IDENTIFIED BY '[senha]' WITH GRANT OPTION; 
```
Caso queira conceder acesso a uma máquina específica da rede: 
```javascript
mysql> GRANT ALL ON *.* TO 'root'@'[ip da máquina]' IDENTIFIED BY '[senha]' WITH GRANT OPTION; 
```
6. Execute o seguinte comando: 
```javascript
mysql> FLUSH PRIVILEGES; 
```
Obs.: caso queira testar a conexão, execute esse comando em uma máquina cliente da rede: 
```javascript
 myslq -uroot -p[senha] -h[IP do servidor] 
 ```
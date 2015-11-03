# Acesso-SSH-sem-senha
Como fazer acesso a computadores Linux sem senha

Após instalar o serviço SSH em seu host.

1 - Executar o seguinte comando na máquina cliente;

ssh-keygen -t rsa 

Este comando irá gerar a chave SSH
Será gerado dois arquivos, a chave da máquina e a chave pública, somente a chave pública que deve ser compartilhada com os servidores.
Estes arquivos ficam dentro do Diretório "/home/user/.ssh", No caso do usuario root "/root/.ssh"

2 - Copie sua chave pública para o computador que será acessado:

scp /home/user/.ssh/id_rsa.pub root@IpDoComputador:/tmp

3 - Após copiar, precisamos mover o conteudo para o arquivo de chaves autorizadas no servidor.

cat /tmp/id_rsa.pub >> /root/.ssh/authorized_keys 

Se o arquivo não existir, você deve cria-lo.

4 - Altere a segurança de seu arquivo de chaves no servidor (não é obrigatório).

chmod 644 /root/.ssh/authorized_keys
chmod 755 /root/.ssh

5 - Teste o acesso ao servidor.

ssh root@IpDoServidor

>Este é um guia básico para iniciantes sobre a instalação e configuração do VMware e Kali Linux.
# VMware

Baixe e instale o [VMware](https://download3.vmware.com/software/WKST-PLAYER-1750/VMware-player-full-17.5.0-22583795.exe). 

# Kali Linux
## Executando VM pré-montada do Kali Linux no VMware

Uma maneira rápida de executar uma VM Kali Linux é usar uma imagem pré-montada. A seção abaixo explica como obter e iniciar uma imagem Kali Linux pré-montada no VMware.

1. Baixe uma imagem pré-montada do Kali Linux no [site oficial](https://www.kali.org/get-kali/#kali-virtual-machines).

2. Selecione a arquitetura desejada e clique sobre a imagem ou no botão de download.

![](https://img001.prntscr.com/file/img001/nmHANRZdTQivYXXtcZACKw.png)

3. Descompacte o arquivo baixado.

4. Abra o **VMware** e selecione **Open a Virtual Machine**.

![](https://img001.prntscr.com/file/img001/39kTt18jTXin93rhYlyvkA.png)

5. Localize e abra o arquivo da máquina virtual do Kali Linux.

![](https://img001.prntscr.com/file/img001/lgtX5y3rToyRQ6B_vlBzEw.png)

Uma instância de VM do Kali Linux aparece no menu ao lado esquerdo.

6. A máquina foi criada e já está pronta para ser iniciada.

![](https://img001.prntscr.com/file/img001/TKAV9jE0R-W5FDnNeHlNug.png)
## Configurações da VM

Antes de iniciar, vou ajustar algumas configurações em **Edit virtual machine settings**. Se quiser pode deixar como está por padrão e iniciar.

**Memory**: Altere a quantidade de memória conforme necessário. Esteja atento as recomendações.

![](https://img001.prntscr.com/file/img001/F6EJ5JUlRcC_QnbF8n6Szw.png)

**Processors**: Escolha o número de processadores.

![](https://img001.prntscr.com/file/img001/exSBTY8hTheZN4YQWHZ0eA.png)

**Network Adapter**: Deixo em modo Bridged.

**O que é o modo Bridged?**
> É uma configuração que permite que a máquina virtual se conecte diretamente à rede física, como se fosse um dispositivo independente.

**Como funciona?**
>A máquina virtual recebe seu próprio endereço IP da rede física.
>Ela pode se comunicar com outros dispositivos na mesma rede, como se fosse um computador físico.

**Quando usar o modo Bridged?**
> Útil quando você precisa que a máquina virtual seja acessível na mesma rede que o seu computador físico.
> Bom para testes e desenvolvimento, pois permite interagir com outros dispositivos na rede como se fosse um dispositivo real.

Depois das configurações, inicie a máquina e pronto!

>Lembre-se de não mexer em configurações avançadas sem conhecimento prévio para evitar problemas.

---
# Iniciando

Ao iniciar a máquina, você deve colocar as credências padrão do Kali.
**Usuário**: kali
**Senha**: kali
>Kali mudou para uma [política de usuário não root](https://www.kali.org/docs/policy/kali-linux-user-policy/) por padrão [desde o lançamento de **2020.1**](https://www.kali.org/blog/kali-default-non-root-user/).

![](https://img001.prntscr.com/file/img001/pov6VCP7Rnm5MpoleBPjVw.png)

---
# O que fazer antes de começar a usar?

Antes de começar a usar o Kali Linux, siga alguns passos para configurar adequadamente o ambiente.

### Atualizar o sistema

Abra o terminal e execute os comandos abaixo para atualizar o sistema:
```zsh
sudo apt-get update
sudo apt-get upgrade
```
> O comando **sudo** do sistema operacional Unix permite a usuários comuns obter privilégios de outro usuário, em geral o super usuário, para executar tarefas específicas dentro do sistema de maneira segura e controlável pelo administrador. O nome é uma forma abreviada de se referir a *substitute user* do ou *super user do*.

![](https://img001.prntscr.com/file/img001/7bF497epR02oOU1k2nXzjw.png)

### Mudar as credenciais padrão

Altere o hostname com o comando abaixo, substituindo "novo" pelo nome desejado:
```zsh
hostnamectl set-hostname novo
```
Volte para o usuário root:
```zsh
sudo su
```
Mude a senha com o comando:
```zsh
passwd
```

### Verificar e modificar hosts

Abra o arquivo hosts com o comando:
```zsh
nano /etc/hosts
```

![](https://img001.prntscr.com/file/img001/YOYUhw0zSgOfoBhimLYzfQ.png)

Altere onde está "kali", substituindo "novo" pelo nome desejado.
```zsh
novo.localdomain novo
```

![](https://img001.prntscr.com/file/img001/mXoecCE_QJ6x1mE-YrssMA.png)

Aperte **ctrl+x** para fechar e confirme com y para sair e salvar.

![](https://img001.prntscr.com/file/img001/bEwReXvtR2ixsigHE_dX6w.png)

![](https://img001.prntscr.com/file/img001/V9c52LPRS0iu9Ezuzitnqg.png)

Com tudo atualizado, vamos verificar os hosts.

![](https://img001.prntscr.com/file/img001/1a0i1cGjRimDk3GnHegfFQ.png)

### Reiniciar a máquina

Após as alterações, reinicie a máquina e faça login com o usuário e senha kali.

![](https://img001.prntscr.com/file/img001/xb8GtjU8QBqTINlnOxa8uA.png)

### Criar um novo usuário

Crie um novo usuário com o comando abaixo, substituindo "novo" pelo nome desejado.
```zsh
sudo adduser novo
```

![](https://img001.prntscr.com/file/img001/ArxxsYOyS0-j4_yvUnE6Qg.png)

### Definir o novo usuário como sudoers

Abra o arquivo sudoers com o comando: 
```zsh
sudo visudo
```
Adicione uma nova linha para o novo usuário: 
```zsh
novo ALL=(ALL:ALL) ALL
```

![](https://img001.prntscr.com/file/img001/uTCbIabKSz2Sdz19O6XgVQ.png)

### Testar as permissões sudo do novo usuário

Faça login com o novo usuário e teste as permissões sudo:
```zsh
sudo ls /root
```
Se tudo estiver configurado corretamente, você deverá ser solicitado a inserir a senha do usuário e o comando será executado com privilégios de super usuário.

### Dicas adicionais:

- Evite usar a conta root para todas as tarefas. Utilize uma conta de usuário comum e eleve privilégios quando necessário com o comando **sudo**.
- Monitore constantemente o sistema e o tráfego de rede.
- Configure um firewall para controlar o tráfego de entrada e saída.
- Use o Kali Linux de maneira ética e responsável, lembrando que é uma distribuição voltada para testes de penetração e segurança.
# Fontes e material complementar

[Importar VM Kali VMware pré-fabricada](https://www.kali.org/docs/virtualization/import-premade-vmware/)
[Site Kali Linux](https://www.kali.org/)
[Documentação Kali Linux](https://www.kali.org/docs/introduction/default-credentials/)
[Ferramentas Kali Linux](https://www.kali.org/tools/)
[Fórum Kali Linux](https://forums.kali.org/)
[Discord Kali Linux](https://discord.kali.org)
[Como você escolhe entre o modo NAT e bridge para sua rede VM?](https://www.linkedin.com/advice/0/how-do-you-choose-between-nat-bridge-mode-your)
[Wiki Sudo](https://pt.wikipedia.org/wiki/Sudo)
[Curso Kali Linux - Configurando usuário, senha e nome da máquina](https://youtu.be/DOxt0C16TCQ)
[Change Linux Username & Hostname](https://youtu.be/VM64fH6tEEU)
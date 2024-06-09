>Este é um guia básico para iniciantes sobre a instalação e configuração do VirtualBox e Kali Linux.
# VirtualBox

Baixe e instale o [VirtualBox](https://www.virtualbox.org/wiki/Downloads). 

# Kali Linux
## Executando VM pré-montada do Kali Linux no VirtualBox

Uma maneira rápida de executar uma VM Kali Linux é usar uma imagem pré-montada. A seção abaixo explica como obter e iniciar uma imagem Kali Linux pré-montada no VirtualBox.

1. Baixe uma imagem pré-montada do Kali Linux no [site oficial](https://www.kali.org/get-kali/#kali-virtual-machines).

2. Selecione a arquitetura desejada e clique sobre a imagem ou no botão de download.

![](https://phoenixnap.com/kb/wp-content/uploads/2024/03/choosing-virtualbox-image-kali-on-virtualbox.png)

3. Descompacte o arquivo baixado.

4. Abra o **VirtualBox** e selecione **Adicionar (Add)**.

![](https://phoenixnap.com/kb/wp-content/uploads/2024/03/add-image-kali-on-virtualbox.png)

5. Localize e abra o arquivo da máquina virtual do Kali Linux.

![](https://phoenixnap.com/kb/wp-content/uploads/2024/03/selecting-vm-image-kali-on-virtualbox.png)

Uma instância de VM do Kali Linux aparece no menu ao lado esquerdo.

6. A máquina foi criada e já está pronta para ser iniciada.

![](https://phoenixnap.com/kb/wp-content/uploads/2024/03/starting-vm-based-on-image-kali-on-virtualbox.png)
## Configurações da VM

Antes de iniciar, vou ajustar algumas configurações. Se quiser pode deixar como está por padrão e iniciar.

### Geral

**Básico:** Altere o nome da máquina e a versão do sistema, se necessário.
**Avançado:** Configure a área de transferência compartilhada e arrastar e soltar (eu deixo ambos em Bidirecional).
**Descrição:** Adicione uma descrição para sua máquina (opcional).
**Criptografia de dados:** Criptografe suas informações para maior segurança, mas isso pode afetar o desempenho.

![](https://img001.prntscr.com/file/img001/0CBOm-1CTxWxrzom-z4elg.png)

### Sistema

**Placa-Mãe:** Configure memória base, ordem de boot, chipset, dispositivo de apontador e recursos estendidos.

![](https://img001.prntscr.com/file/img001/o-LxBmRvRcyCMNmYOiuYQQ.png)

**Processador:** Ajuste a quantidade de processadores e outras configurações relacionadas ao processador.

![](https://img001.prntscr.com/file/img001/ueuZQjkXRjG1G_AFShO_Uw.png)

**Aceleração:** Escolha a opção de aceleração desejada, como KVM.

![](https://img001.prntscr.com/file/img001/vA1ruOJKRtC6HIbD5VubRw.png)

### Monitor

**Tela(s):** Ajuste a memória de vídeo, número de monitores e ative a aceleração 3D, se necessário.
>Se você vai usar apenas aplicações básicas, não é necessário deixar a memória de vídeo no máximo. Você pode reduzir para economizar recursos do sistema. Experimente diminuir para a metade ou até onde você achar que está ok. Isso pode ajudar a melhorar o desempenho da sua máquina virtual, especialmente em sistemas com recursos limitados.

![](https://img001.prntscr.com/file/img001/wUnOpnkPTZSXVaLVUTma8Q.png)

### Armazenamento e Áudio

Deixe as configurações padrão, a menos que haja uma necessidade específica.

### Rede

Deixe conectado em modo Bridge para que a máquina virtual se conecte diretamente à rede física.

![](https://img001.prntscr.com/file/img001/R9tJbSTJRdaIwn3PG3fSHA.png)

**O que é o modo Bridged?**
> É uma configuração que permite que a máquina virtual se conecte diretamente à rede física, como se fosse um dispositivo independente.

**Como funciona?**
>A máquina virtual recebe seu próprio endereço IP da rede física.
>Ela pode se comunicar com outros dispositivos na mesma rede, como se fosse um computador físico.

**Quando usar o modo Bridged?**
> Útil quando você precisa que a máquina virtual seja acessível na mesma rede que o seu computador físico.
> Bom para testes e desenvolvimento, pois permite interagir com outros dispositivos na rede como se fosse um dispositivo real.

### Portas Seriais e USB

Não faça alterações, a menos que necessário.

### Pastas Compartilhadas

Adicione pastas compartilhadas conforme necessário para facilitar o acesso a arquivos.

![](https://img001.prntscr.com/file/img001/_uxTzxbzSjW0O3heDI_Oow.png)

### Interface do usuário

Não faço alterações, apenas clique em Ok para aplicar as configurações feitas e iniciar a máquina virtual.

>É importante notar que este guia não explora configurações avançadas do VirtualBox. Mexer nessas configurações sem conhecimento prévio pode causar problemas.

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

[Como instalar Kali Linux no VirtualBox](https://phoenixnap.com/kb/how-to-install-kali-linux-on-virtualbox)
[Site Kali Linux](https://www.kali.org/)
[Documentação Kali Linux](https://www.kali.org/docs/introduction/default-credentials/)
[Ferramentas Kali Linux](https://www.kali.org/tools/)
[Fórum Kali Linux](https://forums.kali.org/)
[Discord Kali Linux](https://discord.kali.org)
[Tipos de conexão de rede no VirtualBox](https://wltech.com.br/tipos-de-conexao-de-rede-no-virtualbox/) 
[Como você escolhe entre o modo NAT e bridge para sua rede VM?](https://www.linkedin.com/advice/0/how-do-you-choose-between-nat-bridge-mode-your)
[Wiki Sudo](https://pt.wikipedia.org/wiki/Sudo)
[Curso Kali Linux - Configurando usuário, senha e nome da máquina](https://youtu.be/DOxt0C16TCQ)
[Change Linux Username & Hostname](https://youtu.be/VM64fH6tEEU)
[Configurando uma Máquina virtual - Aula 02](https://youtu.be/vxzA77s3jlA)

>**NENHUMA** imagem da seção *Executando VM pré-montada do Kali Linux no VirtualBox* é minha, foram tiradas do primeiro link nas fontes.
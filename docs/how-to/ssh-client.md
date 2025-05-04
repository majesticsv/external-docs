---
sidebar_position: 1
---

# Como usar um cliente SSH

Este guia explica, de forma prática e acessível, como você pode se conectar a um servidor remoto usando um cliente SSH.

![SSH Connection](https://upload.wikimedia.org/wikipedia/commons/thumb/3/35/SSH_architecture_diagram.svg/1200px-SSH_architecture_diagram.svg.png)

## O que é SSH?

SSH (Secure Shell) é um protocolo que permite acessar outro computador de maneira segura através da rede. É muito usado para administrar servidores Linux ou acessar máquinas remotas.

Para utilizar o SSH, você precisa de:

- Um cliente SSH instalado no seu computador (o OpenSSH já vem no Linux e no macOS; no Windows você pode usar o PuTTY ou o OpenSSH do PowerShell)
- O endereço IP ou o nome do servidor
- Um nome de usuário válido
- Uma senha ou uma chave SSH configurada

---

## Como se conectar via terminal (Linux, macOS ou Windows PowerShell)

Se estiver usando Linux, macOS ou o PowerShell no Windows, o processo é simples. Abra o terminal e digite o comando:

```bash
ssh usuario@ip_do_servidor
```

Substitua `usuario` pelo seu nome de usuário no servidor e `ip_do_servidor` pelo endereço IP ou hostname.

**Exemplo:**

```bash
ssh joao@192.168.1.100
```

Na primeira vez que se conectar, o sistema vai perguntar se você confia no servidor. Digite `yes` e pressione Enter. Depois disso, você precisará digitar sua senha.

---

## Como se conectar usando o PuTTY (Windows)

Para quem prefere uma interface gráfica no Windows, o PuTTY é uma boa opção.

1. Baixe o [PuTTY aqui](https://www.putty.org/).
2. Instale e abra o programa.
3. Na tela inicial, insira o endereço IP ou hostname do servidor no campo **Host Name (or IP address)**.
4. Mantenha a porta como `22` e o **Connection type** como SSH.
5. Clique em **Open**.
6. Uma janela de terminal será aberta, onde você deverá digitar seu nome de usuário e sua senha.

![PuTTY Connection](https://the.earth.li/~sgtatham/putty/latest/x86/putty.png)

---

## Usando autenticação por chave SSH

Alguns servidores preferem (ou exigem) autenticação por chave SSH em vez de senha. Para isso, você precisa gerar um par de chaves no seu computador.

1. **Gerar a chave:**

   No terminal, digite:

   ```bash
   ssh-keygen -t rsa -b 4096 -C "seu_email@exemplo.com"
   ```

   Pressione Enter para aceitar os caminhos padrão. Uma chave pública e uma chave privada serão criadas.

2. **Enviar a chave pública para o servidor:**

   Use o comando:

   ```bash
   ssh-copy-id usuario@ip_do_servidor
   ```

3. Agora você pode acessar o servidor sem precisar digitar a senha:

   ```bash
   ssh usuario@ip_do_servidor
   ```

---

## Possíveis problemas e como resolver

- **Connection refused**: verifique se o serviço SSH está ativo no servidor e se a porta `22` está aberta no firewall.
- **Permission denied**: confirme se o nome de usuário, a senha ou as permissões da chave SSH estão corretos.
- **Timeout ou sem resposta**: cheque a conexão de rede e o endereço IP/hostname.

Caso continue com dificuldades, entre em contato com o administrador do sistema ou consulte a [documentação oficial do OpenSSH](https://www.openssh.com/manual.html).

---

## Conclusão

Com estas instruções, você já está apto a acessar servidores remotos de forma segura utilizando um cliente SSH, seja pelo terminal ou usando uma interface gráfica como o PuTTY. O SSH é uma ferramenta essencial para administradores de sistemas e desenvolvedores, garantindo acesso rápido e seguro aos ambientes de trabalho remotos.

---
sidebar_position: 2
---

# Como usar um cliente SFTP

Este guia explica, de forma prática e acessível, como transferir arquivos de forma segura entre seu computador e um servidor remoto usando um cliente SFTP.

![SFTP Connection](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/SFTP_connection_diagram.svg/1200px-SFTP_connection_diagram.svg.png)

## O que é SFTP?

SFTP (SSH File Transfer Protocol) é um protocolo que permite a transferência segura de arquivos através de uma conexão SSH. É uma alternativa segura ao FTP tradicional e é comumente usado para enviar ou baixar arquivos de servidores Linux.

Para utilizar o SFTP, você precisa de:

- Um cliente SFTP instalado no seu computador (o OpenSSH já inclui o comando `sftp` no Linux e macOS; no Windows, você pode usar o WinSCP ou o FileZilla)
- O endereço IP ou nome do servidor
- Um nome de usuário válido
- Uma senha ou uma chave SSH configurada

---

## Como se conectar via terminal (Linux, macOS ou Windows PowerShell)

No terminal, o comando básico para se conectar ao servidor é:

```bash
sftp usuario@ip_do_servidor
```

Substitua `usuario` pelo seu nome de usuário no servidor e `ip_do_servidor` pelo endereço IP ou hostname.

**Exemplo:**

```bash
sftp joao@192.168.1.100
```

Será solicitado que você digite sua senha para autenticação. Após conectar, o terminal mudará para o modo de comandos do SFTP.

Alguns comandos úteis dentro da sessão SFTP:

- `ls`: lista os arquivos no servidor remoto
- `cd nome_da_pasta`: muda de diretório no servidor remoto
- `lcd nome_da_pasta_local`: muda o diretório local
- `get arquivo`: baixa um arquivo do servidor para o seu computador
- `put arquivo`: envia um arquivo do seu computador para o servidor
- `exit` ou `quit`: encerra a sessão SFTP

---

## Como se conectar usando o WinSCP (Windows)

Se preferir uma interface gráfica no Windows, o WinSCP é uma ótima opção.

1. Baixe o [WinSCP aqui](https://winscp.net/eng/download.php).
2. Instale e abra o programa.
3. Na tela inicial, selecione o protocolo **SFTP**.
4. Preencha o **Host name** com o endereço IP ou hostname do servidor.
5. Digite o **User name** e a **Password**.
6. Mantenha a **Port number** como `22` (porta padrão do SFTP).
7. Clique em **Login** para conectar.

A interface exibirá os arquivos locais do lado esquerdo e os arquivos remotos do lado direito. Para transferir arquivos, basta arrastar de um lado para o outro.

![WinSCP Interface](https://winscp.net/eng/docs/screenshots/winscp.png)

---

## Usando autenticação por chave SSH

Caso o servidor utilize autenticação por chave SSH, você precisará informar a chave privada no cliente.

- **No terminal**, o comando é o mesmo, desde que sua chave SSH esteja configurada em `~/.ssh/id_rsa` ou especificada com o parâmetro `-i` no SSH.

- **No WinSCP**, acesse **Advanced > SSH > Authentication** e selecione o arquivo da sua chave privada.

Caso a chave esteja no formato OpenSSH e o programa exija o formato PuTTY, use o PuTTYgen para converter a chave.

---

## Possíveis problemas e como resolver

- **Connection refused**: verifique se o serviço SSH/SFTP está ativo no servidor e se a porta `22` está aberta no firewall.
- **Permission denied**: confirme se o nome de usuário, a senha ou as permissões da chave SSH estão corretos.
- **Timeout ou sem resposta**: verifique a conectividade da rede e o endereço IP/hostname.

Caso continue com dificuldades, entre em contato com o administrador do sistema ou consulte a [documentação oficial do WinSCP](https://winscp.net/eng/docs/start).

---

## Conclusão

Com estas instruções, você já pode transferir arquivos de forma segura entre seu computador e um servidor remoto usando um cliente SFTP, seja pelo terminal ou por uma interface gráfica como o WinSCP. O SFTP é uma ferramenta confiável e prática para administradores e usuários que precisam gerenciar arquivos remotamente.

## Preparação do ambiente de desenvolvimento JavaScript no linux

A seguir resumirei os passos para instalação e preparação das ferramentas necessárias no ambiente dev. Serão elas:

- [Visual Studio Code](https://code.visualstudio.com/)
- [Node.js - Usando NVM](https://github.com/nvm-sh/nvm)
- [Navegador Chromium](https://www.chromium.org/Home)
-
---
## Instalação de dependências

Primeiro atualizaremos a lista de pacotes. Para isso use:

```
sudo apt update
``` 

Agora instale algumas dependências necessárias para o nvm:

```
sudo apt install build-essential libssl-dev
```

Instale também o curl, que será necessário para baixar o script de instalação do nvm:

```
sudo apt install curl
``` 

---
## Node.js - Usando NVM

O `nvm` será usado para instalar o `Node.js`. Com ele é possível instalar qualquer versão do Node existente, além de alterar a versão em uso, configurar alguma versão como padrão, e remover qualquer uma delas caso necessário.

Para instalar o `nvm`, execute o seguinte comando:

```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
```

Para que o terminal reconheça `nvm` como um comando, você pode fechar o terminal e abrir novamente, ou rodar um dos seguintes comandos:

```
source ~/.bashrc # Caso use o bash
```

```
source ~/.zshrc # Caso use o zsh
```

Primeiro vamos listar as versões disponíveis, execute:

```
nvm ls-remote
```

Agora escolha a versão e rode o seguinte comando substituindo pela versão escolhida:

```
nvm install 16.13.1 # Ou use --lts no lugar da versão, para a última lts.
```

Você pode instalar quantas versões quiser, para trocar a versão a ser usada temporariamente, rode o seguinte comando:

```
nvm use 14.18.1 # Ou qualquer versão que você tenha instalado.
```

A primeira versão instalada se torna a `default`, que é um `aĺias` para a primeira versão instalada, isso significa que todo shell iniciará com essa versão, a menos que você a mude. Para fazer isso use:

```
nvm alias default 14.18.1 # Substitua a versão pela de sua escolha.
```

`default` que antes era um apelido para a primeira versão instalada, agora é o `alias` da versão `14.18.1`. Dessa forma, sempre que quiser trocar para a versão padrão, você pode usar `default` no lugar da versão quando rodar o comando `nvm use` .

---
## Snap

As próximas ferramentas serão instaladas via `snap`, para isso instale o `snapd` para ter acesso ao snap:

```
sudo apt install snapd snapd-xdg-open
```

Agora prossiga com os próximos pacotes.

---
## Visual Studio Code

Esse é provavelmente o editor de código mais usado atualmente, além de ser bem potente, gratuito para uso pessoal e comercial, e Open Source! 

Mas usa telemetria... Isso quer dizer que te rastreia, como esperado da Microsoft! Como alternativa a isso, dê uma olhada no [**codium**](https://vscodium.com/). Ele é um facilitador para que você não precise baixar nem compilar o código fonte do `vscode`, ele faz isso por você. É uma cópia exata do `Visual Studio Code`, exceto a telemetria, ícone, e outras personalizações da Microsoft.

Prosseguindo com o `vscode`, tenha certeza de ter o `snap` instalado. Se não tem, então volte ao passo anterior e instale.

Feito isso, agora você pode usar o `snap` para instalar o `Visual Studio Code` com o seguinte comando:

```
sudo snap install code --classic
```

![Visual Studio Code screenshot](https://code.visualstudio.com/assets/home/home-screenshot-linux.png)

---
## Navegador Chromium

Chromium é um navegador Open Source desenvolvido pelo Google, que o usa como base para o Chrome.

Novamente usaremos o `snap` , com ele já instalado execute:

```
sudo snap install chromium
```

![Chromium screenshot](https://dashboard.snapcraft.io/site_media/appmedia/2018/10/chromium-welcome.png)

---
## Insomnia

Insomnia é uma aplicação multiplataforma e Open Source desenvolvida com Electron. Usamos o Insomnia para fazer requisições em API REST.

Para instalar com o snap, é o mesmo padrão, execute:

```
sudo snap install insomnia
```

![Insomnia screenshot](https://miro.medium.com/max/1200/1*GFxrsUhiDg-LlDx17FGmkw.png)

---
## Beekeeper Studio (database client)

Beekeeper Studio é um cliente de banco de dados gratuito e de código aberto. Muito bonito, leve e funcional.

Você pode instalá-lo facilmente usando o snap:

```
sudo snap install beekeeper-studio
```

![Beekeeper Studio screenshot](https://www.beekeeperstudio.io/assets/img/blog/redshift-dark-5ecafab47fef77ddfae91c3d1646d55f21018c7d5911488504dd20c8dcd36bbb.png)

---
## Automatização com Shell Script

Baixe o este arquivo `.sh`.

[environment.sh](https://raw.githubusercontent.com/leonardolima99/environment-automatic/main/environment.sh)

Vá até o arquivo baixado pelo terminal, transforme-o em um arquivo executável:


```
chmod +x environment.sh
``` 

E caso use o zsh, execute o script usando o zsh:

```
zsh environment.sh
```

Caso use o bash como shell, execute o arquivo diretamente:

```
./environment.sh
```

Agora digite sua senha, tecle enter e espere. Ao final da execução, você terá todas essas ferramentas instaladas.

---
## Referências

[NVM - GitHub](https://github.com/nvm-sh/nvm)

[Visual Studio Code - Snapcraft](https://snapcraft.io/code)

[Chromium - Snapcraft](https://snapcraft.io/chromium)

[Beekeeper Studio - Snapcraft](https://snapcraft.io/beekeeper-studio)

[Insomnia - Snapcraft](https://snapcraft.io/insomnia)

---
Cover photo by [Lauren Mancke](https://unsplash.com/@laurenmancke?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/environment-dev?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
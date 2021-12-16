## Uso de fontes personalizadas no React Native

## Introdução

Para usar qualquer fonte no React Native você deve empacotar a fonte desejada, junto com o resto de seu aplicativo, visto que o dispositivo do usuário pode e provavelmente não terá a fonte necessária disponível em seu sistema.

Você pode pensar que isso é uma coisa dificílima, e muito complicada, mas verá que não é. Na verdade é a coisa mais fácil do mundo, tão fácil quanto ir na cozinha beber um copo de água.

Siga os passos que não tem erro.

---
## Escolher as fontes

Acesse https://fonts.google.com/ e siga os passos.

1. Pesquise o nome da fonte desejada;

2. Clique no card da fonte;

3. Escolha os estilos clicando em `+ Select this style`;  (Obs: Não importa qual você selecione, esse passo é apenas para ter acesso ao botão de download.)

4. Por fim, clique em `Download all`.

![Passo a passo google fonts](https://i.imgur.com/VYI4JaI.png)

Será baixado um arquivo `.zip` com todos os pesos dessa fonte.

Ele se parece assim:

![Arquivos .zip abertos](https://i.imgur.com/LIetKcB.png)

Aqui estão 2 exemplos, no primeiro o `.zip` tem as fontes estáticas por padrão. E no segundo elas estão dentro da pasta `static`, os 2 arquivos na raiz são `variable fonts` e você não os usará.

Extraia as fontes estáticas que você precisa em algum lugar.

Crie uma pasta na raiz do seu projeto chamada `assets`, e dentro dela uma pasta chamada `fonts`. Copie as fontes extraídas anteriormente para dentro da nova pasta `fonts`. Deve ficar assim:

![Captura de tela da pasta assets no vscode](https://i.imgur.com/pR2337m.png)

Agora siga para o próximo passo.

---
## Sobre *postscript name* do iOS

Aparentemente diferente do Android que pega o a fonte pelo seu nome de arquivo, o iOS pega a fonte pela propriedade `postscript name` do arquivo de fonte. Isso era um problema para fontes baixadas do https://fonts.google.com/ a algum tempo, você tinha que renomear o arquivo da fonte com o mesmo nome na propriedade `postscript name` para funcionar nos 2 sistemas.

Mas parece que o Google percebeu isso e agora os arquivos de fonte estão vindo já nomeados com o mesmo valor da propriedade `postscript name`

Se você usa linux, pode confirmar isto com o seguinte comando na pasta onde extraiu as fontes:

```
fc-scan Raleway-*.ttf | grep postscriptname # Substitua 'Raleway' pelo nome da sua fonte.
```
Este comando analisa todas as fontes cujo nomes começam com `Raleway-` e terminam com `.ttf`, e filtra a saída para mostrar apenas as linhas com `postscriptname`.

A saída deve ser algo como:

![Saída do comando fc-scan](https://i.imgur.com/uHnGDLl.png)

Repare que todas as 4 tem o nome de arquivo igual ao `postscriptname`.

---
## Arquivo de configuração

Na raiz do seu projeto, crie o arquivo `react-native.config.js` e preencha-o com o seguinte conteúdo:

```javascript
module.exports = {
  project: {
    ios: {},
    android: {},
  },
  assets: ['./assets/fonts'], // Pasta de fontes criada anteriormente
};

```
Simples, não?

---
## Vinculando fontes ao projeto.

Agora você precisa fazer com que o React Native encontre suas fontes quando você for usá-las.

Para fazer isso, também na raiz do seu projeto, execute no terminal:

```
react-native link
```
Isto jogará suas fontes para `android/app/src/main/assets/fonts', veja:

![Captura de tela da pasta de fontes vinculada](https://i.imgur.com/NA2CvwE.png)

Pronto! Agora é só usar a fonte chamando pelo nome do arquivo.

---
## Usando a fonte personalizada

Para usar a fonte dentro de uma tela no react native, é muito fácil. No seu estilo, onde você colocaria o nome de qualquer fonte, coloque o nome do arquivo. Dessa forma:

```javascript
const styles = StyleSheet.create({
  container: {
    margin: 20,
    justifyContent: 'center',
    alignItems: 'center',
  },
  textRegular: {
    fontFamily: 'Raleway-Regular', // Raleway com weight 400
    fontSize: 30,
  },
  textMedium: {
    fontFamily: 'Raleway-Medium', // Raleway com weight 500
    fontSize: 30,
  },
  textBold: {
    fontFamily: 'Raleway-Bold', // Raleway com weight 700
    fontSize: 30,
  },
});
``` 
Aqui estamos usando a fonte `Raleway` como exemplo, você pode usar qualquer fonte.

Repare que não usamos a propriedade `fontWeight`, já que o 'weight' já está separado por arquivo.

Com o estilo definido, basta invocá-lo em um `<Text>`.

```jsx
<View>
  <View style={styles.container}>
    <Text style={styles.textRegular}>Raleway-Regular</Text>
  </View>
  <View style={styles.container}>
    <Text style={styles.textMedium}>Raleway-Medium</Text>
  </View>
  <View style={styles.container}>
    <Text style={styles.textBold}>Raleway-Bold</Text>
  </View>
</View>
``` 

---
## Veja o resultado

![Captura de tela do resultado](https://i.imgur.com/HiP0Cgc.jpg)

Agora você já sabe como usar fontes personalizadas no React Native! Viu como é fácil?

Resumindo o processo sem as explicações, fica mais fácil ainda:

1. Baixe as fontes no https://fonts.google.com/;

2. Selecione os arquivos que deseja, e cole na pasta `./assets/fonts`;

3. Crie aquele arquivo bem pequeno, o `react-native.config.js`;

4. Rode um `react-native link` para vincular suas fontes;

5. Apenas use a fonte normalmente, pelo nome do arquivo.

Agora use de sua criatividade e habilidade em design, para escolher as melhores fontes para cada projeto.

---
Cover photo by <a href="https://unsplash.com/@brett_jordan?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Brett Jordan</a> on <a href="https://unsplash.com/s/photos/fonts?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>
  
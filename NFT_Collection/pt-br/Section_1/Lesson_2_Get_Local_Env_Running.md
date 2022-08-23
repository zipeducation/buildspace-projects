## 📚 Uma pequena introdução sobre blockchain

Antes de qualquer coisa, vamos precisar colocar nossa rede local de Ethereum para funcionar. É dessa maneira que vamos poder compilar e testar nosso código de contratos inteligentes! Você sabe como é necessário criar um ambiente local para trabalhar? Mesma coisa aqui!

Por enquanto, tudo o que você precisa saber é que um contrato inteligente é um pedaço de código que vive na blockchain. A blockhain é um lugar público onde qualquer um pode seguramente ler e escrever dados por uma taxa. Pense nisso em algo como a AWS ou o Heroku, com exceção de que ninguém a possui! Ela é mantida por milhares de pessoas aleatórias conhecidas como "mineradores".

O quadro maior aqui é:

1 -- Nós vamos escrever um contrato inteligente. Esse contrato tem toda a lógica ao redor dos nossos NFTs.

2 -- Nosso contrato inteligente será implantado na blockchain. Dessa maneira, qualquer pessoa no mundo terá acesso e poderá usar nosso contrato inteligente - e vamos deixar eles "mintarem" NFTs!

3 -- Nós vamos construir um site que permitirá que as pessoas "mintem" NFT's facilmente da nossa coleção.

Eu também recomendo ler [esses](https://solidity.web3dev.com.br/) documentos quando você quiser, por diversão. Esse é um dos melhores guias na internet para entender como o Ethereum funciona, na minha opinião.

## ⚙️ Ferramentas para o ambiente local.

Nós vamos usar muito uma ferramenta chamada **Hardhat**, a qual vai nos deixar compilar e testar rapidamente os contratos inteligentes localmente. Primeiro, você precisa ter instalado o node/npm. Se você não tiver, dê uma olhada [aqui](https://hardhat.org/tutorial/setting-up-the-environment.html). Se estiver usando Windows, pode também usar [essa página](https://www.web3dev.com.br/web3melk/como-preparar-o-seu-windows-para-participar-dos-bootcamps-da-web3dev-1dc3)

_Nota: eu estou usando o Node 16. Eu sei que algumas pessoas tiveram "erros de falta de memória" em versões mais velhas do Node, então se isso acontecer, use o Node 16!_

Depois, vamos para o terminal. Vá em frente e `cd` (comando para mudar de pasta) para o diretório que você quer trabalhar. Uma vez que você estiver lá, rode os seguintes comandos:

```bash
mkdir epic-nfts
cd epic-nfts
npm init -y
npm install --save-dev hardhat@2.9.9
```

Você pode ver uma mensagem sobre vulnerabilidades depois de rodar o último comando e instalar o Hardhat. Toda vez que você instala algo do NPM, existe uma checagem de segurança, que é feita para ver se algum dos pacotes da biblioteca que você está instalando tem alguma vulnerabilidade reportada. Isso é mais um aviso para que você esteja ciente! Pesquise um pouco mais sobre as vulnerabilidades no Google se quiser saber mais!

## 🔨 Coloque o projeto teste para funcionar

Legal, agora devemos ter o hardhat. Vamos fazer um projeto teste funcionar.

```
npx hardhat
```

_Nota: Se você está no Windows usando Git Bash para instalar hardhat, você pode encontrar um erro nesse passo (HH1). Você pode tentar usar a CMD do Windows para instalar o HardHat se tiver muitos problemas. Informações adicionais podem ser encontradas [aqui](https://github.com/nomiclabs/hardhat/issues/1400#issuecomment-824097242)._

Escolha a opção de criar um projeto básico de teste (*Create a basic sample project*). Diga "sim" para tudo.

O projeto vai pedir para instalar `hardhat-waffle` e `hardhat-ethers`. Essas são coisinhas que vamos usar depois.

Vá em frente e instale essas outras dependências no caso delas não terem sido instaladas automaticamente.

```bash
npm install --save-dev @nomiclabs/hardhat-waffle ethereum-waffle chai @nomiclabs/hardhat-ethers ethers
```

Você também vai querer instalar algo chamado **OpenZeppelin**, que é uma outra biblioteca muito usada para desenvolver contratos inteligentes seguros. Nós vamos aprender mais sobre isso depois. Por agora, só instale-o.

```bash
npm install @openzeppelin/contracts
```

Depois rode:

```bash
npx hardhat run scripts/sample-script.js
```

Você deve ver algo parecido com isso:

![Untitled](https://i.imgur.com/LIYT9tf.png)

Boom! Se você ver isso, significa que seu ambiente local está configurado **e** você também rodou/implantou um contrato inteligente para uma blockchain local.

Isso é bastante épico. Vamos entrar em mais detalhes, mas basicamente o que está acontecendo aqui passo a passo é:

1. Hardhat compila o seu código inteligente de solidity para bytecode.
2. Hardhat vai rodar uma "blockchain local" no seu computador. É como uma mini versão de testes do Ethereum rodando no seu computador para deixar você testar coisas rapidamente!
3. Hardhat vai então "implantar" (deploy) seu contrato compilado para a blockchain local. Isso é o endereço que você vê no final ali. É o nosso contrato implantado (deployed), na nossa mini versão do Ethereum.

Se você estiver curioso, sinta-se a vontade para olhar o código dentro do projeto e ver como ele funciona. Especificamente, olhe o arquivo `Greeter.sol` que é o contrato inteligente e `sample-script.js` que roda o contrato.

Uma vez que tiver acabado de explorar, vamos para a próxima seção e começar nosso próprio contrato NFT.

🚨 Relatório de progresso.
-------------------
Poste um print do seu terminal com a saída do `sample-script.js` no canal #progress do Discord :).
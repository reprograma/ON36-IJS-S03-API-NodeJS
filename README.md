<h1 align="center">
  <img src="assets/reprograma-fundos-claros.png" alt="logo reprograma" width="500">
</h1>

# Tema da Aula

Turma Online ON36 - Imersão JavaScript | Semana 03 | 2024 | Professora Beatriz Duarte

### Instruções
Antes de começar, vamos organizar nosso setup.
* Fork esse repositório 
* Clone o fork na sua máquina (Para isso basta abrir o seu terminal e digitar `git clone url-do-seu-repositorio-forkado`)
* Entre na pasta do seu repositório (Para isso basta abrir o seu terminal e digitar `cd nome-do-seu-repositorio-forkado`)
* [Add outras intrucoes caso necessario]

### Objetivo
- Compreender sobre o Node.Js e TypeScript
- Compreender os conceitos de protocolos de comunicação focado em HTTP
- Criar uma API 

### Resumo
O que veremos na aula de hoje?
- [Construção de uma API](#tema-da-aula)
    - [Instruções](#instruções)
    - [Objetivo](#objetivo)
    - [Resumo](#resumo)

- [Conteúdo](#conteúdo)
  - [História da Internet](#historia-internet)
    - [Endereçamento e Protocolo IP](#enderecamento-ip)
    - [DNS](#dns)
    - [Conceitos importantes](#conceitos)
  - [Node.js](#historia-internet)
    - [O que é o Node.Js](#oque-e-node)
    - [História e evolução](#historia-node)
    - [Vantagens de uso](#vantagens)
    - [Modulos](#modulos)
    - [Node.js e Typescript](#node-e-typescript)
  - [Protocolos de Comunicação](#protocolos-comunicação)
  - [HTTP](#http)
    - [GET](#get)
    - [POST](#post)
    - [PUT](#put)
    - [PATCH](#patch)
    - [DELETE](#delete)
    - [Status Code](#status-code)
  - [API](#api)
  - [API REST](#rest)
  - [Exercícios](#exercícios)
  - [Material da aula](#material-da-aula)
  - [Links Úteis](#links-úteis)

# Conteúdo
<a id="historia-internet"></a>

## A História da Internet

A Internet é uma rede global de computadores interconectados que permite a comunicação e o compartilhamento de informações entre usuários em todo o mundo. Aqui está uma visão geral simplificada de como a Internet funciona.

### Como a Internet Começou

A ideia de criar a Internet surgiu da necessidade de compartilhar informações e recursos entre instituições de pesquisa e acadêmicas, inicialmente nos Estados Unidos. Décadas atrás, os computadores estavam isolados em suas próprias redes e não podiam se comunicar uns com os outros. No entanto, com o avanço da tecnologia e a crescente demanda por troca de informações, surgiu a necessidade de uma rede que pudesse conectar computadores em diferentes locais geográficos.

A concepção inicial da Internet remonta ao final da década de 1960 e início da década de 1970, com o desenvolvimento do projeto ARPANET (Advanced Research Projects Agency Network). Financiado pela ARPA (Advanced Research Projects Agency), uma agência do Departamento de Defesa dos Estados Unidos, o ARPANET foi o precursor da Internet moderna.

O objetivo principal do ARPANET era criar uma rede de comunicação robusta e descentralizada que pudesse resistir a falhas e ataques, permitindo que os pesquisadores e cientistas compartilhassem recursos de computação e trocassem informações de forma eficiente. O conceito de uma rede de comutação de pacotes, onde os dados são divididos em pequenos pacotes e encaminhados de forma independente, foi fundamental para o design do ARPANET.

À medida que o ARPANET evoluía, outras redes de computadores foram criadas, como a NSFNET (National Science Foundation Network), que expandiu o acesso à Internet para instituições acadêmicas e de pesquisa em todo os Estados Unidos.

Com o tempo, a Internet cresceu além de seu escopo original de pesquisa acadêmica e militar, transformando-se em uma rede global que conecta bilhões de dispositivos em todo o mundo. A ideia subjacente à Internet continua sendo a mesma: fornecer uma plataforma para compartilhar informações e recursos de forma descentralizada e colaborativa.

### Como a Internet Funciona

A Internet funciona através da interconexão de dispositivos, redes e infraestrutura de rede em todo o mundo, permitindo a comunicação e o compartilhamento de informações em escala global.

<a id="enderecamento-ip"></a>

**Endereçamento IP:**

Um endereço IP (Internet Protocol) é um identificador único para cada dispositivo conectado à Internet ou a uma rede local. É como o endereço de uma casa, que ajuda a identificar onde algo está localizado.

**Tipos de Endereços IP:**

1. **IPv4:** É a versão mais comum e utiliza um formato de 32 bits, resultando em aproximadamente 4 bilhões de endereços únicos. Um endereço IPv4 tem a aparência de algo como `192.168.1.1`.
2. **IPv6:** Devido ao esgotamento dos endereços IPv4, o IPv6 foi introduzido. Ele utiliza um formato de 128 bits, permitindo um número muito maior de endereços. Um endereço IPv6 parece algo como `2001:0db8:85a3:0000:0000:8a2e:0370:7334`.

### Protocolo IP

O Protocolo IP (Internet Protocol) é o conjunto de regras que governa o formato e a transmissão dos dados pela rede. Ele garante que os dados sejam encaminhados do remetente ao destinatário corretamente.

<a id="dns"></a>

**Resolução de Nomes de Domínio (DNS):**
O Domain Name System (DNS) é um sistema distribuído de resolução de nomes que traduz nomes de domínio legíveis por humanos (como example.com) em endereços IP, permitindo que os usuários acessem sites e serviços usando nomes de domínio em vez de endereços IP.

Vamos ilustrar isso com um exemplo prático:

1. **Você quer visitar um site (por exemplo, [www.exemplo.com](http://www.exemplo.com/)):**
    - Você digita o endereço no seu navegador.
    - O navegador precisa saber o endereço IP do site para se conectar a ele. Para isso, ele consulta um servidor DNS (Domain Name System) para traduzir `www.exemplo.com` em um endereço IP, como `192.0.2.1`.

<a id="conceitos-importantes"></a>

**Redes Locais e Dispositivos de Rede:**
Os dispositivos individuais, como computadores, smartphones e servidores, estão conectados a redes locais, como redes Wi-Fi, redes corporativas ou redes móveis. Os dispositivos de rede, como roteadores e switches, são usados para encaminhar o tráfego de dados entre os dispositivos em uma rede local e entre diferentes redes.

**Provedores de Serviços de Internet (ISPs):**
Os ISPs fornecem acesso à Internet para os usuários, conectando suas redes locais à infraestrutura de Internet mais ampla. Os ISPs possuem infraestrutura de rede, como cabos de fibra óptica, linhas de comunicação por satélite ou torres de celular, que são usadas para transmitir dados pela Internet.

**Roteamento de Pacotes:**
Quando você envia uma mensagem de texto pelo WhatsApp, ela é dividida em pequenas partes chamadas pacotes. Esses pacotes viajam pela Internet de forma independente, encontrando a melhor rota até o destinatário. Os roteadores funcionam como guardas de trânsito, direcionando cada pacote pelo caminho mais eficiente.

**Protocolos de Comunicação:**
Além do Protocolo IP, vários outros protocolos de comunicação são usados na Internet para diferentes finalidades, incluindo o Transmission Control Protocol (TCP) para comunicação confiável de dados, o User Datagram Protocol (UDP) para comunicação não confiável em tempo real, o Hypertext Transfer Protocol (HTTP) para comunicação web, o Simple Mail Transfer Protocol (SMTP) para comunicação de e-mail, entre outros.

- **TCP/IP:** Imagine que você está fazendo uma videochamada. O TCP garante que os dados da sua chamada sejam entregues corretamente e na ordem certa, enquanto o IP cuida de enviar esses dados pelo caminho mais eficiente.
- **HTTP:** Quando você acessa um site no navegador, o HTTP é o protocolo que define como seu computador solicita as páginas e como o servidor web as entrega de volta para você.

**Rede de Camada Física:**
A infraestrutura física da Internet inclui cabos de fibra óptica submarinos, cabos de fibra terrestres, satélites de comunicação e outras tecnologias de transmissão de dados que permitem a comunicação global.

<a id="oque-e-node"></a>

## Node.js
### O que é Node.js?

[Node.js](https://nodejs.org/en) é um ambiente de tempo de execução (runtime) JavaScript de código aberto e multiplataforma que é utilizado para executar código JavaScript do lado do servidor. Ele permite que os desenvolvedores construam aplicações web escaláveis e de alto desempenho, usando JavaScript tanto no lado do cliente quanto no servidor.

Ele é baseado no motor V8 JavaScript da Google, que é o mesmo motor utilizado no navegador Google Chrome. Ele utiliza uma arquitetura orientada a eventos e assíncrona, que permite que aplicações Node.js lidem com um grande número de conexões simultâneas de forma eficiente.

<a id="historia-node"></a>

### História e evolução do Node.js

O [Node.js](https://nodejs.org/en) foi criado em 2009 por Ryan Dahl, como uma forma de permitir que JavaScript fosse executado no lado do servidor. A motivação por trás do Node.js era fornecer um ambiente de desenvolvimento rápido e eficiente para aplicações web em tempo real, como aplicações de bate-papo e streaming de vídeo.

Desde então, o Node.js passou por várias versões e continua a evoluir rapidamente. Em 2015, o Node.js Foundation foi estabelecido para supervisionar o desenvolvimento e governança do Node.js. Em 2019, o projeto Node.js e o projeto JavaScript runtime da Google, o V8, foram unificados sob a Fundação OpenJS, fornecendo uma estrutura mais colaborativa para o desenvolvimento contínuo.

<a id="vantagens"></a>

### Vantagens

Algumas das vantagens do Node.js incluem:

- **JavaScript em ambos os lados:** O Node.js permite que as pessoas desenvolvedoras usem JavaScript tanto no lado do cliente quanto no servidor, simplificando o desenvolvimento de aplicações web full-stack.
- **Desempenho e escalabilidade:** O modelo assíncrono e orientado a eventos do Node.js permite que ele lide com um grande número de conexões simultâneas de forma eficiente, tornando-o adequado para aplicações web em tempo real e de alto tráfego.
- **Ecossistema NPM**: O Node.js possui um vasto ecossistema de pacotes e bibliotecas disponíveis no NPM (Node Package Manager), o que facilita a construção de aplicações complexas com componentes reutilizáveis.
- **Comunidade ativa:** O Node.js possui uma comunidade grande e ativa de desenvolvedores, o que significa que há muitos recursos, tutoriais e suporte disponíveis.

Alguns casos de uso comuns do Node.js incluem:

- Aplicações web em tempo real, como aplicações de bate-papo e streaming de vídeo.
- Aplicações de API RESTful e microserviços.
- Aplicações de Internet das Coisas (IoT).
- Aplicações de processamento de dados em tempo real.
- Servidores de jogos multiplayer online.

**Características gerais**

Cliente Web: Representa o navegador ou qualquer outro cliente que faça solicitações para o servidor.

- **Servidor Node.js:** O ambiente de tempo de execução Node.js, onde o código JavaScript do lado do servidor é executado.
- **Módulos Node.js:** Representa os módulos do Node.js, que são blocos de código JavaScript reutilizáveis. Os módulos podem ser bibliotecas internas do Node.js ou módulos de terceiros instalados via NPM.
- **Event Loop:** O Event Loop é uma parte fundamental do Node.js que permite que ele seja assíncrono e orientado a eventos. Ele gerencia a execução de tarefas assíncronas e garante que o código JavaScript seja executado de forma eficiente.
- **APIs de Sistema e I/O:** O Node.js fornece APIs para interagir com o sistema operacional e realizar operações de entrada/saída, como leitura e gravação de arquivos, manipulação de rede, etc.
- **NPM (Node Package Manager):** O NPM é o gerenciador de pacotes padrão do Node.js. Ele permite que os desenvolvedores instalem, compartilhem e gerenciem pacotes de código JavaScript de terceiros em seus projetos.

O Node.js é uma poderosa plataforma para construir aplicações web escaláveis e de alto desempenho, e sua popularidade continua a crescer devido às suas vantagens e casos de uso diversificados.

<a id="modulos"></a>

### Módulos

**O que são módulos Node.js?**

Os módulos Node.js são blocos de código JavaScript reutilizáveis que encapsulam funcionalidades específicas. Eles permitem que você divida seu código em partes mais gerenciáveis e modulares, o que facilita a manutenção e reutilização do código.

Existem dois tipos principais de módulos no Node.js:

- Módulos internos do Node.js: Estes são os módulos incorporados ao próprio Node.js e são acessados sem a necessidade de instalação adicional. Alguns exemplos incluem o módulo fs para manipulação de arquivos, o módulo http para criar servidores HTTP, o módulo path para manipulação de caminhos de arquivos, entre outros.
- Módulos de terceiros: Estes são módulos criados pessoas desenvolvedoras externos e disponibilizados via NPM (Node Package Manager) ou outro gerenciador de pacotes. Você pode usar esses módulos em suas aplicações Node.js para adicionar funcionalidades adicionais. Por exemplo, o módulo express é uma popular framework web para Node.js, e o módulo lodash fornece utilitários para manipulação de arrays, objetos, etc.

Exportando e importando módulos:

Em Node.js, você pode exportar partes de um módulo usando a propriedade module.exports e importá-las em outros arquivos usando a função require().

Por exemplo, vamos criar um módulo simples chamado `math.ts` que exporta algumas funções matemáticas:

**math.ts:**

```
// math.ts
export function soma(a: number, b: number): number {
  return a + b;
}

export function subtracao(a: number, b: number): number {
  return a - b;
}
```

Agora, podemos importar e usar essas funções em outro arquivo:

**app.ts**

```
// app.ts
import { soma, subtracao } from './math';

console.log(soma(2, 3)); // Saída: 5
console.log(subtracao(5, 3)); // Saída: 2

```

**Organizando módulos:**

Você pode organizar seus módulos em diretórios para manter seu código mais organizado e modular. Por exemplo:

```
meu_projeto/
  |- math/
  |   |- index.ts
  |   |- soma.ts
  |   |- subtracao.ts
  |- app.ts
```

Os módulos Node.js são uma maneira poderosa de organizar e reutilizar código JavaScript em suas aplicações. Eles permitem uma abordagem modular para o desenvolvimento, tornando o código mais fácil de entender, manter e compartilhar.

<a id="node-e-typescript"></a>

TypeScript é uma linguagem de programação de código aberto desenvolvida pela Microsoft. É um superset do JavaScript, o que significa que adiciona recursos ao JavaScript, como tipagem estática opcional, interfaces, tipos genéricos e outras ferramentas para facilitar a detecção de erros durante o desenvolvimento. TypeScript é projetado para ser transpilado para JavaScript, tornando-o compatível com qualquer ambiente que execute JavaScript, incluindo navegadores e servidores.

O uso do TypeScript traz várias vantagens, especialmente em projetos de grande escala e em equipes de desenvolvimento. Aqui estão algumas das principais vantagens:

**Tipagem Estática**

- **Detecção de Erros em Tempo de Compilação**: A tipagem estática permite identificar erros antes de executar o código, reduzindo bugs e problemas de tipo.
- **Autocompletar e IntelliSense**: Ferramentas de desenvolvimento podem fornecer autocompletar e dicas de código mais precisas, melhorando a produtividade.

**Melhoria na Legibilidade e Manutenção do Código**

- **Definição Clara de Tipos**: Com tipos explícitos, o código se torna mais fácil de entender e manter.
- **Interfaces e Tipos Genéricos**: Permite criar abstrações mais claras e reutilizáveis, facilitando a manutenção e extensão do código.

 **Ferramentas de Desenvolvimento Melhoradas**

- **Refatoração Segura**: Ferramentas como o Visual Studio Code oferecem refatoração automática e segura, graças à compreensão profunda do código.
- **Verificação de Tipo**: TypeScript ajuda a evitar erros comuns, como chamadas de função com argumentos errados ou acesso a propriedades inexistentes.

<a id="protocolos-comunicacao"></a>

Protocolos de comunicação são conjuntos de regras e normas que permitem a troca de informações entre dispositivos em uma rede. Eles definem como os dados são formatados, transmitidos e recebidos, garantindo que os dispositivos possam se comunicar de maneira eficaz e compreensível. Abaixo, estão alguns dos principais protocolos de comunicação usados na internet e em redes de computadores:

## Protocolos de comunicação

### Principais Protocolos de Comunicação

#### TCP/IP (Transmission Control Protocol/Internet Protocol)

- **Descrição**: Conjunto de protocolos fundamentais para a internet.
- **TCP**: Garante a entrega confiável e ordenada de um fluxo de bytes entre dois dispositivos. Divide os dados em pacotes, transmite-os e garante que sejam recebidos e montados na ordem correta.
- **IP**: Responsável pelo endereçamento e roteamento dos pacotes entre dispositivos em redes diferentes. Define os endereços IP que identificam dispositivos na rede.

#### HTTP/HTTPS (Hypertext Transfer Protocol/Secure)

- **HTTP**: Protocolo usado para transferir páginas web e outros recursos na internet. Funciona no modelo de requisição-resposta entre clientes (navegadores) e servidores.
- **HTTPS**: Versão segura do HTTP, que utiliza criptografia SSL/TLS para proteger a comunicação entre o cliente e o servidor, garantindo confidencialidade e integridade dos dados.

#### FTP (File Transfer Protocol)

- **Descrição**: Protocolo para transferência de arquivos entre sistemas em uma rede TCP/IP.
- **Exemplo**: Enviar e baixar arquivos de servidores, gerenciar arquivos em servidores remotos.

#### SMTP (Simple Mail Transfer Protocol)

- **Descrição**: Protocolo para envio de e-mails.
- **Exemplo**: Envio de e-mails de clientes de e-mail para servidores de e-mail e entre servidores de e-mail.

#### IMAP/POP3 (Internet Message Access Protocol/Post Office Protocol 3)

- **IMAP**: Protocolo para leitura e gerenciamento de e-mails armazenados em um servidor. Permite a sincronização de e-mails em múltiplos dispositivos.
- **POP3**: Protocolo para download de e-mails do servidor para um único dispositivo. Uma vez baixados, os e-mails são geralmente removidos do servidor.

#### DNS (Domain Name System)

- **Descrição**: Protocolo que traduz nomes de domínio (como [www.exemplo.com](http://www.exemplo.com/)) em endereços IP que podem ser entendidos pelos dispositivos na rede.
- **Exemplo**: Facilitar a navegação na web, permitindo o uso de nomes de domínio amigáveis em vez de endereços IP numéricos.

#### DHCP (Dynamic Host Configuration Protocol)

- **Descrição**: Protocolo que atribui dinamicamente endereços IP a dispositivos em uma rede.
- **Exemplo**: Facilitar a configuração de dispositivos em redes, permitindo que recebam automaticamente um endereço IP e outras configurações de rede.

#### SSH (Secure Shell)

- **Descrição**: Protocolo para acesso remoto seguro a dispositivos em uma rede.
- **Exemplo**: Acessar remotamente servidores e dispositivos para administração e gerenciamento seguros.

#### WebSocket

- **Descrição**: Protocolo que permite comunicação bidirecional em tempo real entre clientes e servidores.
- **Exemplo**: Aplicações que requerem atualizações instantâneas, como chats online, notificações em tempo real e jogos multiplayer.

#### Exemplos Práticos

- **Navegação na Web**: O navegador utiliza o HTTP/HTTPS para solicitar páginas web de servidores.
- **Envio de E-mails**: Clientes de e-mail utilizam SMTP para enviar e-mails e IMAP/POP3 para recebê-los.
- **Transferência de Arquivos**: FTP é usado para enviar e baixar arquivos de servidores.
- **Conexão Remota**: SSH permite acessar remotamente servidores para administração.

Os protocolos de comunicação são essenciais para garantir que dispositivos de diferentes fabricantes e sistemas operacionais possam se comunicar de maneira eficiente e segura na internet e em outras redes de computadores.

<a id="http"></a>

## HTTP

### Métodos HTTP

<a id="get"></a>

#### GET

- **Descrição**: Utilizado para solicitar dados de um servidor. É um método idempotente, o que significa que várias requisições GET com o mesmo parâmetro não alteram o estado do recurso.
- **Uso comum**: Obter páginas web, imagens, dados de APIs, etc.

<a id="post"></a>

#### POST

- **Descrição**: Utilizado para enviar dados ao servidor, geralmente para criar um novo recurso. O corpo da requisição contém os dados a serem enviados.
- **Exemplo**: Enviar formulários, criar novos registros em um banco de dados, enviar dados para processamento.

<a id="put"></a>

#### PUT

- **Descrição**: Utilizado para atualizar completamente um recurso existente no servidor. Se o recurso não existir, o PUT pode criar um novo.
- **Exemplo**: Atualizar informações de um recurso, como modificar um perfil de usuário ou atualizar uma entrada de banco de dados.

<a id="patch"></a>

#### PATCH

- **Descrição**: Utilizado para atualizar parcialmente um recurso existente. Apenas as partes do recurso que precisam ser modificadas são enviadas.
- **Exemplo**: Realizar atualizações parciais em um recurso, como alterar um único campo de um registro.

<a id="delete"></a>

#### DELETE

- **Descrição**: Utilizado para deletar um recurso do servidor.
- **Exemplo**: Remover registros de um banco de dados, excluir arquivos, deletar contas de usuário.

<a id="status-code"></a>

#### Status Codes

Os códigos de status HTTP são enviados pelo servidor em resposta a uma requisição HTTP do cliente. Eles indicam se a requisição foi bem-sucedida, se houve um erro ou se há necessidade de ações adicionais. Alguns dos mais comuns:

#### 1xx: Informativo

- **100 Continue**: O servidor recebeu o cabeçalho da requisição e o cliente pode continuar a enviar o corpo da requisição.
- **101 Switching Protocols**: O servidor está mudando os protocolos, conforme solicitado pelo cliente.

#### 2xx: Sucesso

- **200 OK**: A requisição foi bem-sucedida.
- **201 Created**: A requisição foi bem-sucedida e um novo recurso foi criado.
- **204 No Content**: A requisição foi bem-sucedida, mas não há conteúdo para enviar na resposta.

#### 3xx: Redirecionamento

- **301 Moved Permanently**: O recurso solicitado foi movido permanentemente para uma nova URL.
- **302 Found**: O recurso solicitado foi encontrado em uma URL diferente.
- **304 Not Modified**: O recurso não foi modificado desde a última requisição.

#### 4xx: Erro do Cliente

- **400 Bad Request**: A requisição é inválida ou malformada.
- **401 Unauthorized**: A autenticação é necessária e falhou ou não foi fornecida.
- **403 Forbidden**: O servidor entende a requisição, mas se recusa a autorizá-la.
- **404 Not Found**: O recurso solicitado não foi encontrado no servidor.

#### 5xx: Erro do Servidor

- **500 Internal Server Error**: O servidor encontrou uma condição inesperada que impediu de atender a requisição.
- **502 Bad Gateway**: O servidor, ao agir como gateway ou proxy, recebeu uma resposta inválida do servidor upstream.
- **503 Service Unavailable**: O servidor está indisponível no momento (por exemplo, sobrecarregado ou em manutenção).

Esses métodos e códigos de status são fundamentais para o funcionamento das aplicações web e são amplamente utilizados no desenvolvimento de APIs RESTful.

<a id="api"></a>

## API (Interface de Programação de Aplicativos)

Uma API (Interface de Programação de Aplicativos) é um conjunto de regras e definições que permite que diferentes softwares se comuniquem entre si. Ela define as maneiras pelas quais diferentes componentes de software podem interagir, permitindo que aplicativos compartilhem dados e funcionalidades.

**Utilizações Comuns de APIs:**

- **Integração de Sistemas:** As APIs permitem que diferentes sistemas e aplicativos se comuniquem entre si, facilitando a troca de dados e funcionalidades. Por exemplo, uma API pode ser usada para integrar um sistema de gerenciamento de vendas com um sistema de contabilidade.
- **Desenvolvimento de Aplicativos Móveis e Web:** Muitos aplicativos móveis e web dependem de APIs para acessar dados e serviços externos. Por exemplo, um aplicativo de previsão do tempo pode usar uma API de serviços meteorológicos para obter informações atualizadas sobre o clima.
- **Desenvolvimento de Plataformas:** Empresas que oferecem serviços baseados em nuvem muitas vezes fornecem APIs para permitir que os desenvolvedores criem aplicativos que se integram perfeitamente com suas plataformas. Por exemplo, o Google Maps API permite que os desenvolvedores incorporem mapas interativos em seus aplicativos.

<a id="rest"></a>

## API REST (Representational State Transfer)

É um estilo arquitetural utilizado para projetar sistemas de software distribuídos, especialmente na web. Ela define um conjunto de princípios e padrões que promovem a criação de serviços web bem estruturados, escaláveis e de fácil manutenção. Uma API RESTful é uma API que segue os princípios e as práticas definidas pela arquitetura REST.

A arquitetura REST (Representational State Transfer) é um estilo arquitetural para projetar sistemas de software distribuídos, especialmente na web. Ela foi introduzida por Roy Fielding em sua tese de doutorado em 2000 e se tornou um padrão amplamente adotado para a construção de APIs web.

Alguns dos princípios-chave de uma API REST incluem:

-  **Recursos Identificáveis:** Os recursos da API (por exemplo, usuários, posts, produtos) são identificados por URLs únicas e bem definidas.
-  **Operações CRUD:** As operações CRUD (Create, Read, Update, Delete) são mapeadas para os métodos HTTP: POST, GET, PUT/PATCH e DELETE, respectivamente.
- **Stateless (Sem Estado):** As requisições para o servidor devem conter todas as informações necessárias para que o servidor entenda e processe a requisição. Isso significa que o servidor não mantém informações sobre o estado do cliente entre requisições.
- **Padrão de Resposta:** As respostas do servidor devem ser consistentes e seguir um padrão bem definido. Isso pode incluir o uso de códigos de status HTTP apropriados, como 200 (OK), 404 (Not Found), 500 (Internal Server Error), etc.
- **HATEOAS (Hypertext As The Engine Of Application State):** Isso significa que as respostas da API devem conter links para recursos relacionados, permitindo a navegação e a descoberta da API de forma mais dinâmica.


***
### Exercícios 
* [Exercicio para sala](/exercicios/para-sala/)
* [Exercicio para casa](/exercicios/para-casa/)

### Material da aula 
* [Material](/material)

### Links Úteis
* 

<p align="center">
Desenvolvido com :purple_heart:  
</p>


# Uma introdução a JavaScript

Vejamos o que há de tão especial sobre JavaScript, o que é possível de se fazer com a linguagem, bem como outras tecnologias com ela compatíveis.

## O que é JavaScript?

*JavaScript* foi criada para *"trazer vida às páginas web"*.

Os programas nessa linguagem são chamados de *scripts*. Eles podem ser inseridos diretamente no HTML de uma página web e são executados automaticamente quando a mesma é carregada.

Os scripts são carregados e executados como texto puro. Não há qualquer preparação ou compilação feita para que sejam rodados.

Nesse aspecto, JavaScript é bem diferente de uma outra linguagem, chamada [Java](https://pt.wikipedia.org/wiki/Java_(linguagem_de_programa%C3%A7%C3%A3o)).

```smart header="Por que é chamada <u>Java</u>Script?"
Quando foi criada, JavaScript tinha um outro nome: "LiveScript". Mas Java era uma linguagem muito popular na época, e decidiu-se que posicionar essa nova tecnologia como uma "irmã mais nova" de Java seria uma boa estratégia.

Com o seu desenvolvimento, JavaScript se tornou uma linguagem totalmente independente, com uma especificação própria denominada [ECMAScript](http://en.wikipedia.org/wiki/ECMAScript), não tendo atualmente nenhuma relação com Java.
```

Hoje em dia, JavaScript pode ser executada não somente em navegadores, mas também em servidores, ou mesmo em qualquer dispositivo que rode o [motor JavaScript](https://en.wikipedia.org/wiki/JavaScript_engine).

Navegadores têm um interpretador embutido, às vezes chamado de "máquina virtual JavaScript".

Interpretadores diferentes têm diferentes "codinomes". Por exemplo:

- [V8](https://en.wikipedia.org/wiki/V8_(JavaScript_engine)) -- no Chrome e no Opera.
- [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey) -- no Firefox.
- ...Existem outros codinomes, como "Trident" e "Chakra", para versões diversas do IE, "ChakraCore" para o Microsoft Edge, "Nitro" e "SquirrelFish" para o Safari, etc.

Lembre-se das expressões acima, pois elas são muito usadas em artigos de desenvolvedores na internet. Nós as usaremos também. Por exemplo, se "V8 oferece suporte ao recurso X", então esse recurso provavelmente funciona no Chrome e no Opera.

```smart header="Como funcionam os motores?"

Motores são complicados, mas seu funcionamento básico é simples.

1. O motor (embutido se no navegador) lê ("analisa") o script;
2. Então, converte ("compila") o script para linguagem de máquina;
3. Finalmente, o código de máquina é executado, muito rapidamente.

O motor otimiza o código a cada etapa do processo. Ele até mesmo monitora o script compilado em tempo de execução, analisa os dados que estão sendo processados, e otimiza o código de máquina, agora baseado nessas informações.
```

## O que pode fazer o JavaScript do navegador?

JavaScript moderno é uma linguagem de programação "segura". Ela não proporciona acesso de baixo nível à memória ou à CPU, pois foi criada inicialmente para navegadores, que não precisavam desses recursos.

Os recursos de JavaScript dependem bastante do tipo de ambiente em que a linguagem está sendo executada. Por exemplo, [Node.js](https://pt.wikipedia.org/wiki/Node.js) dá suporte a funções que permitem ao JavaScript ler/escrever arquivos, fazer requisições de rede, etc.

JavaScript no navegador faz qualquer coisa relacionada a manipulação de páginas web, interação com o usuário e com o servidor web.

Por exemplo, JavaScript no navegador pode:

- Adicionar elementos HTML à página, modificar conteúdo existente, alterar estilos;
- Reaje a ações do usuário, cliques e movimentos do mouse, pressionar de teclas;
- Envia requisições de rede para servidores remotos, faz o download e o upload de arquivos (as conhecidas tecnologias [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming)) e [COMET](https://en.wikipedia.org/wiki/Comet_(programming))).
- Ativar ou desativar cookies, fazer perguntas ao visitante, exibir mensagens;
- Persistir dados client-side ("armazenamento local").

## O que JavaScript no navegador NÃO PODE fazer?

Os recursos de JavaScript no navegador são limitados em prol da segurança do usuário. O objetivo é prevenir páginas maliciosas de acessar informações privadas ou afetar os dados do usuário.

São exemplos dessas restrições:

- JavaScript em uma página we não consegue acessar arquivos arbitrários no disco rígido, tampouco alterá-los, copiá-los, ou executar programas. Não há acesso direto a funções do sistema operacional.

    Navegadores modernos permitem o trabalho com arquivos, mas o acesso a eles é limitado e somente permitido após uma ação do usuário, como "arrastar" para a janela do navegador um arquivo, ou acessá-lo por meio da tag `<input>`.

    Há meios de acesso a câmeras, microfones e outros dispositivos, mas que requerem permissão explícita do usuário. Uma página com JavaScript habilitado não tem como acessar sorrateiramente a câmera web, observar o ambiente e enviar as informações para a [NSA](https://en.wikipedia.org/wiki/National_Security_Agency).

- Abas/janelas diferentes normalmente não têm conhecimento umas sobre as outras, o que é possível, às vezes, quando uma janela usa JavaScript para abrir outra. Mesmo nesse caso, entretanto, o JavaScript de uma página não pode acessar outra, se ambas provêm de diferentes websites (de diferentes domínios, diferente protocolo ou acessadas por portas diferentes).

    Essa é a chamada "Política de Mesma Origem". Para que ela não seja aplicada, *ambas páginas* devem concordar com a troca de dados e conter código JavaScript especial para lidar com isso. Essa técnica será abordada neste tutorial.

    Essa limitação existe, de novo, para a segurança do usuário. Uma página de `http://sitequalquer.com` aberta pelo usuário não pode ser capaz de acessar outra aba, com a URL `http://gmail.com` e roubar informações a partir dali.
- JavaScript pode se comunicar com o servidor de onde partiu a página atual com facilidade. Mas, é bastante limitada para receber dados a partir de outros sites/domínios. Ainda que possível, isso requer uma permissão expressa (contida em cabeçalhos HTTP) vinda do lado remoto. De novo, uma limitação de segurança.

![](limitations.svg)

Esse limites não existem quando JavaScript é usada fora do ambiente do navegador, por exemplo, num servidor. Além disso, navegadores modernos permitem que plugins/extensões requeiram permissões extendidas.

## What makes JavaScript unique?

There are at least *three* great things about JavaScript:

```compare
+ Full integration with HTML/CSS.
+ Simple things are done simply.
+ Support by all major browsers and enabled by default.
```
JavaScript is the only browser technology that combines these three things.

That's what makes JavaScript unique. That's why it's the most widespread tool for creating browser interfaces.

That said, JavaScript also allows to create servers, mobile applications, etc.

## Languages "over" JavaScript

The syntax of JavaScript does not suit everyone's needs. Different people want different features.

That's to be expected, because projects and requirements are different for everyone.

So recently a plethora of new languages appeared, which are *transpiled* (converted) to JavaScript before they run in the browser.

Modern tools make the transpilation very fast and transparent, actually allowing developers to code in another language and auto-converting it "under the hood".

Examples of such languages:

- [CoffeeScript](http://coffeescript.org/) is a "syntactic sugar" for JavaScript. It introduces shorter syntax, allowing us to write clearer and more precise code. Usually, Ruby devs like it.
- [TypeScript](http://www.typescriptlang.org/) is concentrated on adding "strict data typing" to simplify the development and support of complex systems. It is developed by Microsoft.
- [Flow](http://flow.org/) also adds data typing, but in a different way. Developed by Facebook.
- [Dart](https://www.dartlang.org/) is a standalone language that has its own engine that runs in non-browser environments (like mobile apps), but also can be transpiled to JavaScript. Developed by Google.

There are more. Of course, even if we use one of transpiled languages, we should also know JavaScript to really understand what we're doing.

## Summary

- JavaScript was initially created as a browser-only language, but is now used in many other environments as well.
- Today, JavaScript has a unique position as the most widely-adopted browser language with full integration with HTML/CSS.
- There are many languages that get "transpiled" to JavaScript and provide certain features. It is recommended to take a look at them, at least briefly, after mastering JavaScript.

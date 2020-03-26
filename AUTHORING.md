
# Autoria

Aqui estão detalhadas informações importantes sobre a confecção de novos artigos para o tutorial.

## Links internos

Todos os links do tutorial deverão ser escritos a partir do diretório raiz, sem a inclusão do domínio.

✅ OK:

```md
Nós abordaremos esse assunto no capítulo [sobre funções](/function-basics)
```

❌ Not ok:

```md
Nós abordaremos esse assunto no capítulo [sobre funções](https://javascript.info/function-basics)
```

Além disso, para se referir a um capítulo, há uma notação especial "info:", que funciona assim:

```md
Nós abordaremos esse assunto no capítulo <info:function-basics>.
```

Torna-se:
```html
Nós abordaremos esse assunto no capítulo <a href="/function-basics">Básico sobre Funções</a>.
```

O título é inserido automaticamente a partir do artigo referido. Isso tem a vantagem de manter o título correto caso o artigo seja renomeado.

## TODO

Contate @iliakan para mais detalhes.

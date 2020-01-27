# Links e referências
[Protótipo de tela](https://xd.adobe.com/view/4cf9fca3-b3a6-47a5-95e6-8dc246a1702b-19aa)
[Framework utilizada](https://vuetifyjs.com/pt-BR)

# Notas de desenvolvimento da aplicação
Eu desenvolvi essa aplicação como um teste técnico para a empresa UOL EdTech, onde o intuito seria desenvolver um painel de exibição de cursos.

## Pontos notáveis
Fiz algumas adaptações ao layout para manter o padrão de design do [Material Design](https://material.io/design), o qual é utilizado pela framework do [Vuetify](https://vuetifyjs.com/pt-BR).

## Pontos de Melhoria do desenvolvimento
A utilização dos serviços aws ou google cloud seria essencial para visualizar o funcionamento online da aplicação.

No desenvolvimento do modal da coluna "Edição e Conteúdo", eu enfrentei um problema de tamanho máximo da pilha de chamadas excedido, algo estava realizando um looping infinito em um certo ponto da experiência no qual eu não consegui identificar, sendo assim, deixei essa parte do código comentada e o botão estático. 

![working](https://snipboard.io/gB6tCX.jpg)
![error](https://snipboard.io/FapJMA.jpg)

## Configuração de projeto
```
npm install
```

### Compila e habilita o hot-reload para desenvolvimento/testes
```
npm run serve
```

### Compila e minifica os arquivos para produção
```
npm run build
```

### Executa o Linter e formata o texto
```
npm run lint
```

### Configuração de referência
[Configuration Reference](https://cli.vuejs.org/config/).

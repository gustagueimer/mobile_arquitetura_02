# Aula 02 - Atividade 04B: Evolução da aplicação que exibe produtos providos de uma API

Uma aplicação desenvolvida seguindo os padrões do MVVM, separando o código em diferentes áreas de acordo com seu propósito.
A Evolução consiste em adicionar um sistema de cache para ser utilizado quando a API estiver indisponível e implementar uma classe de falha para tratar erros

## Little Questions
**1. Em qual camada foi implementado o mecanismo de cache? Explique por que essa decisão é adequada dentro da arquitetura proposta.** <br>
*O mecanismo de cache foi implementado na camada de datasource, pois é uma fonte de dados que o reopsitory vai utilizar.*

**2. Por que o ViewModel não deve realizar chamadas HTTP diretamente?** <br>
*No MVVM, o papel do viewmodel é apenas ser a ponte lógica entre a UI e o repository, chamadas HTTP devem ser apenas feitas nos datasources que o repository utilizará.*
   
**3. O que poderia acontecer se a interface acessasse diretamente o DataSource?** <br>
*A Interface inteira poderia quebrar caso houvesse alguma divergencia com o retorno da API, como uma indisponibilidade ou algum atributo adiconal fora do definido na interface*

**4. Como essa arquitetura facilitaria a substituição da API por um banco de dados local?** <br>
*Seguindo o MVVM, trocar a fonte de dados da API por um banco local seria fácil como apenas remover o datasource remoto e implementar um datasource local fazendo interface com o banco de dados*

## Estrutura autal do código do projeto:

```
/lib 
|
|_/core
| |
| |_/errors
| |
| |_/network
|
|_/features
  |
  |_/product
    |
    |_/data
    | |
    | |_/datasources
    | |
    | |_/models
    | |
    | |_/repositories
    |
    |_/domain
    | |
    | |_/entities
    | |
    | |_/repositories
    |
    |_/presentation
      |
      |_/pages
      |
      |_/viewmodels
```

## Como Rodar

### Requisitos 
`` Flutter 3.35.3 `` <br>
`` Dart 3.9.2 `` <br>

Clone este repositório em um folder de seu dispositivo seguindo os segiuntes passosem um terminal: <br>
```
git clone https://github.com/gustagueimer/mobile_arquitetura_01  
``` 
entre na pasta pelo terminal com: 
```
cd mobile_arquitetura_01
```
resolva as dependências com:
```
flutter pub get
```
e inicie a applicação com:
```
flutter run -d edge --web-browser-flag="--disable-web-security"
```
assim que a aplicação terminar de carregar no navegador, aperte no botão flutuante no canto inferior esquerdo e os produtos da API devem ser carregados na tela.
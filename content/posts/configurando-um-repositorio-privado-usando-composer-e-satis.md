---
title: "Configurando um repositório privado usando Composer e Satis"
date: "2015-06-21"
tags:
  - "php"
  - "composer"
  - "satis"
---

Recentemente eu precisei incluir um repositório do Git cujo acesso é privado em um projeto que estou trabalhando
na [Coderockr](http://coderockr.com) e este repositório deveria ser importado no projeto por meio do composer, talvez
isso não seja novidade para você, mas, para mim é pelo fato de eu nunca ter precisado criar um ambiente acessível
pelo [composer](https://getcomposer.org) que utilizasse um repositório git privado.

#### Como faz?

Após algumas pesquisas eu encontrei o projeto [Satis](https://github.com/composer/satis), que pelo que pude compreender
é mantido pelos mesmos desenvolvedores que mantém o composer.

O uso dele é bem simples e eu tentarei descrever os passos de uma forma bem simples e objetiva:

#### Instale o Composer

Se ainda não o tiver feito, [(aprenda como)](https://getcomposer.org/doc/00-intro.md).

#### Instale o Satis

Crie um projeto usando o composer, basta rodar o seguinte comando no terminal:

```bash
php composer.phar create-project composer/satis --stability=dev --keep-vcs
```
#### Configure-o para prover o acesso ao seu repositório privado

A primeira coisa que deve ser feita é criar um arquivo chamado satis.json no  
root do projeto que foi criado acima, segue um exemplo deste arquivo:

```json
{  
    "name": "Repositório Local",  
    "homepage": "http://localhost:8888",  
    "archive": {  
            "skip-dev": true  
    },  
    "repositories": [  
        { "type": "vcs", "url": "https://url-para-seu-repositorio-git/nome-do-seu-repositorio.git" }  
    ],  
    "require": {  
        "seu-pacote/sua-lib": "\*"  
    }  
}
```
Como pode ser observado acima, eu configuro com o repositório que eu quero disponibilizar, se precisar colocar mais do
que um repositório basta adicionar outro elemento no array _repositories_.

Em seguida, informe o nome do seu pacote/library e qual versão deseja usar.

Acima, no atributo homepage é informado qual o endereço local que será usado para servir o projeto. Você pode usar uma
URL diferente de localhost sem problemas.

#### Faça a _build_ do seu repositório

Execute o comando abaixo sempre que houver mudanças no seu repositório:

```bash
php bin/satis build <configuration file> <build dir>
```
Por exemplo, eu rodei assim:

```bash
php bin/satis build satis.json repo
```
O diretório repo será usado para disponibilizar os fontes do repositório privado.

#### Disponibilize o repositório

Você pode criar um virtual host apontando para o diretório _repo_, mas dependendo do caso, usar o webserver embutido no
CLI do PHP:

```bash
php -S 0.0.0.0:8888 -t repo
```
Após rodar o comando acima (ou configurar um virtual host), acesse: [**http://localhost:8888**](http://localhost:8888)

Se for mostrada uma tela com os repositórios que você configurou eles poderão ser usados adicionando no composer.json do
seu projeto:
```json
"repositories": [  
    {  
      "type": "composer",  
      "url": "http://localhost:8888"  
    }  
  ],  
  "require": {  
    "seu-pacote/sua-lib": "dev-master"  
  }
```

#### Conclusão

Existem muitas outras configurações que podem ser feitas, mas essa configuração básica já ajuda na maioria das
situações.

Você conhece alguma outra maneira de lidar com uma situação como essa? Deixe seu comentário.

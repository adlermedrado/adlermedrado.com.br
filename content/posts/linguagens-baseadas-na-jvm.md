---
title: "Linguagens baseadas na JVM"
date: "2015-10-11"
tags:
  - "clojure"
  - "java"
  - "jruby"
  - "jvm"
  - "nashorn"
---

Apesar de existirem muitas críticas à linguagem Java, é um fato que a JVM (Java Virtual Machine) é uma obra-prima.

Muitas pessoas confundem a Java Virtual Machine com a linguagem Java e tratam tudo como se fosse uma coisa só, esse é o
tipo de ignorância que infelizmente é muito difundida por aí. Uma coisa é a linguagem Java ter suas deficiências (como
qualquer outra linguagem tem) e receber críticas por isso e outra coisa é a plataforma e ecossistema Java.

Basicamente é o seguinte:

- Java é a linguagem de programação;
- JVM é a máquina virtual que interpreta os bytecodes gerados pelo compilador Java, ela foi criada inicialmente para
  interpretar programas Java permitindo que programas compilados em uma plataforma pudessem ser executado em outra,
  dando origem ao lema: “Write once, run anywhere”;

Eu particularmente gosto muito da plataforma Java, inclusive da linguagem, no entanto o que me fascina mesmo é a JVM que
proporciona muitas possibilidades com a implementação de especificações de outras linguagens permitindo que estas
funcionem em cima da JVM tirando proveito assim da portabilidade, velocidade e segurança já existentes nela, sem falar
de linguagens totalmente novas.

Seguem abaixo algumas linguagens e implementações de linguagens já existentes para JVM:

- [Quercus](http://quercus.caucho.com) (PHP)
- [jRuby](http://jruby.org) (Ruby)
- [Nashorn](http://openjdk.java.net/projects/nashorn/) (Javascript)
- [Clojure](http://clojure.org)
- [Scala](http://www.scala-lang.org)
- [Groovy](http://www.groovy-lang.org)
- [Jython](https://wiki.python.org/jython/) (Python)

Existem muitas outras, [veja nesta lista da Wikipedia](https://en.wikipedia.org/wiki/List_of_JVM_languages).

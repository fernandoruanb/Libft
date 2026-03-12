# 📚 Libft — My First Custom C Library

![Library](https://cdn.pixabay.com/photo/2017/08/06/22/01/library-2596809_1280.jpg)

## 📖 About the Project

A **Libft** é o primeiro grande projeto que desenvolvi durante minha experiência na **École 42**.

O objetivo principal desse projeto é ensinar um princípio fundamental da programação: **não depender exclusivamente de funções prontas**, mas sim compreender profundamente como elas funcionam e ser capaz de implementá-las por conta própria.

Durante nossa jornada como estudantes de programação, frequentemente encontramos limitações — seja por não podermos usar determinadas funções da biblioteca padrão ou por percebermos que certas ferramentas que gostaríamos de utilizar simplesmente não existem ainda.

A **Libft** surge justamente como uma solução para isso.

Ela representa o **primeiro passo rumo à liberdade do programador**: construir nossa própria biblioteca de funções, totalmente compreendida, validada e testada por nós mesmos.

Com o tempo, essa biblioteca se torna uma **base pessoal reutilizável**, capaz de acelerar o desenvolvimento de novos projetos.

---

## ⚙️ Build System — Makefile

Para organizar e compilar todas essas funções, utilizamos um arquivo de configuração chamado **Makefile**.

O **Makefile** é responsável por:

* definir **como o código será compilado**
* organizar os arquivos do projeto
* automatizar o processo de build
* gerar o arquivo final da biblioteca

No projeto **Libft**, utilizamos esse sistema para gerar uma **biblioteca estática**.

Uma biblioteca estática é um conjunto de funções compiladas que **não fazem parte das bibliotecas padrão do sistema**, mas que podem ser **incluídas manualmente durante a compilação de outros programas**.

Isso permite reutilizar nossas funções em qualquer projeto futuro em C.

---

## 🎯 Main Objective

O projeto Libft permite desenvolver habilidades essenciais como:

* compreensão profunda das funções da libc
* manipulação de memória
* manipulação de strings
* criação de bibliotecas reutilizáveis
* organização de projetos em C
* automação de build com Makefile

---

## 🧠 Example Functions

Como demonstração do que foi desenvolvido na **Libft**, abaixo explico algumas funções e o que aprendi ao implementá-las.

### 🔢 `ft_atoi`

A primeira função que gostaria de mencionar é a **`ft_atoi`**.

Antes de tudo, vale explicar o prefixo **`ft`**, que significa **"forty-two"**. Todas as funções implementadas pelos estudantes da École 42 utilizam esse prefixo para evitar conflitos com as funções originais da biblioteca padrão da linguagem C.

A função **`atoi`** é responsável por converter uma **string em um número inteiro**.

Por exemplo:

```
"++++++42asdfjafs"
```

é convertido para:

```
42
```

Isso é extremamente útil para entendermos **como tratar dados recebidos em formato textual** e convertê-los para valores numéricos utilizáveis em programas.

Durante essa implementação, também aprendemos sobre **overflow de inteiros**.

Por exemplo, em um `signed int`, o valor máximo possível é:

```
2147483647
```

Isso ocorre porque um inteiro de **32 bits** possui:

* **1 bit reservado para o sinal**
* **31 bits para representar o valor**

O que resulta em:

```
2³¹ − 1 = 2147483647
```

Quando um valor maior que esse é passado para a função, ocorre **overflow**, o que gera resultados inesperados.

No exercício da **Libft**, implementamos uma versão própria da função apenas para **entender profundamente seu funcionamento interno**. Posteriormente, podemos adaptá-la conforme as necessidades de nossos próprios projetos.

---

### 🧵 Manipulação de Strings e Memória

Outro ponto importante do projeto foi a criação de funções que lidam com **alocação dinâmica de memória**.

Entre elas:

* `ft_strjoin`
* `ft_split`

A função **`ft_strjoin`** permite unir duas strings em uma nova string alocada dinamicamente.

Já **`ft_split`** permite dividir uma string em várias substrings com base em um delimitador, algo extremamente útil em parsing de dados.

Também implementamos funções como:

```
ft_strlcpy
```

Essa função retorna o **tamanho total que a string teria**, mesmo quando o buffer de destino não é grande o suficiente.

Isso é muito útil porque permite calcular **exatamente quanto espaço precisamos alocar na heap** para realizar operações seguras de cópia de strings.

Durante esse processo, aprendemos uma lição fundamental da programação em C:

> Tudo o que é alocado na memória deve ser liberado pelo programador.

Ou seja:

```
malloc → precisa de free
```

Caso contrário, ocorrerão **memory leaks**, algo que é **rigorosamente avaliado durante os projetos da 42**.

---

### ⚡ `memcpy` vs `memmove`

Outro aprendizado importante envolve a manipulação direta de memória.

Funções como:

```
memcpy
memmove
```

parecem semelhantes, mas possuem uma diferença crucial.

Se utilizarmos **`memcpy`** para copiar regiões de memória que **se sobrepõem**, podemos perder dados durante a operação.

Já **`memmove`** resolve esse problema copiando os dados **de trás para frente**, garantindo que os bytes originais não sejam sobrescritos antes da cópia terminar.

Esse tipo de detalhe é fundamental para entender **como a memória realmente funciona em baixo nível**.

---

### 🔗 Linked Lists (Bonus Part)

Na parte **bonus da Libft**, aprendemos a trabalhar com **listas ligadas (linked lists)** utilizando **structs em C**.

Implementamos funções capazes de:

* criar um novo nó (`ft_lstnew`)
* adicionar elementos na lista (`ft_lstadd_front`, `ft_lstadd_back`)
* calcular o tamanho da lista (`ft_lstsize`)
* percorrer a lista
* deletar nós (`ft_lstdelone`)
* limpar toda a lista (`ft_lstclear`)

Esse conhecimento foi extremamente útil em projetos posteriores da 42, como o **so_long**, onde estruturas de dados dinâmicas se tornam muito importantes para organizar informações complexas.

---


### 📊 Function Table

| Function   | Description                       |
| ---------- | --------------------------------- |
| ft_atoi    | Converts a string to an integer   |
| ft_split   | Splits a string using a delimiter |
| ft_strjoin | Concatenates two strings          |
| ft_memcpy  | Copies memory area                |
| ft_memmove | Safe memory copy with overlap     |

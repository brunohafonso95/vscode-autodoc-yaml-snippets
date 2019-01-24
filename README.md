# Autodoc Yaml Snippets (Visual Studio Code)
---

Essa extensão tem como objetivo faciliar a utilização da ferramenta de CLI **Autodoc Yaml**, que foi criado com intuito de facilitar o processo de documentação de software, onde o usuário apenas necessita seguir um padrão de comentários com algumas anotações (labels) utilizando a sintaxe de arquivosyaml para que a documentação seja gerada de forma automatica, é uma ferramenta de linha de comando que funciona com projetos construídos em **python**, **java**, **yaml**, **javascript** e **typescript**.

### Instalação do Autodoc Yaml
---

Para realizar a instalação do pacote é necessário ter o versão 8.+ do node.js, caso já possua o mesmo instalado em sua máquina, executar o seguinte comando:


```javascript
npm i -g autodoc_yaml
```

após finalizar o download do pacote, abrir os arquivos que devem ser documentados e comentar as classes e métodos seguindo o seguinte padrão:


```java
/// - Annotation:
///     title: comandosBasicos
///     text_description:
///	   - Método construtor da classe.
///     parameters:
///	   - WebDriver: driver
///     ex:
///     - language: java
/// 	   - WebDriver driver = new WebDriver();
///	   - ComandosBasicos comBasico = new ComandosBasicos(driver);
///     return: void
```

Os blocos de documentação devem conter no inicio de cada linha a  3 barras (///) caso a linguagem utilizada tenha o padrão de comentário usando barra, caso contrátio utilizar 3 cerquilhas (###), que é o simbolo usado para comentários em outras linguagens como python.Além disso é possível também gerar a documentação fazendo as anotações direto em arquivos yaml, na pasta yamlFIles.


Obs: se for necessário utilizar o simbolo de dois pontos ( : ) ou 2 asteriscos ( ** ) no texto, o mesmo deve ficar entre aspas duplas para que seja tratado de forma literal.A label Annotation deve conter a seguinte estrutura ( - Annotation), pois cada uma representa um bloco diferente de documentação,além disso apenas é o único label que é obrigatório os demais podem ser incluidos de acordo com a necessidade e caso seja necessário usar mais de uma anotação num mesmo bloco, será preciso separar os labels repetidas por uma label annotation o nome do mesmo incluindo um número no finalizar como no exemplo abaixo:


```java
/// - Annotation:
///     title: comandosBasicos
///     text_description:
///	    - Método construtor da classe.
///     parameters:
///	    - WebDriver: driver
/// - Annotation:
///     text_description:
///	    - segunda anotação de text_description.
///     ex:
/// 	    - WebDriver driver = new WebDriver();
///	    - ComandosBasicos comBasico = new ComandosBasicos(driver);
///     return: void
```

### Descrição das labels de um bloco de documentação 
---

**Annotation**

Label obrigatória em todo o bloco de documentação, ela serve para delimitar o inicio de um novo bloco, e a mesma deve a seguinte estrutura:


```java
/// - Annotation:
///    demais label...
```

**mainTitle**

Label que cria um título principal no bloco, tem a seguinte sintaxe:


```java
/// - Annotation:
///     mainTitle: comando exemplo mainTitle
```

**title**

Label que cria um título principal secundário no bloco, tem a seguinte sintaxe:


```java
/// - Annotation:
///     title: comando exemplo title
```

**text_description**

Label que cria um paragrafo no bloco, no inicio de cada linha de cada linha deve ser inserida com o caractere traço ( - ) no inicio e incluir as labels paragraph para definir os paragrafos como o exemplo abaixo:


```java
/// - Annotation:
///     text_description:
///     - paragraph:
///	       - primeira linha do paragrafo.
///	       - segunda linha do paragrafo.
///	       - terceira linha do paragrafo.
///     - paragraph:
///	       - primeira linha do paragrafo.
///	       - segunda linha do paragrafo.
///	       - terceira linha do paragrafo.
```

**parameters**

Label que cria um ou mais parêmetros para auxiliar na descrição de um método ou função, cada parâmetro deve ser inserido em uma linha com o caractere traço ( - ) no inicio como o exemplo abaixo:


```java
/// - Annotation:
///     parameters:
///	    - tipoDoParametro: nomeDoParametro
///	    - tipoDoParametro2: nomeDoParametro2
```

**ex**

Label que cria um bloco de exemplo de código para auxiliar na descrição de um método ou função, no inicio de cada linha deve ser inserido com o caractere traço ( - ) seguido do nome da linguagem e dois pontos ( : ) no inicio como o exemplo abaixo:


```java
/// - Annotation:
///     ex:
/// 	    - language: nome da linguagem;
///	    - linha de script;
///	    - linha de script;
///	    - linha de script;
```

**exception**

Label que cria um bloco de paragrafo de descrição de uma exception como o exemplo abaixo:


```java
/// - Annotation:
///     exception: descrição da excepetion
```

**return**

Label que cria a descrição do retorno de um método ou função como o exemplo abaixo:


```java
/// - Annotation:
///     return:
///        - tipoRetorno: descrição do retorno
///        - tipoRetorno: descrição do retorno
```

**image**

Label que cria uma imagem deve receber o altText que será o título da imagem e o texto de acessibilidade caso o link da imagem esteja quebrado e o nome da mesma junto com a extensão como o exemplo abaixo:


```java
/// - Annotation:
///     image:
///     - imageLink: avatar.png
///     - altText: DevOps Logo
```

**unorderedList**

Label que cria uma lista inordenada cada item deve ser inserido em uma linha com o caractere traço ( - ) no inicio como o exemplo abaixo:


```java
/// - Annotation:
///     unorderedList:
///        - item 1
///        - item 2
///        - item 3
```

**orderedList**

Label que cria uma lista ordenada cada item deve ser inserido em uma linha com o caractere traço ( - ) no inicio como o exemplo abaixo:


```java
/// - Annotation:
///     orderedList:
///        - item 1
///        - item 2
///        - item 3
```

**link**

Label que cria uma lista ordenada cada item deve ser inserido em uma linha com o caractere traço ( - ) no inicio como o exemplo abaixo:


```java
/// - Annotation:
///     link:
///        - linkText: link do google
///        - linkUrl: http://google.com
```

**logo**

Label que insere um logo no topo e no rodapé dos pdf's gerados, é necessário que o logo esteja na raiz do projeto e essa anotação deve ir no inicio da documentação (na anotação que fica no inicio do pdf) e deve ser implementada da seguinte forma:


```java
/// - Annotation:
///     logo:
```

### Exemplo de uso em um arquivo java 
---

```java
/// - Annotation:
///     mainTitle: exemplo
///     text_description:
///         - paragraph:
///	           - Classe de exemplo.
public class exemplo {
/// - Annotation:
///     title: exemplo
///     text_description:
///         - paragraph:
///	            - Método de teste
///     parameters:
///	       - String: teste
///     ex:
///         - language: java
///         - exemplo('texto');
///     return:
///	     - void: método não tem retorno
   public void exemplo(String teste) {
	    this.teste = teste;
   }
}
```

### Exemplo de uso em um arquivo python 
---

```python
### - Annotation:
###     mainTitle: exemplo
###     text_description:
###	       - paragraph:
###	           - Classe de exemplo.
class exemplo(object):
### - Annotation:
###     title: exemplo
###     text_description:
###	       - paragraph:
###	           - Método de teste
###     parameters:
###	       - string: teste
###     ex:
///         - language: python
### 	       - exemplo('texto')
###     return: método não tem retorno
     def exemplo(teste):
 	    self.teste = teste
```

### Command Line (CLI) 
---

No final depois de finalizar o processo de documentação, basta executar os comandos com os devidos parâmetros na raiz do projeto documentado para que a documentação seja gerada.


- **autodoc --help**: para obter a descrição de todos os parâmetros e opções disponiveis no CLI.
- **autodoc -V, --version**:          para saber a versão do autodoc.
- **autodoc -l --language [value]**:  passando a linguagem dos arquivos documentados como parâmetro para que a documentação seja gerada.
As opções de linguagem disponíveis são as seguintes:


1. javascript
2. typescript
3. java
4. python
5. yaml
O processo será iniciado e documentação será gerada coso toda as estruturaesteja correta é só acessar a pasta documentation e visualizar os arquivos gerados


### Observações finais 
---

A lib irá criar na raiz do projeto uma pasta **documentation** contendo as seguintes pastas:


- confluenceFiles
- images
- yamlFiles
- jsonFiles
- mdFiles
- pdfFiles


os arquivos de documentação gerados serão armazenados nas pastas citadas anteriormente, além disso os arquivos md podem ser visualizados através de um algum software de preview no no vscode, basta instalar um plugin, ou, então abrir os pdf's exportados na documentação na pasta pdfFiles.

PS: os arquivos exportados na pasta confluenceFiles são gerados no padrão do confluence, e podem ser usados para publicação da documentação sem a necessidade de adaptação.
# Engenharia de Software Moderna  
**Autor:** Marco Tulio Valente  
**Capítulo 9: Refactoring**

---

## **Entendimento do Capítulo**

O capítulo 9 do livro "Engenharia de Software Moderna" aborda o conceito de **refactoring**, definido como modificações realizadas no código para melhorar sua manutenibilidade sem alterar seu comportamento. O objetivo principal é facilitar a compreensão e evolução futura do sistema.

O autor apresenta os principais refactorings descritos por Martin Fowler, como:
- **Extração de Método**: Dividir métodos grandes em partes menores e mais legíveis.
- **Inline de Método**: Incorporar métodos pequenos diretamente nos pontos de chamada.
- **Movimentação de Método**: Mover métodos para classes onde eles façam mais sentido.
- **Extração de Classes**: Criar novas classes a partir de classes com muitas responsabilidades.
- **Renomeação**: Dar nomes mais claros e significativos a variáveis, métodos ou classes.

Além disso, o capítulo discute a importância de uma boa suíte de testes para garantir que o comportamento do sistema seja preservado durante as refatorações. Também são apresentados **code smells**, que são indicadores de código de baixa qualidade, como:
- Código duplicado.
- Métodos longos.
- Classes grandes.
- Variáveis globais.
- Objetos mutáveis.

Uma citação marcante é de Kent Beck:  
*"I'm not a great programmer; I'm just a good programmer with great habits."*  
Isso reforça que boas práticas, como refactoring, são essenciais para manter a saúde de um sistema ao longo do tempo.

No meu estágio em desenvolvimento iOS, percebo que o refactoring é uma prática indispensável para manter o código limpo e fácil de entender, especialmente em projetos que crescem rapidamente ou passam por mudanças frequentes.

---

## **Aplicação no Mercado**

Os conceitos apresentados no capítulo são extremamente aplicáveis ao desenvolvimento de aplicativos iOS. Vou destacar alguns pontos e como eles se relacionam com minha experiência prática:

### 1. **Extração de Método**
Esse refactoring é essencial para dividir métodos grandes em partes menores e mais específicas. No desenvolvimento iOS, isso ajuda a evitar controladores sobrecarregados (o *Massive View Controller*). Por exemplo:
- Em uma tela de listagem de produtos, podemos extrair métodos para configurar a interface (`setupUI()`), carregar dados da API (`fetchProducts()`) e tratar interações do usuário (`handleUserActions()`).
- Isso torna o código mais modular e fácil de entender, além de facilitar a reutilização de métodos em outras partes do app.

---

### 2. **Renomeação**
Dar nomes claros e significativos a variáveis, métodos e classes é fundamental para a legibilidade do código. Já enfrentei situações em que nomes confusos dificultavam o entendimento do que determinada função fazia. Por exemplo:
- Renomear um método genérico como `doSomething()` para algo mais descritivo, como `validateUserInput()`, facilita a compreensão do código por outros desenvolvedores da equipe.

---

### 3. **Movimentação de Método**
Às vezes, métodos estão implementados na classe errada, o que aumenta o acoplamento entre componentes. No desenvolvimento iOS, isso pode ocorrer quando métodos relacionados à lógica de negócios estão no controlador em vez de estarem no ViewModel (no caso de MVVM). Por exemplo:
- Um método de formatação de preços pode ser movido do controlador para o ViewModel, melhorando a coesão e separação de responsabilidades.

---

### 4. **Code Smells**
Identificar e corrigir code smells é uma parte importante do refactoring. Alguns exemplos práticos no desenvolvimento iOS incluem:
- **Código Duplicado:** Ao implementar várias telas que compartilham elementos visuais semelhantes, como botões ou tabelas, criamos componentes reutilizáveis para evitar duplicação.
- **Métodos Longos:** Dividimos métodos extensos em funções menores e mais específicas, usando o refactoring de Extração de Método.
- **Classes Grandes:** Quando uma classe acumula muitas responsabilidades, usamos Extração de Classe para dividi-la em partes menores. Por exemplo, uma classe `OrderManager` pode ser dividida em `OrderValidator` e `OrderProcessor`.

---

### 5. **Refactorings Automatizados**
Ferramentas como o Xcode oferecem suporte para refactorings automatizados, como renomeação de métodos ou extração de variáveis. Isso reduz o risco de erros e acelera o processo de refatoração. Por exemplo:
- Recentemente, usei o recurso de renomeação automática do Xcode para atualizar o nome de um método em todo o projeto, garantindo consistência e economizando tempo.

---

## **Exemplos Práticos**

### **Exemplo 1: Extração de Método no Desenvolvimento iOS**
No capítulo, o autor menciona a Extração de Método como um dos refactorings mais importantes. No meu estágio, apliquei esse conceito ao refatorar um método extenso que configurava uma tabela:
- Antes do refactoring, o método fazia tudo: configurava células, lidava com eventos e formatava dados.
- Após o refactoring, criei métodos separados como `configureCell()`, `handleRowSelection()` e `formatDataForDisplay()`. Isso tornou o código mais organizado e fácil de testar.

---

### **Exemplo 2: Identificação e Correção de Code Smells**
Um exemplo prático seria identificar código duplicado em duas telas diferentes que exibiam listas de produtos. Ambas usam lógicas semelhantes para buscar dados da API e exibi-los. Para resolver isso:
- Criar uma classe utilitária `ProductService` que centraliza a lógica de busca de dados.
- Isso elima a duplicação e facilitou a manutenção, pois qualquer mudança na lógica agora precisa ser feita em apenas um lugar.

---

### **Exemplo 3: Movimentação de Método no Contexto de MVVM**
No capítulo, o autor explica que métodos devem estar nas classes corretas para melhorar a coesão. No meu estágio, identifiquei um método de validação de entrada de dados que estava no controlador (`ViewController`). Para corrigir:
- Movi o método para o ViewModel correspondente, tornando o controlador mais enxuto e respeitando o padrão MVVM.
- Isso também facilitou a criação de testes unitários para validar a funcionalidade.

---
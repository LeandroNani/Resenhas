# Engenharia de Software Moderna  
**Autor:** Marco Tulio Valente  
**Capítulo 7: Arquitetura**

---

## **Entendimento do Capítulo**

O capítulo 7 do livro "Engenharia de Software Moderna" aborda o conceito de arquitetura de software e sua importância no desenvolvimento de sistemas. A arquitetura é descrita como o projeto em um nível mais alto, focando na organização de componentes maiores, como módulos, camadas ou serviços, e nas decisões críticas que moldam o sistema.

O autor explora diversos padrões arquiteturais amplamente utilizados, incluindo:  
- **Arquitetura em Camadas** (com destaque para a Arquitetura em Três Camadas).  
- **Arquitetura MVC** (Model-View-Controller).  
- **Arquitetura baseada em Microsserviços**.  
- **Arquiteturas Orientadas a Mensagens**.  
- **Arquiteturas Publish/Subscribe**.  

Além disso, o capítulo discute outros padrões arquiteturais, como Pipes & Filtros, Cliente/Servidor e Peer-to-Peer, bem como apresenta o anti-padrão "Big Ball of Mud", que descreve sistemas sem uma arquitetura definida, resultando em dificuldades de manutenção.

Uma citação que chamou atenção foi a definição:
*"Architecture is about the important stuff. Whatever that is."*  
Isso reforça que a arquitetura está diretamente ligada às decisões mais relevantes e difíceis de reverter em um sistema.

No meu estágio , percebo que as escolhas arquiteturais têm impacto direto na escalabilidade, manutenção e testabilidade dos aplicativos.

---

## **Aplicação no Mercado (e no meu estágio)**

Os conceitos apresentados no capítulo são extremamente aplicáveis ao desenvolvimento de aplicativos iOS. Vou destacar alguns pontos e como eles se relacionam com minha experiência prática:

### 1. **Arquitetura em Camadas**
A arquitetura em camadas organiza o sistema em níveis hierárquicos, onde cada camada depende apenas da camada imediatamente inferior. No desenvolvimento iOS, isso é muito útil para estruturar o código de forma modular e organizada. Um exemplo seria dividir o app em:
- **Camada de Interface (UI):** Gerencia a interação com o usuário, utilizando frameworks como UIKit ou SwiftUI.
- **Camada de Lógica de Negócio:** Implementa as regras de negócio, como validações e cálculos.
- **Camada de Persistência:** Gerencia o armazenamento de dados, utilizando Core Data ou UserDefaults.

Essa separação facilita a manutenção e evolução do app. Por exemplo, ao mudar a interface de UIKit para SwiftUI, a lógica de negócio e a persistência permanecem intactas.

---

### 2. **Arquitetura MVVM**
Embora o capítulo foque bastante em MVC, no meu estágio utilizamos principalmente o padrão **MVVM (Model-View-ViewModel)**, que resolve algumas limitações do MVC, como o problema do *Massive View Controller*. O MVVM divide o sistema em três componentes principais:
- **Modelo (Model):** Representa os dados e a lógica de negócios.
- **Visão (View):** Responsável pela interface gráfica e exibição dos dados.
- **ViewModel:** Faz a ponte entre o modelo e a visão, transformando os dados para exibição e lidando com eventos gerados pela interface.

Por exemplo, ao implementar uma tela de listagem de produtos:
- O **Modelo** (`Product`) armazena os dados dos produtos.
- A **Visão** (`ProductListView`) exibe os produtos em uma `UICollectionView`.
- O **ViewModel** (`ProductListViewModel`) prepara os dados para exibição, formata preços e lida com interações do usuário, como cliques em itens.

Esse padrão reduz o acoplamento entre a interface e a lógica de negócios, tornando o código mais modular e fácil de testar.

---

### 3. **Microsserviços**
Embora microsserviços sejam mais comuns em back-end, o conceito de modularização também se aplica ao desenvolvimento iOS. Por exemplo:
- Dividimos o app em módulos independentes, como autenticação, pagamento e notificações.
- Cada módulo tem suas próprias responsabilidades e pode ser desenvolvido e testado separadamente.

Essa abordagem permite que diferentes equipes trabalhem simultaneamente em partes distintas do app, acelerando o desenvolvimento.

---

### 4. **Arquiteturas Orientadas a Mensagens**
Em apps iOS, utilizamos filas de mensagens para gerenciar tarefas assíncronas, como downloads ou sincronização de dados. Por exemplo:
- Usamos bibliotecas como Combine ou RxSwift para implementar comunicação assíncrona entre componentes.
- Isso garante que o app continue responsivo enquanto processa operações demoradas em segundo plano.

---

### 5. **Publish/Subscribe**
Esse padrão é útil para lidar com eventos no app. Em iOS, usamos frameworks como NotificationCenter ou Combine para implementar essa arquitetura. Por exemplo:
- Quando o usuário faz login, publicamos um evento usando `NotificationCenter`.
- Outras partes do app, como a tela inicial, assinam esse evento para atualizar os dados exibidos.

---

## **Exemplos Práticos**

### **Exemplo 1: Arquitetura em Três Camadas no Desenvolvimento iOS**
No capítulo, o autor menciona a arquitetura em três camadas como uma forma de organizar sistemas corporativos. No meu estágio, algo semelhante ocorre ao desenvolver uma funcionalidade como "exibir lista de produtos":
- **Camada de Interface:** Configuramos um `UICollectionView` para exibir os produtos.
- **Camada de Lógica de Negócio:** Criamos um `ProductListViewModel` para preparar os dados para exibição.
- **Camada de Persistência:** Utilizamos um serviço de API (`ProductService`) para buscar os dados do servidor.

Essa divisão torna o código mais modular e fácil de testar. Por exemplo, podemos testar o `ProductListViewModel` isoladamente, sem depender da interface ou da API.

---

### **Exemplo 2: Uso de MVVM no Desenvolvimento iOS**
No capítulo, o autor explica que o padrão MVC separa a lógica de negócios da interface. No entanto, no meu estágio, utilizamos **MVVM** para evitar controladores sobrecarregados. Um exemplo prático seria implementar uma tela de login:
- **Modelo:** Uma classe `User` que armazena as credenciais do usuário.
- **Visão:** Um formulário com campos de texto e botões, criado com SwiftUI.
- **ViewModel:** Uma classe `LoginViewModel` que valida os dados inseridos e chama o serviço de autenticação.

Essa separação facilita a manutenção, pois mudanças na interface não afetam a lógica de autenticação.

---

### **Exemplo 3: Publish/Subscribe com NotificationCenter**
No capítulo, o autor menciona o padrão Publish/Subscribe. Um exemplo prático no meu estágio seria implementar notificações internas no app:
- Quando o usuário adiciona um item ao carrinho, publicamos um evento usando `NotificationCenter`.
- Outras partes do app, como a barra de navegação, assinam esse evento para atualizar o número de itens no carrinho.

Essa abordagem desacopla os componentes, permitindo que cada um seja desenvolvido e testado de forma independente.

---
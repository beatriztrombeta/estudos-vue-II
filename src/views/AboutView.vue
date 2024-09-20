<template>
  <div class="about">
    <h1 class="text-3xl">Sobre</h1>
    <p>
      Esse mini projeto foi realizado com o intuito de estudar o framework Vue 3 e aplicar na
      prática os conceitos aprendidos durante as semanas de estudo. Através do desenvolvimento da
      lista de tarefas (to-do list), é possível consolidar conhecimentos fundamentais como o uso da
      Composition API, manipulação de estados reativos e comunicação entre componentes.
    </p>
    <p>
      Além disso, o projeto proporciona uma experiência realista no desenvolvimento de uma aplicação
      web com operações de CRUD, permitindo ao estudante explorar funcionalidades essenciais para
      qualquer aplicação moderna, como a adição, edição e exclusão de itens.
    </p>
    <p>
      O uso de `provide` e `inject` nesse contexto reforça a capacidade de gerenciar dependências e
      compartilhar lógica entre diferentes partes do aplicativo, facilitando o desenvolvimento de
      aplicações escaláveis e modulares no Vue.js 3.
    </p>
  </div>
</template>

<style>
.about {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  p {
    text-align: center;
    font-family: sans-serif;
    width: 40%;
    margin-top: 1rem;
  }
}
</style>

<template>
  <div
    :style="{
      'background-image': 'url(https://wallpapercave.com/wp/wp1834381.jpg',
    }"
  >
    <div>
      <h3>
        <label
          >Preencha o formularios algumas vezes para saber o que é o
          Flamengo</label
        >
      </h3>
    </div>

    <div>
      <label>Nome</label>

      <input v-model="formList.nome" placeholder="Digite o nome" />
    </div>

    <div>
      <label>Time</label>

      <input v-model="formList.time" placeholder="Digite o seu time" />
    </div>

    <div>
      <label>Sexo</label>

      <input v-model="formList.sexo" placeholder="Digite a o sexo" />
    </div>

    <div>
      <label>Idade</label>

      <input v-model="formList.idade" placeholder="Digite a o sexo" />
    </div>

    <button @click="addUser(formList.nome)">Cadastrar</button>

    <div v-for="(user, index) in users" :key="index">
      <p>Nome: {{ user.nome }}</p>

      <p>Time: {{ user.time }}</p>

      <p>Sexualidade: {{ user.sexo }}</p>

      <p>Idade: {{ user.idade }}</p>

      <button @click="removeUser(user.nome)">Delete</button>

      <button @click="editUser(user.nome)">Editar</button>

      <hr />
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";

const form = {
  nome: "",

  time: "",

  sexo: "",

  idade: "",
};

const users = ref<any>([]);

const formList = ref<any>({ ...form });

function addUser(nome: string) {
  const nomeExistente = users.value.find((user: any) => user.nome == nome);

  if (!nomeExistente) {
    users.value = [...users.value, { ...formList.value }];

    formList.value = { ...form };
  }
}

function removeUser(nome: string) {
  users.value = users.value.filter((user: any) => user.nome !== nome);
}

function editUser(nome: string) {
  const userEdited = users.value.find((user: any) => user.nome === nome);

  if (userEdited) {
    formList.value = { ...userEdited };

    users.value = users.value.filter((user: any) => user.nome !== nome);
  }
}
</script>


<template>
  <div>
    <v-card height="100vh">
      <v-navigation-drawer
        v-model="drawer"
        :color="color"
        :miniVariant="miniVariant"
        absolute
        temporary
        dark
      >
        <v-list dense nav class="py-0">
          <v-list-item two-line :class="miniVariant && 'px-0'">
            <v-list-item-content>
              <div class="">
                <v-img
                  src="../assets/logo@2x.png"
                  aspect-ratio="2"
                  contain
                ></v-img>
              </div>
            </v-list-item-content>
          </v-list-item>

          <v-divider></v-divider>

          <v-list-item v-for="item in items" :key="item.title" link>
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>

      <div class="navbar">
        <v-row>
          <v-col cols="auto" class="mr-auto">
            <v-list-item two-line>
              <v-btn
                absolute
                left
                icon
                color="#7B96C4"
                @click.stop="drawer = !drawer"
              >
                <v-icon>mdi-menu</v-icon>
              </v-btn>
            </v-list-item>
          </v-col>
          <v-col cols="auto">
            <v-list-item two-line>
              <v-list-item-avatar>
                <img src="../assets/Ellipse@2x.png" />
              </v-list-item-avatar>

              <v-list-item-content>
                <v-list-item-title style="color:#7B96C4"
                  >João da Silva</v-list-item-title
                >
              </v-list-item-content>
            </v-list-item>
          </v-col>
        </v-row>
      </div>
      <v-card-title style="font-weight:bold">
        Painel de cursos
        <v-spacer></v-spacer>
        <v-text-field
          style="display:flex"
          v-model="search"
          append-icon="mdi-magnify"
          label="Pesquisar cursos ou empresas"
          single-line
          hide-details
        ></v-text-field>
      </v-card-title>
      <v-data-table
        style="color:#737373"
        :headers="headers"
        :items="desserts"
        :header-props="data"
        :search="search"
      >
        <template v-slot:item.conteudo>
          <div class="text-center">
            <v-btn rounded color="primary">Ver descrição</v-btn>
          </div>
        </template>

        <!-- O código a seguir apresenta falhas de tamanho máximo da pilha de chamadas excedido -->

        <!-- <template v-slot:item.conteudo>
          <div class="text-center">
            <v-dialog v-model="dialog" max-width="480">
              <template v-slot:activator="{ on }">
                <v-btn rounded color="primary" v-on="on">Ver descrição</v-btn>
              </template>
              <v-card>
                <v-card-title class="headline">Descrição do Curso</v-card-title>
                <v-card-text>{{desserts[0].conteudo}}</v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn text @click="dialog = false">Fechar</v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </div>
        </template> -->
      </v-data-table>
    </v-card>
  </div>
</template>

<style>
.navbar {
  text-align: center;
  position: relative;
  width: 100%;
  height: 89px;
  background: rgb(239, 244, 253);
}

.logoSidebar {
  height: 89px;
  width: 205px;
  background-color: #21324f;
}

.sidebar {
  position: absolute;
  left: 0;
  height: 100%;
  width: 205px;
  background-color: #293b5a;
  transition: all 0.3s;
}
</style>

<script lang="ts">
import Vue from "vue";
import Component from "vue-class-component";
import data from "../data";

@Component
export default class DataTable extends Vue {
  search: string = "";
  data: any = data;
  drawer: any = false;
  miniVariant: any = false;
  dialog: boolean = false;
  items: any = [
    { title: "Grupos Colaborativos", icon: "mdi-google-analytics" },
    { title: "Central de Mensagens", icon: "mdi-email" },
    { title: "Cursos em Destaque", icon: "mdi-file-star-outline" },
    { title: "Histórico", icon: "mdi-history" }
  ];
  color: any = "#293B5A";
  headers: any = [
    {
      width: "150",
      text: "Empresa",
      align: "left",
      value: "empresa"
    },
    { text: "Curso", value: "curso" },
    { text: "Descrição", value: "desc" },
    { text: "Qtd. de Alunos", value: "alunos" },
    { text: "Edição e Conteúdo", value: "conteudo" }
  ];
  desserts: any = [];

  mounted() {
    data.contents.map(r => {
      r.Courses.map(c => {
        this.desserts.push({
          empresa: r.Company,
          curso: c.Name,
          desc: c.Description,
          alunos: c.Quantity,
          conteudo:
            "Comunicar-se bem é um diferencial no mercado de trabalho. A forma como um profissional se apresenta e expõe suas ideias diante de um grupo, em reuniões e conversas de trabalho, faz muita diferença no resultado dos negócios que ele conduz. Para vencer o medo e as dificuldades de falar em público, existem técnicas, recursos e habilidades que podem ser desenvolvidas para falar com clareza e segurança. Com este curso, domine a arte de falar em público!"
        });
      });
    });
    console.log("desserts", this.desserts);
    console.log("headers", this.headers);
  }
}
</script>

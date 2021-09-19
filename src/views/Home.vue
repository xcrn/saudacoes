<template>
  <ion-page>
    <ion-header :translucent="true">
      <ion-toolbar>
        <ion-title>Saudações!</ion-title>
      </ion-toolbar>
    </ion-header>
    
    <ion-content :fullscreen="true">
      <ion-header collapse="condense">
        <ion-toolbar>
          <ion-title size="large">Olá!</ion-title>
        </ion-toolbar>
      </ion-header>
    
    <div class="body"> 
      <form @submit.prevent="horario">
        <div>
          <label>Digite a hora que está mostrando na sua tela: (__h)</label>
        </div>
        <input v-model.number="hora" type="number"/>
        <ion-button type="submit">Enviar</ion-button>
      </form>
      
      <span> {{ mensagem }} </span>
    </div>
    </ion-content>
  </ion-page>
</template>

<script lang="ts">
import { IonContent, IonHeader, IonPage, IonTitle, IonToolbar } from '@ionic/vue';
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Home',
  data() {
    return {
      hora: '', 
      mensagem: ''
    };
  },
  methods: {
    horario() {
      const {hora} = this;
      if(hora>= 0 && hora <= 5){
        this.mensagem = 'Boa noite';
      }
      if (hora>=6 && hora<= 12) { 
        this.mensagem = 'Bom dia';
      }
      if(hora>12 && hora<=18){
        this.mensagem = 'Boa tarde';
      }
      if (hora>=19 && hora <= 23) {  
        this.mensagem = 'Boa noite';
      }
      if (hora > 24){
         this.mensagem = 'Digite uma hora válida.';
      }
    }
  },
  components: {
    IonContent,
    IonHeader,
    IonPage,
    IonTitle,
    IonToolbar
  }
});
</script>

<style scoped>
.body {
  display: flex;
  flex-direction: column;
  text-align: center;
  justify-content: center;
  padding: 40px;
  background-color: rgb(121, 172, 238);
  height: 100vh;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}

label {
  margin: 5px 0;
}
input { 
  margin: 10px;
}

#container {
  text-align: center;
  
  position: absolute;
  left: 0;
  right: 0;
  top: 50%;
  transform: translateY(-50%);
}

#container strong {
  font-size: 20px;
  line-height: 26px;
}

#container p {
  font-size: 16px;
  line-height: 22px;
  
  color: #8c8c8c;
  
  margin: 0;
}

#container a {
  text-decoration: none;
}
</style>
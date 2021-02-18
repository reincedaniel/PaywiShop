<template>
      <q-dialog full-width persistent v-model="dialog" position="top">
      <q-card class="no-border-radius" style="width: 100%">
        <q-linear-progress :value="1" color="warning" />
    
            <q-card-section>
                <div class="col column text-center q-pb-md">
                    <q-btn @click="fecharDialog()" label="Fechar" class="bg-grey-2 no-border-radius" flat size="sm" color="grey-8" icon="logout" />
                </div>
                <div class="col column text-center">
                    Olá Querido/a😃,
                    😃 Inicie Sessão ou Crie uma Conta para poderes também vender Artigos na <span class="text-bold">Paywi-Shop</span>
                </div>
                <div class="col column text-center">
                    <div class="flex flex-center q-pt-md q-gutter-md">
                        <q-btn icon="screen_lock_rotation" no-caps class="no-border-radius text-white bg-warning" label="Iniciar a sessão" />
                        <q-btn icon="person_add" no-caps class="no-border-radius text-white bg-grey-9" label="Criar uma Conta" />

                    </div>
                </div>
            </q-card-section>
        <!-- <q-card-section class="row items-center no-wrap text-center">
          <div>
            <div class="text-weight-bold">The Walker</div>
            <div class="text-grey">Fitz & The Tantrums</div>
          </div>

          <q-space />

          <q-btn flat round icon="fast_rewind" />
          <q-btn flat round icon="pause" />
          <q-btn flat round icon="fast_forward" />
        </q-card-section> -->
      </q-card>
    </q-dialog>
</template>

<script>
export default {
    name:'D-CreateOrLogin',
    props:['dialog'],
      methods:{
    fecharDialog(){
        this.$emit('fecharDialog')
    }
  },

}
</script>

<style>

</style>
<template>
  <q-layout view="hHh Lpr lff">
    <q-header class="bg-white" height-hint="64">
        <div class="col q-px-md">
          <q-toolbar>
            <q-btn
              flat
              dense
              round
              color="grey-9"
              icon="menu"
              size="lg"
              aria-label="Menu"
              @click="drawer = !drawer" 
            />
            <q-space/>
            <img src="~assets/logo1.png" :width="$q.screen.gt.sm?'10%':'30%'" alt />

            <q-space/>

            <q-btn
              flat
              dense
              round
              color="grey-9"
              size="lg"
              icon="add_circle"
              @click="dialogCreateOrLogin=true"
              
            />
          </q-toolbar>
        </div>
    </q-header>
    <q-drawer
    
        v-model="drawer"

        :mini="!drawer || miniState"
        @click.capture="drawerClick"
        content-class="bg-info q-ml-lg"
        
      >
          <q-list class="col text-white">
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="screen_lock_rotation" >
                  <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
                    <strong>Iniciar a sessão</strong> 
                  </q-tooltip>
                </q-icon>
              </q-item-section>

              <q-item-section>
                Iniciar a sesão
              </q-item-section>
            </q-item>

            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="person_add">
                  <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
                    <strong>Criar uma Conta</strong> 
                  </q-tooltip>
                </q-icon>
              </q-item-section>

              <q-item-section>
                Criar uma Conta
              </q-item-section>
            </q-item>

          </q-list>

        <!--
          in this case, we use a button (can be anything)
          so that user can switch back
          to mini-mode
        -->
        <div class="q-mini-drawer-hide absolute" style="top: 7px; right: -15px">
          <q-btn
            dense
            round
            unelevated
            color="grey-9"
            icon="chevron_left"
            @click="miniState = true"
          />
        </div>
      </q-drawer>
    <q-page-container class="">
        <q-page class="flex column col q-px-lg">

          <router-view />
      </q-page>
    </q-page-container>


    <DCreateOrLogin @fecharDialog="fecharDialog()" :dialog="dialogCreateOrLogin"/>
  </q-layout>
</template>








<script>
import DCreateOrLogin from 'components/Dialogs/D-CreateOrLogin'
export default {
  name: 'MainLayout',
  data () {
    return {
      dialogCreateOrLogin:false,
      drawer: false,
      miniState: false
    }
  },
  methods:{
    fecharDialog(){
      this.dialogCreateOrLogin=false
    },
    drawerClick (e) {
      // if in "mini" state and user
      // click on drawer, we switch it to "normal" mode
      if (this.miniState) {
        this.miniState = false

        // notice we have registered an event with capture flag;
        // we need to stop further propagation as this click is
        // intended for switching drawer to "normal" mode only
        e.stopPropagation()
      }
    }

  },
  components:{
    DCreateOrLogin
  }
}
</script>


<style lang="sass">
  .bgcolor
    background: linear-gradient(to right, #fff00, #fff)
  .q-page
    background: linear-gradient(to right, #fff00, #fff)
  .degree
    top: -44px
  .skyline
    flex:0 0 100px
    background: url('~assets/skyline.png')
    background-size: contain
    background-position: center bottom
</style>

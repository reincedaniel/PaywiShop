 <template>
  <q-page class="flex bg-white">
    <div class="full-width">
      <div class="q-pl-sm q-pr-sm q-gutter-sm">
    <div class="col">
      <q-bar style="height:30px" dense class="bg-grey-9 text-white text-bold q-mb-md">
        <q-icon style="padding-left: 9px" size="sm" class="q-pr-md" name="roofing" />
        <div>Paywi-Shop / Início</div>
      </q-bar>
      <div class="col q-px-md">
        <q-input
          v-model="search"
          placeholder="Procurar"
          
          >

          <template v-slot:before>
            <q-icon
              name="my_location" />
          </template>

          <template v-slot:append>
            <q-btn round dense flat icon="tune">
              <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
                <strong>Filtro de Pesquisa</strong> 
              </q-tooltip>
            </q-btn>
            <q-btn round dense flat icon="search">
              <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
              <strong><em>Pesquisar</em></strong> 
            </q-tooltip>
            </q-btn>
          </template>
        </q-input>
      </div>

    </div>

        <div >
          <q-table
            title=""
            :data="data"
            :columns="columns"
            row-key="name"
            selection="multiple"
            :selected.sync="selected"
            :filter="search"
            grid
            hide-header
            no-data-label="..."
            :pagination.sync="pagination"
            :rows-per-page-options="rowsPerPageOptions"
            rows-per-page-label="Mostrar"
            no-results-label="Nenhum dado encontrado!"
          >

            <template v-slot:item="props">
              <div
                class="q-pa-md col-xs-12 col-sm-12 col-md-4 col-lg-3 grid-style-transition"
                :style="props.selected ? 'transform: scale(0.95);' : ''"
              >
                  <q-card class="no-border-radius">
                    <q-img src="https://cdn.quasar.dev/img/chicken-salad.jpg" />

                    <q-card-section>
                      <q-btn
                        fab
                        color="grey-9"
                        icon="place"
                        class="absolute"
                        style="top: 0; right: 12px; transform: translateY(-50%);"
                      >
                          <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
                            <strong>{{props.row.place}}</strong> 
                          </q-tooltip>
                      </q-btn>
                      <div class="row no-wrap items-center">
                        <div class="col text-h6 ellipsis">
                          {{props.row.name}}
                        </div>
                        <div class="col-auto text-grey text-caption q-pt-md row no-wrap items-center">
                          <q-tooltip anchor="top middle" self="bottom middle" :offset="[10, 10]">
                            <strong>{{props.row.place}}</strong> 
                          </q-tooltip>
                        </div>
                      </div>

                      <q-rating v-model="stars" :max="5" size="32px" />
                    </q-card-section>

                    <q-card-section class="q-pt-none">
                      <div class="text-h6 text-bold">
                       <span class="text-warning">{{props.row.price}} </span> <span class="text-grey-8">AKZ</span>
                      </div>
                      <div class="text-caption text-grey">
                        {{props.row.description}}
                      </div>
                    </q-card-section>

                    <q-separator />

                    <q-card-actions>
                      <div class="col column q-gutter-sm">
                      <q-btn icon="add_shopping_cart" class="bg-grey-3 no-border-radius text-warning" no-caps >
                        Adicionar
                      </q-btn>

                      <q-btn icon="credit_score" class="bg-warning no-border-radius" no-caps color="warning">
                        Finalizar Compras
                      </q-btn>
                      </div>

                    </q-card-actions>
                  </q-card>
                <!-- <q-card :class="props.selected ?  'bg-grey-2':'shadow-20'">
                  <q-card-section :class="getColorBg(props.row.status)">
                    <q-checkbox class="text-grey-7" color="secondary" dense v-model="props.selected"  />
                  </q-card-section>
                  <q-separator />
                    
                  <q-separator />
                <q-card-section>
                  <div :class="'text-overline '+getColorText(props.row.status)">{{getText(props.row.status)}} : <span class="text-grey-8 text-bold"> {{props.row.codigo}}</span> <q-btn round icon="file_copy" color="grey-8" size="xs"></q-btn></div>
                  <div class="text-h5 text-grey-8 q-mt-sm q-mb-xs">Via (Canal): {{props.row.name}}</div>
                  <div class="text-caption text-grey">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
                  </div>
                </q-card-section>
                  <q-card-section class="flex flex-center">
                      <q-img :src="props.row.path" style="width:10%; " alt />
                      
                  </q-card-section>

                  <q-card-section class="flex flex-center">
                    <q-btn-group  flat>
                      <q-btn size="md" label="Ver" color="light-blue-7"  icon="offline_pin" />
                      <q-btn size="md" label="Configurar" color="grey-9" icon="settings" />
                      <q-btn size="md" label="Anular" color="pink-9" icon="label_off" />
                    </q-btn-group>
                  </q-card-section>


            <q-card-actions class="bg-grey-2">
              <q-btn flat color="grey-8" label="Share" />

              <q-space />

              <q-btn
                color="grey"
                round
                flat
                dense
                :icon="expanded ? 'keyboard_arrow_up' : 'keyboard_arrow_down'"
                @click="expanded = !expanded"
              />
            </q-card-actions>

            <q-slide-transition>
              <div v-show="expanded">
                <q-separator />
                <q-card-section class="text-subitle2">
                  {{ lorem }}
                </q-card-section>
              </div>
            </q-slide-transition>
                </q-card> -->
              </div>
            </template>

          </q-table>
      

      </div>
        
      </div>
    </div>
  </q-page>
</template>


<script>
import {
  fasSignal,
  fasWifi,
  fasBatteryFull,
} from "@quasar/extras/fontawesome-v5";

export default {
  data() {
    return {
      stars: 4,
      search:'',
      text:'',

      tab: 'interacao',
      fabPos: [18, 75],
      draggingFab: false,
      isTest:false,
      bar2:false,
       pagination: {
        page: 1,
        rowsPerPage: this.getItemsPerPage(),
      },
      newInteracao:{

      },
      filter: '',
      selected: [],
      expanded: false,
      lorem: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      columns: [
        {
          name: 'desc',
          required: true,
          label: 'Dessert (100g serving)',
          align: 'left',
          field: row => row.name,
          format: val => `${val}`,
          sortable: true
        },

      ],
      data: [
        {
          name: 'Frango YB',
          codigo:'FB23242SA12',
          path:'http://localhost:8080/x12.jpg',
          price:7500,
          description:"Frango grelhado à braza, batata, salada, molho especial, pãozinhos, etc.",
          place:"Icolo& Bengo, Estrada de Catete, disvio do Bom Jesus"
        },

        {
          name: 'Pizza 4 Estações',
          codigo:'WB2324HS32',
          path:'http://localhost:8080/x12.jpg',
          price:5000,
          description:"Massa de 5 cm, queijo, cebola tomate, frango tika, chouriço, etc. ",
          place:"Viana 2, Luanda Sul, Mercado, de frente ao BFA"
        },
        {
          name: 'Humburger X Big',
          codigo:'TG003232LP233',
          path:'http://localhost:8080/x12.jpg',
          price:1500,
          description:"Carne bem passada, milho, fiambre, chouriço, batata, molho especial, etc.",
          place:"Nova Vida, rua 47, entrada A, AP. 1"
        },
        {
          name: 'Hot Dog Max',
          codigo:'WTA23HH24675',
          path:'https://placeimg.com/600/600/tech/iphone',
          price:700,
          description:"Salsicha grande, batata, chetchup, milho, fiambre, salada, etc.",
          place:"Benfica, Dona Xepa de Frente a Loja da Zap"
        }
      ]
    };
  },
   watch: {
    "$q.screen.name"() {
      this.pagination.rowsPerPage = this.getItemsPerPage();
    },
  },
  computed: {
    rowsPerPageOptions() {
      if (this.$q.screen.gt.xs) {
        return this.$q.screen.gt.sm ? [2, 4, 8, 12] : [3, 6];
      }

      return [3];
    },
  },
  methods:{
    factoryFn (file) {
     },
    getColorText(num){
      if(num==1){
        return 'text-green'
      }
      else if(num==2){
        return 'text-orange'
      }
      else if(num==3){
        return 'text-red'
      }
      else return 'text-grey-8'

    },
    getColorBg(num){
      if(num==1){
        return 'bg-green-1'
      }
      else if(num==2){
        return 'bg-orange-1'
      }
      else if(num==3){
        return 'bg-red-1'
      }
      else return 'bg-grey-2'

    },
    getText(num){
      if(num==1){
        return 'Integrado'
      }
      else if(num==2){
        return 'Em Breve'
      }
      else if(num==3){
        return 'Off-line'
      }
      else return 'Não Tipificado'

    },
    moveFab (ev) {
      this.draggingFab = ev.isFirst !== true && ev.isFinal !== true

      this.fabPos = [
        this.fabPos[0] - ev.delta.x,
        this.fabPos[1] - ev.delta.y
      ]
    },
    addInteracao(){
    
      this.limpar()
    },
    limpar(){
      this.bar2=false
      this.newInteracao={}
    },
    getItemsPerPage() {
      const { screen } = this.$q;
      if (screen.lt.sm) {
        return 3;
      }
      if (screen.lt.md) {
        return 6;
      }
      return 4;
    },
  },
  created() {
    this.fasSignal = fasSignal;
    this.fasWifi = fasWifi;
    this.fasBatteryFull = fasBatteryFull;
  },
};
</script>

<style lang="sass" scoped>
.my-card
  width: 100%
  max-width: 300px
</style>

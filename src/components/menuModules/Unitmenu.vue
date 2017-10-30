<<template>
  <div >
    <div>
      <p>
        <q-item-side avatar="statics/guy-avatar.png" >
        ¡Hola <span>{{userName}}</span>!.
        </q-item-side>
      </p>
    </div>
    <q-collapsible group="indexunit" icon="explore" label="Índice de la unidad didáctica" opened>
        <div>
            <app-index-unit></app-index-unit>
        </div>
    </q-collapsible>
    <q-collapsible group="indexunit" icon="perm_identity" label="Menú de la unidad didáctica">
        <div>
          <q-list no-border link inset-delimiter>
            <q-item @click="$refs.locutionModal.open()">
              <q-item-side icon="speaker notes" />
              <q-item-main label="Locución" sublabel="Mostrar la transcripción del audio incorporado en la escena de la unidad didáctica" />
            </q-item>
            <q-item @click="$refs.glossaryModal.open()">
              <q-item-side icon="find in page" />
              <q-item-main label="Glosario" sublabel="Glosario de la unidad didáctica" />
            </q-item>
            <q-item @click="$refs.bibliographyModal.open()">
              <q-item-side icon="library books" />
              <q-item-main label="Bibliografía" sublabel="Bibliografía relacionada con la unidad didáctica" />
            </q-item>
            <q-item @click= "launch('./statics/Test.pdf')">
              <q-item-side icon="book" />
              <q-item-main label="e-book" sublabel="Libro electrónico de la unidad didáctica en formato pdf" />
            </q-item>
          </q-list>
        </div>
    </q-collapsible>
    <q-list no-border link inset-delimiter>
        <q-item @click= "closeUnit()">
            <q-item-side icon="power settings new" />
            <q-item-main label="Cerrar" sublabel="Cerrar la unidad didáctica" />
        </q-item>
    </q-list>

    <!-- Modal dialogs -->
    <div>
        <q-modal 
        ref="locutionModal"
        :content-css= "{minWidth:'80vw', minHeight:'80vh'}"
      >
        <q-modal-layout>
          <q-toolbar slot="header">
              <q-icon name="speaker notes e"></q-icon>
              Locución
          </q-toolbar>

          <p>Módulo vista de la locución del la unidad didáctica</p>
          <q-btn flat @click="$refs.locutionModal.close()">Cerrar</q-btn>
        </q-modal-layout>
      </q-modal>

      <q-modal 
        ref="glossaryModal" 
        :content-css= "{minWidth:'80vw', minHeight:'80vh'}"
      >
        <q-modal-layout>
          <q-toolbar slot="header">
            <q-icon name="find in page e"></q-icon>
            Glosario
          </q-toolbar>
          <p>Módulo vista del glosario del la unidad didáctica</p>
          <q-btn flat  @click="$refs.glossaryModal.close()">Cerrar</q-btn>
        </q-modal-layout>
      </q-modal>

      <q-modal 
        ref="bibliographyModal"
        :content-css= "{minWidth:'80vw', minHeight:'80vh'}"
      >
        <q-modal-layout>
            <q-toolbar slot="header">
                <q-icon name="library books e"></q-icon>
                Bibliografía
            </q-toolbar> 

            <p>Módulo vista de la Bibliografía de la unidad didáctica</p>
            <q-btn flat  @click="$refs.bibliographyModal.close()">Cerrar</q-btn>
        </q-modal-layout>
    </q-modal>
    </div>  
      
  </div>
</template>
<script>
import IndexMenu from './Indexunit.vue'
import {
  openURL,
  QCard,
  QCardTitle,
  QCardMedia,
  QCardActions,
  QCardSeparator,
  QCardMain,
  QList,
  QModal,
  QModalLayout,
  QIcon,
  QItem,
  QItemMain,
  QItemSide,
  QItemTile,
  QCollapsible,
  QBtn,
  QChip,
  QToolbar
} from 'quasar'
export default {
  components: {
    QCard,
    QCardTitle,
    QCardMedia,
    QCardActions,
    QCardSeparator,
    QCardMain,
    QList,
    QModal,
    QModalLayout,
    QItem,
    QIcon,
    QItemMain,
    QItemSide,
    QItemTile,
    QCollapsible,
    QBtn,
    QChip,
    QToolbar,
    'app-index-unit': IndexMenu
  },
  data: function () {
    return {
      userName: 'noName'
    }
  },
  methods: {
    launch (url) {
      openURL(url)
    },
    getUserName: function () {
      return this.userName
    },
    closeUnit () {
      top.close()
    }
  }
}
</script>
<style>

</style>

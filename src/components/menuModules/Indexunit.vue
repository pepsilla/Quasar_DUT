<<template>
  <div>
    <q-list no-border link inset-delimiter>
        <q-item>          
            <q-item-side icon="fingerprint" />
            <q-item-main label="Título de la escena" sublabel="Breve descripción de la acción a desarrollar" />
        </q-item>
        <q-item >          
            <q-item-side icon="fingerprint" />
            <q-item-main label="Título de la escena" sublabel="Breve descripción de la acción a desarrollar" />
        </q-item>
        <q-item >          
            <q-item-side icon="fingerprint" />
            <q-item-main label="Título de la escena" sublabel="Breve descripción de la acción a desarrollar" />
        </q-item>
        </q-list>
  </div>

</template>
<script>
import {
  QList,
  QItem,
  QItemMain,
  QItemSide,
  QItemTile
} from 'quasar'
export default {
  components: {
    QList,
    QItem,
    QItemMain,
    QItemSide,
    QItemTile
  }
}
</script>
<<style>

</style>

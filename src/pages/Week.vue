  <template>
<div class="q-pa-md">
    <div class="row" style="align-items: center;">
      <div class="col-1">
        <q-btn class="float-left q-pr-sn"  icon="keyboard_arrow_left"  flat
        dense @click="minusWeek()" />
      </div>
      <div class="col-10" id="butt">
        <q-btn class="dateFond" @click="()=>{vision = !vision;}" >
          {{formatBtn}}
        </q-btn>
      </div>
      <div class="col-1">
        <q-btn class="float-right q-pl-sn"  icon="keyboard_arrow_right"  flat
        dense @click="plusWeek()" />
      </div>
    <div class="q-gutter-md items-start" id="picker" :style="vision? 'display:block!important' : 'display:none!important'">
      <q-date  v-model="date" @click="()=>{vision = !vision;}"
        v-touch-swipe.mouse.right="handleSwipeR"
        v-touch-swipe.mouse.left="handleSwipeL"
         />
    </div>
    <q-card
      class="my-card"
    >
      <q-card-section class="text-white" style="background: radial-gradient(circle, #35a2ff 0%, #014a88 100%)"
      v-touch-swipe.mouse.right="handleSwipeWeekR"
      v-touch-swipe.mouse.left="handleSwipeWeekL"
       >
        <div class="text-h6" >
        <!-- v-for="(day, index) in days" :key="index" -->
          day
        </div>
        <q-card-section class="q-pt-none" v-for="subject in subjects" :key="subject.name">
          {{subject.name}}: {{subject.assessment}}
        </q-card-section>
      </q-card-section>
    </q-card>
  </div>
</div>
</template>

<style>
 
.dateFond{
 background: white;
 width: 100%;

}
.my-card{
  width: 100%;
}

</style>


<script>
import { date } from 'quasar'
import moment, { locale } from 'moment';


export default {
  data () {
    return {
    date: new Date(Date.now()) ,
    n:'',
    // .toLocaleString('ru', {
    //     year: 'numeric',
    //     month: 'long',
    //     weekday: 'narrow',
    //     day: 'numeric',
    // })
    objectDay:[],
 

    vision: false,
    
    subjects: [{
          name: 'Алгебра',
          assessment:[5 , 4 , 3 , 2, 2, 2, 2, 2, 2, 2, 2 ]
        }, {
          name: 'Русский язык',
          assessment:[5 , 4 , 3 , 3]
        }, {
          name: 'Иностранный',
          assessment:[5 , 4 , 3 , 2 ]
        }, {
          name: 'География',
          assessment:[4 , 4 , 3 , 2 ]
        }, {
          name: 'История',
          assessment:[5 , 4 , 3 , 2 ]
        }, {
          name: 'Физика',
          assessment:[5 , 4 , 3 , 2 ]
        }, {
          name: 'Физкультура',
          assessment:[5 , 4 , 3 , 2 ]
      }],
    }
  },
  computed:{
    formatBtn(date){
      this.n = new Date(this.date)
      let monthplus = moment(this.n).add(1, 'month');
      let quantityDays = Math.round((monthplus - this.n) / 1000 / 3600 / 24);//кл-во дней в месяце
      let startw = moment(this.n).startOf('isoWeeks'); //начало недели 
      let endw = moment(this.n).endOf('isoWeeks');//конец недели
      let stroka = `${moment(startw).format('DD')}-${moment(endw).format('DD')} ${moment(this.date).locale('ru').format('MMMM YYYY')}`
      return stroka
    },
    weekDay(){
      let d = this.date
      for (let i = 1; i < 7; i++) { 
       let a = moment(d).isoWeekday(i).locale('ru').format('dddd')
       this.objectDay = a
      }
      return this.objectDay
    },
    // month(date){
    //     let t = new Date(this.date)
    //     let newDate = t(new Date(), { month: 1 })
    //     console.log(newDate)
    //   }
    // нипайму как привязать текущий день к нужному ему массиву рассписания
    // week(){
    //   this.days[0] = this.subjects[0],[1],[2]
    //   this.days[1] = this.subjects[3],[2],[4]
    // }
    },
    filters: {
  },
  methods:{
      plusWeek(date){
        let t = this.date
        t = moment(t).add(1,'isoWeek')
        this.date = t
        return this.date
      },
      minusWeek(date){
        let t = this.date
        t = moment(t).add(-1,'isoWeek')
        this.date = t
        return this.date
      },
      events(date){
        return moment(date).locale("ru").format('')
      },
      handleSwipeR(date){
        let t = this.date
        t = moment(t).add(1,'months')
        this.date = t
        return this.date
      },
      handleSwipeL(date){
        let t = this.date
        t = moment(t).add(-1,'months')
        this.date = t
        return this.date
      },
      handleSwipeWeekR(date){
        let t = this.date
        t = moment(t).add(1,'isoWeek')
        this.date = t
        return this.date
      },
      handleSwipeWeekL(date){
        let t = this.date
        t = moment(t).add(-1,'isoWeek')
        this.date = t
        return this.date
      },
    },
  
}
</script>
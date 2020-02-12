<template>
<div class="list">
<q-markup-table :separator="separator" flat bordered dense
    
    >
      <thead>
        <tr>
          <th class="text-left"></th>
          <th class="text-right">Calories</th>
          <th class="text-right">Fat (g)</th>
          <th class="text-right">Carbs (g)</th>
          <th class="text-right">Protein (g)</th>
          <th class="text-right">Sodium (mg)</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td class="text-left">Frozen Yogurt</td>
          <td class="text-right">159</td>
          <td class="text-right">6</td>
          <td class="text-right">24</td>
          <td class="text-right">4</td>
          <td class="text-right">87</td>
        </tr>
        <tr>
          <td class="text-left">Ice cream sandwich</td>
          <td class="text-right">237</td>
          <td class="text-right">9</td>
          <td class="text-right">37</td>
          <td class="text-right">4.3</td>
          <td class="text-right">129</td>
        </tr>
        <tr>
          <td class="text-left">Eclair</td>
          <td class="text-right">262</td>
          <td class="text-right">16</td>
          <td class="text-right">23</td>
          <td class="text-right">6</td>
          <td class="text-right">337</td>
        </tr>
        <tr>
          <td class="text-left">Cupcake</td>
          <td class="text-right">305</td>
          <td class="text-right">3.7</td>
          <td class="text-right">67</td>
          <td class="text-right">4.3</td>
          <td class="text-right">413</td>
        </tr>
        <tr>
          <td class="text-left">Gingerbread</td>
          <td class="text-right">356</td>
          <td class="text-right">16</td>
          <td class="text-right">49</td>
          <td class="text-right">3.9</td>
          <td class="text-right">327</td>
        </tr>
      </tbody>
    </q-markup-table>
</div>
</template>

<script>
import AppHelper from './AppHelper'

export default {
    

    data(){
        return{
            date: AppHelper.date ,
            separator: 'vertical'
        }
    },
computed:{
    objectDays() {
        return {
        date: [ 
        { id:1, date: moment(this.date).isoWeekday(1).locale('ru').format('dddd, D MMM')},
        { id:2, date: moment(this.date).isoWeekday(2).locale('ru').format('dddd, D MMM')},
        { id:3, date: moment(this.date).isoWeekday(3).locale('ru').format('dddd, D MMM')},
        { id:4, date: moment(this.date).isoWeekday(4).locale('ru').format('dddd, D MMM')},
        { id:5, date: moment(this.date).isoWeekday(5).locale('ru').format('dddd, D MMM')},
        { id:6, date: moment(this.date).isoWeekday(6).locale('ru').format('dddd, D MMM')}
        ]}
        },
    },
methods:{
    
  }
}
</script>

<style>
.list{
    height: 100%;
}
</style>
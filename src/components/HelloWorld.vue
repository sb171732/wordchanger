<template>
  <div class="hello">
    <div class="w3-padding">
      <el-button type="success" @click="change"> change </el-button>        
      <el-button type="warning" @click="change2"> change 2</el-button>        
    </div>      
      <el-row class="w3-margin-top">
         <el-col :span="12" class="w3-border-right">
             <textarea v-model="text1" id="" cols="100" rows="10"></textarea>
         </el-col>
         <el-col :span="12">
             <textarea v-model="text2" id="" cols="100" rows="10"></textarea>
         </el-col>
      </el-row>

  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      text1:'үптежир',
      text2:'',
      endings:['ар','ер','ур','үр','ир','ыр','эр'],
      ends2:[
        { end:'яр', rep:'й', count:2 },
        { end:'өер', rep:'өй', count:3 },
      ],
      replace:[
        {b1:'ж', rep:'ш'},
        {b1:'д', rep:'т'},
        {b1:'б', rep:'п'},
        {b1:'э', rep:'е'},
      ]
    }
  },
  methods:{
    // rep_change(row){
       
      //  row.forEach(word=>{
      //      this.ends2.forEach(end=>{
      //         let w = word
      //         let count = word.length
      //         let count2 = end.count
      //         let end2 =''
      //         for (let i=count2;i<=1;i--){
      //             end2=end2 +w[count-i]
      //         }
      //         console.log(end2)
      //      })
      //     //  console.log(word)
      //  })

    // },
    change(){
        // функция для изменеия форм слов, из неопреденной формы в лемму


        let v = this.text1
        var row = v.split('\n')         // расплитим строковые данные из textarea в массив row
        // console.log(row)
        // this.rep_change(row)
        
        var row2=[]                       // новый массив куда будем пушить измененные слова
        for(let i=0; i<=row.length-1; i++){    // цикл проходит по всему массиву слов
            var word = row[i].trim()                  // word - слово текущей итерации 
            let count = word.length            // длинна слова  
            // console.log(word)
            // console.log(count)
            var haveends = false               // переменная для опред-я наличия окончаний в массиве endings в слове
            for (let e=0;e<=this.endings.length-1;e++){          //   массив проходящий по окончаниям
              // console.log(this.endings[e])
              if  (word[count-2]+word[count-1]===this.endings[e]){    //   если в слове есть одно из окончаний то делаем haveendings true и break цикла
                   haveends = true             //
                   break
              }
            }
            if (haveends===true){     // если true присваиваем новому слову word2 все буквы кроме окончания 
                let word2=''
                for (let b=0;b<=count-3; b++){   // массив по буквам слова
                    word2 = word2 + word[b]      // складываем слово по буквам   
                }
                row2.push(word2)                 // пушим новое слово в новый массив
            } 
             
        }
       this.text2 = row2.join('\n')           // добавление измененных слов в textarea 2  
         
    },
    change2(){
        // эта функция применяет правило смены звонких букв на глухие при изменении формы слова
           
      
       let v = this.text2
       var row = v.split('\n')
       var row2 = []
       for (let i=0;i<=row.length-1;i++){
           let word = row[i]
           var haveends2 ='false'
           this.replace.forEach(element => {
              if (word[word.length-1]===element.b1){ haveends2 = element.rep }
                    // console.log(word[word.length-1])
                    // console.log(element.b1)
                    // console.log(element.rep)
                    // console.log(haveends2)
                    // console.log('-----------')
               });
            // console.log(haveends2)
           if (haveends2!='false'){
              let word2=''
              for(let j=0;j<=word.length-2;j++){
                 word2 = word2+word[j]
              }
              word2 = word2 +haveends2
              row2.push(word2)
           }
           else {
            row2.push(word)
           }
          this.text2 = row2.join('\n')
           
       }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

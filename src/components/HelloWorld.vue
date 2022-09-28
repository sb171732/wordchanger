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
      endings:['ар','ер','ур','үр','ир','ыр'],
      replace:[
        {b1:'ж', rep:'ш'},
        {b1:'д', rep:'т'},
        {b1:'б', rep:'п'},
      ]
    }
  },
  methods:{
    change(){
        let v = this.text1
        var row = v.split('\n')
        // console.log(row)
        var row2=[] 
        for(let i=0; i<=row.length-1; i++){
            var word = row[i]
            let count = word.length
            // console.log(word)
            // console.log(count)
            var haveends = false
            for (let e=0;e<=this.endings.length-1;e++){
              // console.log(this.endings[e])
              if  (word[count-2]+word[count-1]===this.endings[e]){
                   haveends = true   
              }
            }
            if (haveends===true){
                let word2=''
                for (let b=0;b<=count-3; b++){
                    word2 = word2 + word[b]
                }
                row2.push(word2) 
            } 
             
        }
       this.text2 = row2.join('\n')
         
    },
    change2(){
        
           
      
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

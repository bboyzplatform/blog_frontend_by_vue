<template>
    <div class="paperbox posttime">
        <ul>
            <li ><i @click="filter('')" class="fa fa-hand-pointer-o" aria-hidden="true">显示全部</i></li>
          <transition-group name="flip">
            <li v-for="(item,index) in Posttimes" :key="item" >
                <i @click="filter(item)" class="fa fa-hashtag" aria-hidden="true"> {{item}}</i>
            </li>
          </transition-group>
        </ul>
    </div>
</template>



<script>

import { mapActions } from 'vuex'

    export default {
        name:"Posttimes",
        data(){
            return{

            }
        },
       computed: {
        Posttimes() {
          return Array.from(new Set(this.$store.getters.getPosttimes))
        }
      },
      methods: {
        ...mapActions({
          filter: 'LOAD_TIME' 
        })
      }
    }

</script>
<style lang="stylus" scoped>
.flip-move {
  transition: transform 8s;
}


i
    border-bottom: 1px gray dashed;
    transition: 0.2s;
     

i:hover{
   
    color:#fff;
    background-color: #000;
    cursor: pointer;

}
   li{
  margin-top: 5px;
}
.posttime{
    background-color: #eee;
    margin-top: 20px;
}
</style>
<template>
  <div>
    <button :class="{active:item.active}" v-for="(item, idx) in list" :key="idx" @click="turnOn(idx)">{{item.year}}</button>
  </div>
</template>
<style>
    .active{color:blue;}
</style>
<script>
export default {
    data() {
        return {
            list: [2018, 2019, 2020, 2021, 2022, 2023]
        }
    },
    mounted(){
        this.list = this.list.map(item => {
            return {
                active: item == '2023' ? true : false,
                year: item
            }
        })
    },
    methods:{
        turnOn(idx) {
            if (this.list.filter(item => item.active).length == 1 && this.list[idx].active) {
                return;
            }
            this.list.map((item, index) => {
                if (idx == index) {
                    item.active = !item.active;
                }
            })
        }
    }

}
</script>


<style>

</style>
<template>
    <div class="search-box">
        <input type="text" class="search-bar" placeholder="Search..." 
        v-model="superValue" @keypress.enter="$emit('enter')"/>
    </div>
</template>

<script>
export default {
    props: {
        modelValue:{
            type:String,
            required:true
        }
    },
    computed: {
        superValue: {
            get(){
                return this.modelValue
            },
            set(x){
                this.$emit('update:modelValue', x)
            }
        }
    }
}
</script>

<style scoped>
.search-box {
  width: 100%;
  margin-bottom: 30px;
}

.search-box .search-bar {
  display: block;
  width: 100%;
  padding: 15px;

  color: #313131;
  font-size: 20px;

  appearance: none;
  border: none;
  outline: none;
  background: none;

  background-color: rgba(255,255,255,0.5);
  border-radius: 16px 16px 16px 16px;
  transition: 0.4s;
}

.search-box .search-bar:focus {
  box-shadow: 0px 0px 16px rgba(255,255,255,0.25);
  background-color: rgba(255,255,255,0.75);
}
</style>
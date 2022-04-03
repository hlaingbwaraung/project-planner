<template>
  <div class="project">
    <div class="flexing">
      <div @click="showDetail = !showDetail">
        <h3>{{ project.title }}</h3>
      </div>
      <div>
        <i class="bi bi-trash" @click="deleteProject"></i>
        <i class="bi bi-pen"></i>
        <i class="bi bi-check2"></i>
      </div>
    </div>
    <p v-if="showDetail">{{ project.detail }}</p>
  </div>
</template>

<script>
export default {
  props: ["project"],
  data() {
    return {
      showDetail: false,
      api:"http://localhost:3000/projects/"
    };
  },
  methods:{
    deleteProject(){
    fetch(this.api+this.project.id,{method:"DELETE"})
    .then(()=>{
        this.$emit("delete",this.project.id)
    })
    .catch((err)=>{
console.log(err);
    })
    }
  }
};
</script>

<style>
.project {
  padding: 20px;
  margin: 10px;
  border-radius: 20px;
  border-left:5px solid crimson;
  background: #ececec;
  box-shadow: 20px 20px 73px #ededed, -20px -20px 73px #ffffff;
}
h3 {
  color: indigo;
  cursor: pointer;
}
.flexing {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
i {
  margin-left: 15px;
}
.bi:hover {
  cursor: pointer;

  color: crimson !important;
}
</style>

<template>
  <h1>Edit Project</h1>
  <form @submit.prevent="addProject">
    <label>Project Title</label>
    <input type="text" v-model="title">
    <label>Project Detali</label>
    <textarea name="" id="" cols="30" rows="10" v-model="detail"></textarea>
    <button @click="updateProject">Update Project</button>
  </form>
</template>

<script>
export default {
    props:["id"],
    data(){
        return{
            title:"",
            detail:"",
            
        }
    },
    mounted(){
        fetch("http://localhost:3000/projects/"+this.id)
        .then((res)=>{
            return  res.json()
        })
        .then((data)=>{
            this.title=data.title
            this.detail=data.detail
        })
        .catch((err)=>{

        })
    },
    methods:{
        updateProject(){
            fetch("http://localhost:3000/projects/"+this.id,{
                method:"PATCH",
                headers:{"Content-Type":"application/json"},
                body:JSON.stringify({
                    title:this.title,
                    detail:this.detail
                })

            })
            .then(()=>{
                this.$router.push("/")
            })
            .catch((err)=>{
                
            })
        }
    }
}
</script>

<style>

</style>
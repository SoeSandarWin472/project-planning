<template>
 <div class="project" >
    <div class="flexing">
    <div ><h3 @click="showDetail=!showDetail"> {{ project.title }}</h3></div>
    <div>
        <span class="material-symbols-outlined">
        delete
        </span>
        <span class="material-symbols-outlined">
        edit
        </span>
        <span class="material-symbols-outlined">
        done
        </span>
    </div>
    </div>
     <p v-if="showDetail"> {{ project.detail }}</p>
    
 </div>
</template>

<script>
export default {
    props:['project'],
    data(){
        return{
            showDetail:false
        }
    }
}
</script>

<style>
.project {
    padding: 20px;
    background-color: #f2f2f2;
    margin:10px ;  
    border-left: 6px solid crimson;
}
h3{
    cursor: pointer;
    color: indigo;
}
.flexing{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
span{
    margin-left: 5px;
}
span:hover{
    cursor: pointer;
    color: #777;
}
</style>
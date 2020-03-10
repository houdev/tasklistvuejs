<template>
    <div class="Addtodo">
        <form @submit="addtodo">
            <input type="text" v-model="title" name="title" placeholder="Title">
            <input type="submit" value="Add" class="add-btn" v-bind:disabled="title < 3">
        </form>
    </div>
</template>

<script>
export default {
    name:"Addtodo",
    data(){
        return {
            title: "",
        }
    },

    methods:{
    addtodo(e){
        e.preventDefault();
        const newtodo = {
            id: Math.round(Math.random() *1000),
            title: this.title,
            completed: false,
            showEdit:false,
        }
        this.$emit('new-todo' , newtodo);
        this.title = "";
    },
    }
    
}
</script>

<style scoped>

.add-btn{
    padding: 5px;
    margin: 3px;
    background:limegreen;
    color:white;
    border: none;
}
.add-btn:disabled{
    padding: 5px;
    margin: 3px;
    background:gray;
    color:white;
    border: none;
}

</style>
<template>
    <div class="Addtodo">
        <form>
          <v-row>
            <v-col cols="10">
              <v-text-field label="Title" v-model="title"></v-text-field>
            </v-col>
            <v-col cols="2">
              <v-btn fab color="success"
              v-bind:disabled="title.length < 4" 
              @click="addtodo">
                <v-icon>
                    mdi-plus
                </v-icon>
              </v-btn>
            </v-col>
          </v-row>
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
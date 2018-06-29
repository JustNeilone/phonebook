<template>
<div>
<nav class="panel column is-offset-2 is-8">
  <p class="panel-heading">
    Laravel|Vue.js Phonebook Application
    <button class="button is-link is-outlined" @click="openAdd">
      Add new contact
    </button>
  </p>
  
  <div class="panel-block">
    <p class="control has-icons-left">
      <input class="input is-small" type="text" placeholder="search">
      <span class="icon is-small is-left">
        <i class="fa fa-search" aria-hidden="true"></i>
      </span>
    </p>
  </div>
  
  
  <a class="panel-block" v-for="item,key in lists">
    <span class="column is-9">
    {{item.name}}
    </span>
<span class="panel-icon column is-1">
      <i class="has-text-danger fa fa-trash" aria-hidden="true"></i>
    </span></i>
    <span class="panel-icon column is-1">
      <i class="has-text-info fa fa-edit" aria-hidden="true"></i>
    </span></i>
    <span class="panel-icon column is-1">
      <i class="has-text-primary fa fa-eye" aria-hidden="true" @click="openShow"></i>
    </span></i>
  </a>
  
  <div class="panel-block">
    
  </div>
</nav>
<Add :openmodal='addActive' @closeRequest='close'></Add>
</div>



</template>

<script>

let Add = require('./Add.vue');
 export default{
 	components:{Add},
 	data(){
 	return{
 	addActive : '',
 	showActive : '',
 	lists:{},
 	errors:{}	
 	}
 	},
 	mounted(){
 	axios.post('/getData').then((response)=>this.lists = response.data)
  .catch((error)=> this.errors = error.response.data.errors)
 	},
 	methods:{
 	openAdd(){
 	this.addActive = 'is-active';
 	},
 	openShow(){
 	this.showActive = 'is-active';
 	},
 	close(){
 		this.addActive =''
 	}
 	}
 }
</script>
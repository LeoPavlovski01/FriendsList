<template>
  <body>
  <header>
    <h1>FriendList</h1>
  </header>
  <section id="app">
    <ul v-for="friend in friends" :key="friend.id">
      <li>
        <h2>{{friend.name}}</h2>
        <button
            @click="showDetails(friend)"
            :aria-expanded="selectedItem === friend.id"
        >
          Show Details
        </button>
        <ul v-if="selectedItem === friend.id">
          <li><strong>Phone:</strong> {{friend.phone}}</li>
          <li><strong>Email:</strong> {{friend.email}}</li>
        </ul>
      </li>
    </ul>
  </section>
  </body>
</template>

<script>
export default{
  data(){
    return{
      selectedItem:null,
      friends:[
        {id:1, name:'Manuel Lorenz', phone:'01234 5678 991' , email:'manuel@localhost.com'},
        {id:2, name:'Julie Jones', phone:'01234 5678 991' , email:'julie@localhost.com'}
      ]
    }
  },
  methods:{
    // showDetails(item){
    //  this.friends = this.friends.map(friend=>{
    //    if(friend.id === item.id){
    //      return {...friend , details: !friend.details};
    //    }
    //    else{
    //      return {...friend , details:false,}
    //    }
    //  })
    //   console.log('Friends : ' , this.friends);
    // },
    showDetails(item){
      // If the item is selected , disselect  it  otherwise select it .
      this.selectedItem = this.selectedItem === item.id ? null : item.id;
    }
  },
}
</script>


<style>
* {
  box-sizing: border-box;
}

html {
  font-family: 'Jost', sans-serif;
}

body {
  margin: 0;
}

header {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 3rem auto;
  border-radius: 10px;
  padding: 1rem;
  background-color: #58004d;
  color: white;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app ul {
  margin: 0;
  padding: 0;
  list-style: none;
}

#app li {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  margin: 1rem auto;
  border-radius: 10px;
  padding: 1rem;
  text-align: center;
  width: 90%;
  max-width: 40rem;
}

#app h2 {
  font-size: 2rem;
  border-bottom: 4px solid #ccc;
  color: #58004d;
  margin: 0 0 1rem 0;
}

#app button {
  font: inherit;
  cursor: pointer;
  border: 1px solid #ff0077;
  background-color: #ff0077;
  color: white;
  padding: 0.05rem 1rem;
  box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
  background-color: #ec3169;
  border-color: #ec3169;
  box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

</style>

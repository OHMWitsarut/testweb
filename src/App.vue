<template>
  <img  src="./assets/Barcelona-Logo.png" width="200">
  <h1>{{title}}</h1>
  <canvas id="myChart" width="400" height="400"></canvas><br>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/JIoxfAb01Y4" 
          title="YouTube video player" frameborder="0" 
          allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
          allowfullscreen>
  </iframe>
  <br>
  <br>
  <br>
  <div>
    <input type="text" 
           v-model="newTask" 
           placeholder="New Name">
    <button @click="addTasks" :disabled="newTask.length< 1">ADD NAME</button>
  </div>
  
  <div v-if="newTask.length > 0">
  <h3> New Name </h3>
    <h2>{{newTask}}</h2>
  </div>
  <br>

  <center>
    <table>
    
      <tr>
        <th width="30" align="left"> Number</th>
        <th width="300"> Name</th>
        <th> detail</th>
      </tr>
    
      <tr v-for="task in tasks" key="task.id"><td align="center"> {{task.id}}.</td>
          <td>{{task.name}}</td>
          <td> 
            <div v-if="task.finshed">
                  <button >detail</button>
            </div>
            <div v-else-if="task.edit">
                  <button>edit</button>
            </div>
            <div v-else>
                <p>No detail</p>
            </div>
          </td>
      </tr>
    </table>
  </center>
  <div>
      {{ message }}
    </div>
  <!-------Do not change below this line------->
  <div align="right">
    <iframe src="//widget.calendarlabs.com/v1/calendar.php?cid=1001&ver=1.2&uid=9833589006&c=26&l=en&cbg=800000&cfg=fff&hfg=fff&hfg1=fff&ct=1&cb=1&cbc=2275FF&cf=verdana&cp=bottom&sw=0&hp=t&ib=0&ibc=&i=images/" 
      align="center"  width="170" height="155" marginwidth=0 marginheight=0 frameborder=no scrolling=no allowtransparency='true'>Loading...
    </iframe>
  </div>
    <!-------Do not change above this line------->
    
</template>

<script>



export default {
  data(){
    return{
      title: 'Welcome to Barcelona',
      message: 'Witsarut Bunmee',
      newTask: '',
      tasks: [
        { id:1 , name: 'Marc-André ter Stegen', finshed : true },
        { id:2 , name: 'Héctor Bellerín', finshed : false },
        { id:3 , name: 'Gerard Piqué', finshed : false },
      ]
    }
  },
  methods:{
    addTasks(){
      if (this.tasks.length <1) return;

      this.tasks.push({
        id: this.tasks.length + 1,
        name: this.newTask,
        finshed: false
      });

      this.newTask ='';
    }
  }
 
}

</script>

<style>
#app {
  font-family: Avenir, Courier ;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #341501;
  margin-top: 60px;
  background-color: rgb(251, 251, 251);;
}
</style>

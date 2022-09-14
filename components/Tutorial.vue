<template>
  <b-card>
    <b-list-group>
      <b-row>
      <b-col v-for="col in cols" :key="col.caption">
          <h1>{{col.caption}}</h1>
        <draggable class="dragArea" group="panels" v-model="panels">
          <b-list-group-item v-for="panel in col.panels" :key="panel.id">{{panel.message}}</b-list-group-item>
        </draggable>
      </b-col>
      </b-row>  
    </b-list-group>  
  </b-card>
</template>

<script>
import draggable from 'vuedraggable'
export default {
  name: 'Tutorial',
  components:  {
    draggable
  },
  data: () => ({ 
      cols:[
        {
          caption:"backlog",
          panels:[
           {
            id:1,
            message:"testmessage",
           } 
            
          ]
        },
        {
          caption:"sachritt 1",
          panels:[
           {
            id:1,
            message:"testmessage",
           },
           {
            id:2,
            message:"asdfasdf",
           },
           {
            id:3,
            message:"testmeqwertqertssage",
           },
           {
            id:4,
            message:"testshwrthmessage",
           },
           {
            id:5,
            message:"testmesxcvbxcvbzuiosage",
           },
           {
            id:6,
            message:"testmessqwertage",
           },
            
          ]
        },
        {
          caption:"schritt 2",
          panels:[
           {
            id:1,
            message:"testmessage",
           } 
            
          ]
        },
        {
          caption:"blockiert",
          panels:[
           {
            id:1,
            message:"testmessage",
           } 
            
          ]
        },
        {
          caption:"fertig",
          panels:[
           {
            id:1,
            message:"testmessage",
           } 
            
          ]
        },         
      ],

  }),
}
</script>
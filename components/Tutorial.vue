<template>
  <div id="kanbanBoard">
    <b-list-group>
      <b-row>
      <b-col v-for="col in cols" :key="col.caption">
        <b-card>
        <h1>{{col.caption}}</h1>
        <draggable class="dragArea" group="panels" v-model="panels">
          <b-list-group-item v-for="panel in col.panels" :key="panel.id">
            <b-row>
              <b-col sm:1 md:1250>
                  <h2>{{panel.panelCaption}}</h2>
                  <p>{{panel.message}}</p>
              </b-col>
            </b-row>
          </b-list-group-item>
        </draggable>
        </b-card>
      </b-col>
      </b-row>  
    </b-list-group>  
  </div>
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
            panelCaption:"caption10",
            message:"testmessage",
           } 
            
          ]
        },
        {
          caption:"sachritt 1",
          panels:[
           {
            id:1,
            panelCaption:"caption9",
            message:"testmessage",
           },
           {
            id:2,
            panelCaption:"caption8",
            message:"asdfasdf",
           },
           {
            id:3,
            panelCaption:"caption7",
            message:"testmeqwertqertssage",
           },
           {
            id:4,
            panelCaption:"caption6",
            message:"testshwrthmessage",
           },
           {
            id:5,
            panelCaption:"caption5",
            message:"testmesxcvbxcvbzuiosage",
           },
           {
            id:6,
            panelCaption:"caption4",
            message:"testmessqwertage",
           },
            
          ]
        },
        {
          caption:"schritt 2",
          panels:[
           {
            id:1,
            panelCaption:"caption3",
            message:"testmessage",
           } 
            
          ]
        },
        {
          caption:"blockiert",
          panels:[
           {
            id:1,
            panelCaption:"caption2",
            message:"testmessage",
           } 
            
          ]
        },
        {
          caption:"fertig",
          panels:[
           {
            id:1,
            panelCaption:"caption1",
            message:"testmessage",
           } 
            
          ]
        },         
      ],

  }),
}
</script>
<template>
  <div>
      <b-row>
        <b-col v-for="col in cols" :key="col.caption">
          <b-card>
            <h1>{{ col.caption }}</h1>
            <draggable
              class="dragArea"
              group="panels"
              v-model="col.panels"
              :list="col.panels"
            >
              <div v-for="panel in col.panels" :key="panel.id">
                    <h2>{{ panel.panelCaption }}</h2>
                    <p>{{ panel.message }}</p>
              </div>
            </draggable>
            <b-button
              block
              variant="success"
              v-b-modal.ticket-modal
              @click="setCurrentCaption(col.caption)"
              >+</b-button
            >
          </b-card>
        </b-col>
      </b-row>
    <b-form id="ticketForm">
      <b-modal
        id="ticket-modal"
        title="Ticket hinzufügen:"
        ok-title="Bestätigen"
        ok-variant="success"
        cancel-title="Abbruch"
        cancel-variant="danger"
        @ok="addTicket"
      >
        <b-form-group
          id="titelGroup"
          label="Tickettitel"
          label-for="tickettitel"
        >
          <b-form-input
            id="formTicketCaption"
            v-model="newTicket.panelCaption"
            required
          ></b-form-input
        ></b-form-group>
        <b-form-group
          id="contentGroup"
          label="Ticketbeschreibung"
          label-for="ticketcontent"
        >
          <b-form-input
            id="formticketcontent"
            v-model="newTicket.message"
            required
          ></b-form-input
        ></b-form-group>
        <b-form-group
          id="contentGroup"
          label="Ticketaufwand"
          label-for="ticketdifficulty"
        >
          <b-spinbutton id="ticketdifficulty" min="1" max="10"></b-spinbutton
        ></b-form-group>
      </b-modal>
    </b-form>
    <b-card header="Board Json Raw">
      <pre class="m-0">{{ cols }}</pre>
    </b-card>
  </div>
</template>

<script lang="ts">
import draggable from "vuedraggable";
export default {
  name: "Tutorial",
  components: {
    draggable,
  },
  data: () => ({
    currentCaption: "",
    newTicket: {
      panelCaption: "",
      message: "",
    },
    cols: [
      {
        caption: "backlog",
        panels: [
          {
            panelCaption: "caption10",
            message: "testmessage",
          },
        ],
      },
      {
        caption: "schritt 1",
        panels: [
          {
            panelCaption: "caption9",
            message: "testmessage",
          },
          {
            panelCaption: "caption8",
            message: "asdfasdf",
          },
          {
            panelCaption: "caption7",
            message: "testmeqwertqertssage",
          },
          {
            panelCaption: "caption6",
            message: "testshwrthmessage",
          },
          {
            panelCaption: "caption5",
            message: "testmesxcvbxcvbzuiosage",
          },
          {
            panelCaption: "caption4",
            message: "testmessqwertage",
          },
        ],
      },
      {
        caption: "schritt 2",
        panels: [
          {
            panelCaption: "caption3",
            message: "testmessage",
          },
        ],
      },
      {
        caption: "blockiert",
        panels: [
          {
            panelCaption: "caption2",
            message: "testmessage",
          },
        ],
      },
      {
        caption: "fertig",
        panels: [
          {
            panelCaption: "caption1",
            message: "testmessage",
          },
        ],
      },
    ],
    isModalVisible: false,
  }),
  methods: {
    setCurrentCaption(caption: string) {
      this.currentCaption = caption;
    },
    showModal() {
      this.isModalVisible = true;
    },
    closeModal() {
      this.isModalVisible = false;
    },
    addTicket() {
      this.cols
        .find((col) => col.caption === this.currentCaption)
        ?.panels.push(this.newTicket);
      this.newTicket = {
        panelCaption: "",
        message: "",
      };
    },
  },
};
</script>
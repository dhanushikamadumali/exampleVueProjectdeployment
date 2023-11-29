<template>
  <div>
    <center>
      <v-row>
        <v-col lg="4" v-for="item in items" :key="item.firstname">
          <v-list lines="three">
            <v-list-item
              :title="item.firstname + ' ' + item.lastname"
              :subtitle="item.gendar"
            ></v-list-item>
            <v-btn
              block=""
              color="blue"
              elevation="10"
              @click="openDialog(item.title, item.firstname, item.lastname)"
              >senddata</v-btn
            >
          </v-list>
        </v-col>
      </v-row>
    </center>
    <v-dialog width="500" v-model="dialog">
      <DialogModal :title="title" :FormData="form" />
    </v-dialog>
  </div>
</template>
<script>
import DialogModal from "@/components/DialogModal.vue";

export default {
  components: {
    DialogModal,
  },
  data() {
    return {
      items: [
        {
          title: "ehgr11",
          firstname: "ferf1",
          lastname: "qwrdfweregf1",
          gendar: "afertyh",
        },
        {
          title: "ehgrtsdreger222",
          firstname: "ferf2",
          lastname: "qwrdfweerg2",
          gendar: "afer",
        },
        {
          title: "ehgrtdfgbvd333",
          firstname: "ferf3",
          lastname: "qwrdfweth3",
          gendar: "afer",
        },
      ],
      dialog: false,
      title: "",
      form: {},
    };
  },
  methods: {
    openDialog(title, firstname, lastname) {
      console.log(title);
      this.dialog = true;
      this.title = title;
      this.form.firstname = firstname;
      this.form.lastname = lastname;
    },
  },
};
</script>

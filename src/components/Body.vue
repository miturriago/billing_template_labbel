<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-img
          src="https://res.cloudinary.com/dos13qenv/image/upload/v1595486292/Labbel/icono_gnqumt.png"
          class="my-3"
          contain
          height="200"
        />
      </v-col>

      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">Welcome to BillApp</h1>

        <p class="subheading font-weight-regular">
          Application developed to create billing <br />
          Please visit us
          <a href="https://www.labbel.com.co" target="_blank">Labbel.com.co</a>
        </p>
      </v-col>

      <v-col class="mb-5" cols="12">
        <h2 class="headline font-weight-bold mb-3">Do we start?</h2>

        <v-row justify="center">
          <v-btn color="primary" class="ma-2" dark @click="dialog = true">
            START!
          </v-btn>
        </v-row>
      </v-col>
    </v-row>
    <v-dialog
      v-model="dialog"
      fullscreen
      hide-overlay
      transition="dialog-bottom-transition"
      scrollable
    >
      <v-card tile>
        <v-toolbar flat dark color="primary">
          <v-btn icon dark @click="dialog = false">
            <v-icon>mdi-close</v-icon>
          </v-btn>
          <v-toolbar-title>BillApp</v-toolbar-title>
          <v-spacer></v-spacer>
          <v-toolbar-items>
            <v-btn dark text @click="dialog = false"> Generate </v-btn>
          </v-toolbar-items>
          <v-menu bottom right offset-y>
            <v-list>
              <v-list-item
                v-for="(item, i) in items"
                :key="i"
                @click="() => {}"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </v-toolbar>
        <v-card-text>
          <v-list three-line subheader>
            <v-subheader>Date</v-subheader>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Creation date </v-list-item-title>
                <v-list-item-subtitle>Billing issue date</v-list-item-subtitle>
                <v-col cols="12" sm="6">
                  <v-menu
                    ref="menu"
                    v-model="menu"
                    :close-on-content-click="false"
                    :return-value.sync="date"
                    transition="scale-transition"
                    offset-y
                    min-width="290px"
                  >
                    <template v-slot:activator="{ on, attrs2 }">
                      <v-text-field
                        v-model="date"
                        label="Date"
                        prepend-icon="mdi-calendar"
                        readonly
                        v-bind="attrs2"
                        v-on="on"
                      ></v-text-field>
                    </template>
                    <v-date-picker v-model="date" no-title scrollable>
                      <v-spacer></v-spacer>
                      <v-btn text @click="menu = false">Cancel</v-btn>
                      <v-btn text color="primary" @click="$refs.menu.save(date)"
                        >OK</v-btn
                      >
                    </v-date-picker>
                  </v-menu>
                </v-col>
              </v-list-item-content>
            </v-list-item>

            <v-divider></v-divider>

            <v-subheader>Client information</v-subheader>

            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Addressed to</v-list-item-title>
                <v-list-item-subtitle
                  >Full name of the person or company to which it is
                  addressed</v-list-item-subtitle
                >
                <v-col cols="12" sm="6">
                  <v-text-field
                    v-model="message4"
                    label="Full name"
                    outlined
                    clearable
                  ></v-text-field>
                </v-col>
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Identification</v-list-item-title>
                <v-list-item-subtitle
                  >Select the type of identification and enter the
                  number</v-list-item-subtitle
                >
                <v-col class="d-flex" cols="12" sm="2">
                  <v-select :items="items" label="Type" outlined></v-select>
                </v-col>
                <v-col cols="12" sm="4">
                  <v-text-field
                    v-model="message4"
                    label="Number"
                    outlined
                    clearable
                  ></v-text-field>
                </v-col>
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Address</v-list-item-title>
              <v-list-item-subtitle>Residence address</v-list-item-subtitle>
              <v-col cols="12" sm="6">
                <v-text-field
                  v-model="message4"
                  label="Address"
                  outlined
                  clearable
                ></v-text-field>
              </v-col>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>City / department</v-list-item-title>
              <v-list-item-subtitle
                >City and department</v-list-item-subtitle
              >
              <v-col cols="12" sm="6">
                <v-text-field
                  v-model="message4"
                  label="City / Department"
                  outlined
                  clearable
                ></v-text-field>
              </v-col>
            </v-list-item-content>
          </v-list-item>
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title>Phone Number</v-list-item-title>
              <v-list-item-subtitle
                >Contact phone number</v-list-item-subtitle
              >
              <v-col cols="12" sm="6">
                <v-text-field
                  v-model="message4"
                  label="Phone number"
                  outlined
                  clearable
                ></v-text-field>
              </v-col>
            </v-list-item-content>
          </v-list-item>
          <v-divider></v-divider>
          <v-list three-line subheader>
            <v-subheader>General</v-subheader>
            <v-list-item>
              <v-list-item-action>
                <v-checkbox v-model="notifications"></v-checkbox>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>Notifications</v-list-item-title>
                <v-list-item-subtitle
                  >Notify me about updates to apps or games that I
                  downloaded</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-action>
                <v-checkbox v-model="sound"></v-checkbox>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>Sound</v-list-item-title>
                <v-list-item-subtitle
                  >Auto-update apps at any time. Data charges may
                  apply</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
            <v-list-item>
              <v-list-item-action>
                <v-checkbox v-model="widgets"></v-checkbox>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>Auto-add widgets</v-list-item-title>
                <v-list-item-subtitle
                  >Automatically add home screen widgets</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-card-text>

        <div style="flex: 1 1 auto"></div>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  name: "body",

  data: () => ({
    menu: false,
    date: new Date().toISOString().substr(0, 10),
    dialog: false,
    notifications: false,
    sound: true,
    widgets: false,
    items: ["NIT", "CC", "TI", "CE"],

    ecosystem: [
      {
        text: "Mauricio Maldonado",
        href: "https://github.com/miturriago",
      },
    ],

    whatsNext: [
      {
        text: "Explore components",
        href: "https://vuetifyjs.com/components/api-explorer",
      },
      {
        text: "Select a layout",
        href: "https://vuetifyjs.com/getting-started/pre-made-layouts",
      },
      {
        text: "Frequently Asked Questions",
        href:
          "https://vuetifyjs.com/getting-started/frequently-asked-questions",
      },
    ],
  }),
};
</script>

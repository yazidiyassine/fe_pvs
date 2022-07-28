<template>
<div class="ajout">

     <v-card elevation="2" 
  outlined  class="mx-auto my-auto justify-center"
     >
     <v-toolbar class="nvbar mb-3" flat height="34px" app>
  <v-toolbar-title  class=" darkgrey--text text-h6">معطيات الشكاية</v-toolbar-title>
  </v-toolbar>
        <v-form 
        dense
         ref="form"
        class="ma-0 pa-0 px-2">
          
           <v-row no-gutters dense >
          <v-col cols="12" sm="4" class="ml-2">
            <v-select
            class="blue-lighten-6" 
            label="نوع الشكاية" 
             dense
            outlined
            >
            </v-select>
          </v-col>
          
          <v-col cols="12" sm="4" class="ml-2">
            <v-select
            item-text="nom" 
            item-value="id" 
            label="مصدر الشكاية"
            dense 
            required 
            outlined
           
            >
            </v-select>
          </v-col>
          </v-row>
          <v-row  dense no-gutters>
           <v-col cols="12" sm="4" class="ml-2">
          <v-text-field 
            dense
            outlined
            required 
            label="مرجع الشكاية"
          ></v-text-field>
        </v-col>
        <v-col cols="12" sm="4" class="ml-2">
          <v-text-field dense 
            single-line
            outlined
            required 
            label="مكان الوقائع"
          ></v-text-field>
        </v-col>
</v-row>
<v-row no-gutters dense>
          <v-col
      cols="12"
      sm="3" class="ml-2"
    >
      <v-menu
        ref="menu"
        v-model="menu"
        :close-on-content-click="false"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            prepend-inner-icon="mdi-calendar"
            readonly
            v-bind="attrs" dense
            v-on="on"
            outlined required 
            label="تاريخ الشكاية"
          ></v-text-field>
        </template>
        <v-date-picker
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            color="primary"
            @click="$refs.menu.save(plaint.datePlaints)"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>
    </v-col>
        <v-col
      cols="12"
      sm="3" class="ml-2"
    >

      <v-menu
        ref="menu1"
        v-model="menu1"
        :close-on-content-click="false"
        :return-value.sync="date1"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            v-model="plaint.dateEnregPlaints" dense
            prepend-inner-icon="mdi-calendar"
            readonly :rules="rules.name"
            v-bind="attrs"
            v-on="on" required 
            label="تسجيل الشكاية"
            outlined
          ></v-text-field>
        </template>
        <v-date-picker
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            outlined
            color="primary"
            @click="$refs.menu1.save()"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>
    </v-col>
     <v-col
      cols="12"
      sm="3"
      class="ml-2"
    >
      <v-menu
        ref="menu2"
        v-model="menu2"
        :close-on-content-click="false"
        :return-value.sync="date2"
        transition="scale-transition"
        offset-y
        min-width="auto"
      >
        <template v-slot:activator="{ on, attrs }">
          <v-text-field
            dense
           prepend-inner-icon="mdi-calendar"
            readonly
            v-bind="attrs"
            v-on="on" required 
            label="تاريخ الوقائع"
            outlined
          ></v-text-field>
        </template>
        <v-date-picker
          no-title
          scrollable
        >
          <v-spacer></v-spacer>
          <v-btn
            text
            color="primary"
            @click="menu = false"
          >
            Cancel
          </v-btn>
          <v-btn
            text
            color="primary"
            @click="$refs.menu2.save()"
          >
            OK
          </v-btn>
        </v-date-picker>
      </v-menu>
    </v-col>
    </v-row>
    <v-row no-gutters dense>
    <v-col cols="12" sm="9" class="ml-2">
    <v-textarea
    clearable dense
    label="موضوع الشكاية"
    class="font-weight-black"
    rows="1"
    outlined
    no-resize
    >
    </v-textarea>
    </v-col>
        </v-row>
        </v-form>

   </v-card>
   <v-card 
  outlined  class="mx-auto my-4"
  flat
     >
        <v-form>
  <v-spacer></v-spacer>

        <template><v-card flat  class="mt-9 mr-4">
          <v-form><v-row  dense justify align-content-center><v-col cols="12" sm="4">
 <v-file-input
    color="blue accent-4"
    counter class="mt-3"
    label="أضف المُرفق"
    multiple
    placeholder="أضف المُرفق"
    prepend-icon="mdi-file-plus"
    outlined dense
    :show-size="1000"
  >
    <template v-slot:selection="{ index, text }">
      <v-chip
        v-if="index < 2"
        color="blue accent-4"
        light
        label
        small
      >
        {{ text }}
      </v-chip>

      <span
        v-else-if="index === 2"
        class="text-overline grey--text text--lighten-3 mx-2"
      >
        +{{ files.length - 2 }} File(s)
      </span>
    </template>
  </v-file-input></v-col><v-col cols="12" sm="4">
     <v-card-actions>
              <v-btn
              hidden
              text
              light
              class="my-2 green lighten-1"
              elevation="2"
            >
            <v-icon right >mdi-notebook-plus-outline</v-icon>             
              حفظ
              </v-btn>     
              </v-card-actions></v-col>
      </v-row></v-form></v-card>
</template>
  <v-row>
    <v-col cols="12" sm="4"></v-col>
   <v-card-actions class="mt-4">
              <v-btn
               text
              height="30px"
              class="my-2 blue"
              elevation="2" 
              :loading="load"
            >
            <v-icon left >mdi-notebook-plus-outline</v-icon>             
               تسجيل الشكاية
              </v-btn>
              <v-btn
          text
          height="30px"
              class="my-2 red"
              elevation="2"
        >
          إلغاء
        </v-btn>
        <v-spacer></v-spacer>
              </v-card-actions></v-row>
          </v-form>
  </v-card>
</div>

</template>
 
 
<script>
export default {
   data () {
     const defaultForm = Object.freeze({
         contreInconnu:false,
        TypePlaintID:null,
        SourcePlaintID: null,
        referencePlaints:"",
        datePlaints:"",
        dateEnregPlaints:"",
        dateFaits:"",
        EmplaceFaits: "",
        sujetPlaints:""
      })
       return {
         plaint: Object.assign({}, defaultForm),
         slct: null,
         rules: {
            name: [val => (val || '').length > 0 || 'المرجوا ملأ هذا الحقل'],
      select: [(v) => !!v || 'المرجوا ملأ هذا الحقل'],
      select2: [(v) =>  v.length>0 || ''],
      
    },
    tab:null,
        snackbar: false,
         load:false,

         editedIndex:-1,
         editedItem:{},
         dialogDelete:false,
        plaint:{
        contreInconnu:false,
        TypePlaintID:null,
        SourcePlaintID: null,
        referencePlaints:"",
        datePlaints:"",
        dateEnregPlaints:"",
        dateFaits:"",
        EmplaceFaits: "",
        sujetPlaints:""
        },
        defaultForm,
        datePlaints: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        dateEnregPlaints: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        dateFaits: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
        menu: false, modal: false,menu1: false, modal1: false, menu2: false, modal2: false,
       }
}
}
</script>
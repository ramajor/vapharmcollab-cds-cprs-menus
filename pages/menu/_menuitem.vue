<template>
  <div>
    <b-container>
      <h3>{{ PageHeader }}</h3>
      <div>
        This will be replaced with better menu layout, just testing dynamic
        content pull
      </div>
      <NuxtLink to="/PrimaryMenu">Go back to Primary Menu</NuxtLink>
      <b-row>
        <!-- First Column -->
        <b-col>
          <div class="my-3" v-for="item in C1items" :key="item.index">
            <div v-if="item.Header === 1">
              <!-- Div only shows if Header is true (1) -->
              <h5>{{ item.Text }}</h5>
            </div>
            <div v-else-if="item.Text === '[emptyRow]'">&nbsp;</div>
            <div v-else>
              <!-- Div only shows if Header is false (0) -->
              <div>{{ item.Text }}</div>
              <small v-if="item.Item">>> {{ item.Item }}</small>
            </div>
          </div>
        </b-col>
        <!-- Second Column -->
        <b-col v-if="col2">
          <div class="my-3" v-for="item in C2items" :key="item.index">
            <div v-if="item.Header === 1">
              <!-- Div only shows if Header is true (1) -->
              <h5>{{ item.Text }}</h5>
            </div>
            <div v-else-if="item.Text === '[emptyRow]'">&nbsp;</div>
            <div v-else>
              <!-- Div only shows if Header is false (0) -->
              <div>{{ item.Text }}</div>
              <small v-if="item.Item">>> {{ item.Item }}</small>
            </div>
          </div>
        </b-col>
        <!-- Third Column -->
        <b-col v-if="col3">
          <div class="my-3" v-for="item in C3items" :key="item.index">
            <div v-if="item.Header === 1">
              <!-- Div only shows if Header is true (1) -->
              <h5>{{ item.Text }}</h5>
            </div>
            <div v-else-if="item.Text === '[emptyRow]'">&nbsp;</div>
            <div v-else>
              <!-- Div only shows if Header is false (0) -->
              <div>{{ item.Text }}</div>
              <small v-if="item.Item">>> {{ item.Item }}</small>
            </div>
          </div>
        </b-col>
        <!-- Fourth Column -->
        <b-col v-if="col4">
          <div class="my-3" v-for="item in C4items" :key="item.index">
            <div v-if="item.Header === 1">
              <!-- Div only shows if Header is true (1) -->
              <h5>{{ item.Text }}</h5>
            </div>
            <div v-else-if="item.Text === '[emptyRow]'">&nbsp;</div>
            <div v-else>
              <!-- Div only shows if Header is false (0) -->
              <div>{{ item.Text }}</div>
              <small v-if="item.Item">>> {{ item.Item }}</small>
            </div>
          </div>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
//imports
import MenuData from '~/static/OrderMenus.json';
export default {
  async asyncData({ params, redirect }) {
    const filteredMenuItem = MenuData.find(
      (el) => el.Name.replace(/\W/g, '_') === params.menuitem
    );
    if (filteredMenuItem) {

//****repeating same function 4 times here... can refactor this to thin out
//Column 1
      let C1items = filteredMenuItem.contents.filter((i) => i.Column === 1);
      { //brackets here for variable scope only
      //add in blank lines for missing numbers
      let existingLines = [];
      //first get all existing numbers
      for (var i = 0; i < C1items.length; i++) {
        existingLines[i] = C1items[i]['Row'];
      }
      //next get the highest line number used
      let maxLine = Math.max(...existingLines);
      //use high number to loop through them all and add missing lines
      for (var i = 1; i < maxLine; i++) {
        //if the existing rows array does not contain the curent line (test returns -1)
        if (existingLines.indexOf(i) < 0) {
          //then create and add an empty row to our data
          var emptyRow = {
            Row: i,
            Text: '[emptyRow]',
          };
          C1items.push(emptyRow);
        }
      }
      }//brackets here for variable scope only
      C1items.sort((x, y) => x.Row - y.Row);

//column2
      let C2items = filteredMenuItem.contents.filter((i) => i.Column === 2)
      {//brackets here for variable scope only
      //add in blank lines for missing numbers
      let existingLines = [];
      //first get all existing numbers
      for (var i = 0; i < C2items.length; i++) {
        existingLines[i] = C2items[i]['Row'];
      }
      //next get the highest line number used
      let maxLine = Math.max(...existingLines);
      //use high number to loop through them all and add missing lines
      for (var i = 1; i < maxLine; i++) {
        //if the existing rows array does not contain the curent line (test returns -1)
        if (existingLines.indexOf(i) < 0) {
          //then create and add an empty row to our data
          let emptyRow = {
            Row: i,
            Text: '[emptyRow]',
          };
          C2items.push(emptyRow);
        }
      }//brackets here for variable scope only
      }
      C2items.sort((x, y) => x.Row - y.Row);

//Column3
      let C3items = filteredMenuItem.contents.filter((i) => i.Column === 3)
      {//brackets here for variable scope only
      //add in blank lines for missing numbers
      let existingLines = [];
      //first get all existing numbers
      for (var i = 0; i < C3items.length; i++) {
        existingLines[i] = C3items[i]['Row'];
      }
      //next get the highest line number used
      let maxLine = Math.max(...existingLines);
      //use high number to loop through them all and add missing lines
      for (var i = 1; i < maxLine; i++) {
        //if the existing rows array does not contain the curent line (test returns -1)
        if (existingLines.indexOf(i) < 0) {
          //then create and add an empty row to our data
          var emptyRow = {
            Row: i,
            Text: '[emptyRow]',
          };
          C3items.push(emptyRow);
        }
      }//brackets here for variable scope only
      }
      C3items.sort((x, y) => x.Row - y.Row);

//Column4
      let C4items = filteredMenuItem.contents.filter((i) => i.Column === 4)
      { //brackets here for variable scope only
      //add in blank lines for missing numbers
      let existingLines = [];
      //first get all existing numbers
      for (var i = 0; i < C4items.length; i++) {
        existingLines[i] = C4items[i]['Row'];
      }
      //next get the highest line number used
      let maxLine = Math.max(...existingLines);
      //use high number to loop through them all and add missing lines
      for (var i = 1; i < maxLine; i++) {
        //if the existing rows array does not contain the curent line (test returns -1)
        if (existingLines.indexOf(i) < 0) {
          //then create and add an empty row to our data
          var emptyRow = {
            Row: i,
            Text: '[emptyRow]',
          };
          C4items.push(emptyRow);
        }
      }//brackets here for variable scope only
      }
      C4items.sort((x, y) => x.Row - y.Row);

//set true or false to show columns if they have content in them
      let col2 = C2items.length > 0; //returns true if at least one item is in the array
      let col3 = C3items.length > 0;
      let col4 = C4items.length > 0;

      return {
        C1items,
        C2items,
        C3items,
        C4items,
        col2,
        col3,
        col4,
        PageHeader: filteredMenuItem.Name,
      };
    } else {
      return {
        C1items: [],
        C2items: [],
        C3items: [],
        C4items: [],
        col2: false,
        col3: false,
        col4: false,
        PageHeader: 'The menu you are searching for is not found!',
      };
    }
  },
};
</script>

<style>
</style>

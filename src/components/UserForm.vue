<template>

  <div class="container">
    <label for="c1">Class 1</label>
    Monday: <input type="checkbox" name="mon" />
    Tuesday: <input type="checkbox" name="tue" /> 
    Wednesday: <input type="checkbox" name="wed" /> 
    Thursday: <input type="checkbox" name="th" /> 
    Friday: <input type="checkbox" name="fri" />
    <input
      @keyup.enter="saveMessage1"
      type="text"
      id="c1"
      name="class1"
      placeholder="course name"
      v-model="message"
    />
    <label for="c2">Class 2</label>
    Monday: <input type="checkbox" name="mon" />
    Tuesday: <input type="checkbox" name="tue" /> 
    Wednesday: <input type="checkbox" name="wed" /> 
    Thursday: <input type="checkbox" name="th" /> 
    Friday: <input type="checkbox" name="fri" />
    <input
      @keyup.enter="saveMessage2"
      type="text"
      id="c2"
      name="class2"
      placeholder="course name"
      v-model="message1"
    />
    <label for="c3">Class 3</label>
    Monday: <input type="checkbox" name="mon" />
    Tuesday: <input type="checkbox" name="tue" /> 
    Wednesday: <input type="checkbox" name="wed" /> 
    Thursday: <input type="checkbox" name="th" /> 
    Friday: <input type="checkbox" name="fri" />
    <input
      @keyup.enter="saveMessage3"
      type="text"
      id="c3"
      name="class3"
      placeholder="course name"
      v-model="message2"
    />
    <label for="c4">Class 4</label>
    Monday: <input type="checkbox" name="mon" />
    Tuesday: <input type="checkbox" name="tue" /> 
    Wednesday: <input type="checkbox" name="wed" /> 
    Thursday: <input type="checkbox" name="th" /> 
    Friday: <input type="checkbox" name="fri" />
    <input
      @keyup.enter="saveMessage4"
      type="text"
      id="c4"
      name="class4"
      placeholder="course name"
      v-model="message3"
    />
    <p>
      Classes: {{ message }}, {{ message1 }}, {{ message2 }}, {{ message3 }}
    </p>
    <br />
    <label for="sem">Choose a semester</label>
    <select v-model="selected">
      <option disabled value="">Please select a semester</option>
      <option>Spring</option>
      <option>Fall</option>
    </select>
    <br />
    <br />
    <span>Selected: {{ selected }}</span>
    <br />
    <br />
    <!--
    Here, I'm trying to submit everything to the database just by clicking the button
    <input type="submit" value="Submit" @onclick="saveMessages"/>
    -->
  </div>
</template>

<script>

//import * as mdc from "material-components-web";
//import firebase from "firebase";
import { db } from "../main.js";

//var db = firebase.firestore();
export default {
  data() {
    return {
      message: "",
      message1: "",
      message2: "",
      message3: "",
      selected: ""
    };
  },

  methods: {
    saveMessage1() {
      // Save message1 to firestore
      db.collection("class").add({
        c1: this.message
      });
    },
    saveMessage2() {
      // Save message1 to firestore
      db.collection("class").add({
        c2: this.message1
      });
    },
    saveMessage3() {
      // Save message1 to firestore
      db.collection("class").add({
        c3: this.message2
      });
    },
    saveMessage4() {
      // Save message1 to firestore
      db.collection("class").add({
        c4: this.message3
      });
    }
  }
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
label {
  text-align: left;
  color: #18b1ff;
}
p {
  font-weight: bold;
}
input[type="text"],
select {
  width: 100%; /* Full width */
  padding: 12px; /* Some padding */
  border: 1px solid #ccc; /* Gray border */
  border-radius: 4px; /* Rounded borders */
  box-sizing: border-box; /* Make sure that padding and width stays in place */
  margin-top: 6px; /* Add a top margin */
  margin-bottom: 16px; /* Bottom margin */
}
</style>

---
title: "Username Generator"
date: 2017-07-21
tags: [software, html, css, javascript]
header:
    image:
---

<html>
<head>
  <link rel="stylesheet" type="text/css" href="/assets/css/style_username.css">
</head>
<body>
  <div id="instructions_container">
    <p> To use the generator, complete any of the fields that contain information you wish to include in your potential username. 
        When you are ready, press the submit button and up to 9 usernames will be generated for you. Enjoy! </p>
  </div>
  <div id="form_container">
  <form id="form1" action="" method="get">
    <table id="form_table">
      <tr>
        <td>
          Name:         <input class="input_box" type="text" name="name">
        </td>
        <td>
          Lucky Number: <input class="input_box" type="number" name="number">
        </td>
      </tr>
      <tr>
        <td>
          Favourite Colour: <input class="input_box" type="text" name="colour">
        </td>
        <td>
          Profession: <input class="input_box" type="text" name="profession">
        </td>
      </tr>
      <tr>
        <td>
          Adjective: <input class="input_box" type="text" name="adjective">
        </td>
        <td>
          Favourite Video Game: <input class="input_box" type="text" name="video_game">
        </td>
      </tr>
      <tr>
        <td>
          Favourite Sport: <select class="input_box" id="sport">
                             <option value=""> -- </option>
                             <option value="soccer"> Soccer </option>
	       	             <option value="ball"> Basketball </option>
                             <option value="football"> Football </option>
                             <option value="hockey"> Hockey </option>
                             <option value="golf"> Golf </option>
                             <option value="swimming"> Swimming </option>
                             <option value="baseball"> Baseball </option>
                             <option value="tennis"> Tennis </option>
                           </select>
        </td>
        <td>
          Favourite Animal: <select class="input_box" id="animal">
                             <option value=""> -- </option>
                             <option value="dog"> Dog </option>
                             <option value="cat"> Cat </option>
                             <option value="hamster"> Hamster </option>
                             <option value="bird"> Bird </option>
                             <option value="lizard"> Lizard </option>
                             <option value="snake"> Snake </option>
                             <option value="fish"> Fish </option>
                             <option value="bunny"> Bunny </option>
                           </select>
        </td>
      </tr>
    </table>
    <input type="button" class="button" onclick="myFunction()" value="Submit">
  </form>
  </div>
  <div id="username_box" style="display: none;">
    <!-- div that will display generated usernames upon button click -->
    <div id="username_display" style="display: none;">
    </div>
  </div>

<script>
function myFunction() {

  // define form1
  var form1 = document.getElementById("form1");

  // variable to hold number of input fields, input tags + select tags, minus 1 to account for button
  var numInputFieldsTotal = form1.getElementsByTagName("input").length - 1;

  var inputFields = document.getElementsByTagName("input");
  
  // same variable as above, but only counts inputs that have been filled out
  var numActiveInputFields = 0;
  
  /* loop through input fields, add to numInputFieldsTotal variable
  if field is not empty and exclude the value of the submit button */
  for (var j=0; j < numInputFieldsTotal; j++) {
    if (inputFields[j].value != "" && inputFields[j].value != "Submit") {
      numActiveInputFields += 1;
    }
  }

  // same process for select fields

  // all select fields
  var selectFields = form1.getElementsByTagName("select");

  // same variable as above to store active select fields, only counts filled out select inputs in for loop
  var numActiveSelectFields = 0; 

  for (var h=0; h < selectFields.length; h ++) {
    if (selectFields[h].value != "") {
      numActiveSelectFields += 1;
    }
  }
 
  // sum of total active input and select fields, minus 1 to account for button
  var sumActiveFields = numActiveInputFields + numActiveSelectFields;
  
  // store all inputs into an array
  var arrayInputs = [];
  for (var i=0; i < (numInputFieldsTotal); i++) {
    /* assign each input to a variable if input not empty and 
    not submit (to avoid button value) and not the same as other values */
    if (inputFields[i].value != "" && inputFields[i].value != "Submit" && !arrayInputs.includes(inputFields[i].value)) {
      arrayInputs[i] = inputFields[i].value;
    }
    // otherwise assign the index a placeholder number equal to the index
    else {
      arrayInputs[i] = i;
    }
  }
 
  var tempInputArrayLength = arrayInputs.length;
  /* remove placeholders numbers from before. Two variables are used
  in this foor loop. The splicing method removes the index and pushes
  the other indices in front of it down 1 spot. Thus this must be 
  accounted for by decrementing the variable b each time the splicing
  occurs */
  var a = 0
  var b = a;
  for(a; a < tempInputArrayLength; a++) {
    if(arrayInputs[b] == a) {
      console.log("Splice" + " a: " + a + " b: " + b);
      arrayInputs.splice(b, 1);
      b -= 1;
    }
    b += 1;
  }
  
  // store all select inputs into an array
  var arraySelectInputs = [];
  for (var k=0; k < 2; k++) {
    // make sure select field is filled in
    if (selectFields[k].value != "") {
      arraySelectInputs[k] = selectFields[k].value;
    }
  }

  // combine the two arrays of regular inputs and select inputs
  arrayAllInputs = arrayInputs.concat(arraySelectInputs);

  // variable to hold arrays of multiple usernames
  var usernames = [];
  
  // loop that combines all the inputs in a random order, number of times dictated by "q < x" where x represents the number of times
  for ( var q=0; q < 9; q++) {
    // initialize an array inside the username array
    usernames[q] = [];
    
    // keep adding to the inside array until all the inputs have been inserted
    while (usernames[q].length < arrayAllInputs.length) {
      
      // generate a random number to pick a random input
      var random = Math.floor(Math.random() * arrayAllInputs.length);
      
      // if the input is not already in the inside array, add it 
      if (!usernames[q].includes(arrayAllInputs[random])) {
        usernames[q].push(arrayAllInputs[random]);
      }
    }
  }
  
  var usernameStrings = [];
  // join inside arrays into strings, w < "x" x should be the same as the q < "X" from the above for loop
  for ( var w=0; w < 9; w ++) {
    usernameStrings[w] = usernames[w].join("");
  }

  // open larger username box for users to view
  document.getElementById("username_box").style.display = "block";
  
  // open username display box for users to view
  document.getElementById("username_display").style.display = "block";
  
  // clear previous content from username_display
  document.querySelector('#username_display').innerHTML = "";

  // display usernames individually
  for( var n=0; n < 9; n++) {
    // print a new line after every 3 usernames
    if( (n % 3 == 0) && (n !=0) ) {
      document.querySelector('#username_display').innerHTML += ("<br>");
    }
    // check if username combo already exists
    if (document.querySelector('#username_display').innerHTML.indexOf(usernameStrings[n]) != -1) {
      document.querySelector('#username_display').innerHTML += "  ";
    }
    else {
      document.querySelector('#username_display').innerHTML += "  " + usernameStrings[n];
    }
  }
}
</script>

</body>
</html>
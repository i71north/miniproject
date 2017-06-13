<!DOCTYPE html>
<html>
<head>
<style>
body {
  margin: 0;
  min-width: 250px;
}
/* Include the padding and border in an element's total width and height */
* {
  box-sizing: border-box;
}
/* Remove margins and padding from the list */
ul {
  margin: 0;
  padding: 0;
}
/* Style the list items */
ul li {
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  background: #eee;
  font-size: 18px;
  transition: 0.4s;
  
  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #2DCCD3;
}
/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}
/* On click, add a background color and strike out text */
ul li.checked {
  background: #000;
  color: #fff;
  text-decoration: line-through;
}
/* Add a check mark when clicked on */
ul li.checked::before {
  content: '';
  position: absolute;
  border-color: #fff;
  border-style: solid;
  border-width: 0 2px 2px 0;
  top: 10px;
  left: 16px;
  transform: rotate(45deg);
  height: 15px;
  width: 7px;
}
/* Style the close button */
.close {
  position: absolute;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px
}
.close:hover {
  background-color: #f44336;
  color: white;
}
/* Style the header */
.header {
  background-color: #008B98;
  padding: 30px 40px;
  color: #fff;
  text-align: center;
}
/* Clear floats after the header */
.header:after {
  content: "";
  display: table;
  clear: both;
}
/* Style the input */
input {
  border: none;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 18px;
}
/* Style the "Add" button */
.addBtn {
  border-radius: 4px;
  padding: 10px;
  width: 25%;
  background: #E05D49;
  color: #fff;
  float: left;
  text-align: center;
  font-size: 18px;
  cursor: pointer;
  transition: 0.4s;
}
.addBtn:hover {
  background-color: #bbb;
}
</style>
</head>
<body>

<div id="myDIV" class="header">
  <h2 style="margin:5px">Cleveland Codes Applicant To Do List</h2>
  <input type="text" id="myInput" placeholder="Add a task...">
  <span onclick="newElement()" class="addBtn">Add</span>
</div>

<ul id="myUL">
 <li class="checked">Complete the Online form</li>
  <li class="checked">Complete the assessment</li>
  <li>Complete the mini-project</li>
  <li>Update my resume</li>
  <li>Practice for my interview</li>
</ul>
 
<script>
// Create a "close" button and append it to each list item
var myNodelist = document.getElementsByTagName("LI");
var i;
for (i = 0; i < myNodelist.length; i++) {
  var span = document.createElement("SPAN");
  var txt = document.createTextNode("\u00D7");
  span.className = "close";
  span.appendChild(txt);
  myNodelist[i].appendChild(span);
}
// Click on a close button to hide the current list item
var close = document.getElementsByClassName("close");
var i;
for (i = 0; i < close.length; i++) {
  close[i].onclick = function() {
    var div = this.parentElement;
    div.style.display = "none";
  }
}
// Add a "checked" symbol when clicking on a list item
var list = document.querySelector('ul');
list.addEventListener('click', function(ev) {
  if (ev.target.tagName === 'LI') {
    ev.target.classList.toggle('checked');
  }
}, false);
// Create a new list item when clicking on the "Add" button
function newElement() {
  var li = document.createElement("li");
  var inputValue = document.getElementById("myInput").value;
  var t = document.createTextNode(inputValue);
  li.appendChild(t);
  if (inputValue === '') {
    alert("You must write something!");
  } else {
    document.getElementById("myUL").appendChild(li);
  }
  document.getElementById("myInput").value = "";
  var span = document.createElement("SPAN");
  var txt = document.createTextNode("\u00D7");
  span.className = "close";
  span.appendChild(txt);
  li.appendChild(span);
  for (i = 0; i < close.length; i++) {
    close[i].onclick = function() {
      var div = this.parentElement;
      div.style.display = "none";
    }
  }
}
</script>
</body>
<!-- Create for intial code base https://www.w3schools.com -->
</html>

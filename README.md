/* bling.js */

    window.$ = document.querySelector.bind(document);
    window.$$ = document.querySelectorAll.bind(document);

    Node.prototype.on = window.on = function (name, fn) {
      this.addEventListener(name, fn);
    }

    NodeList.prototype.__proto__ = Array.prototype;

    NodeList.prototype.on = NodeList.prototype.addEventListener = function (name, fn) {
      this.forEach(function (elem, i) {
        elem.on(name, fn);
      });
    }

// jquery can be an overkill for some projects where you are just craving the jquery shorthands
// heres an amazing 11 lines of code by bling.js which can make ur life way easier in writing javascript
// theres one addition to the library which was added by wes bos  supposedly you can check his presentation heres
// https://wesbos.github.io/just-javascript/#1

// impoprted bling js mini library above lets use it

// $('button').on('click', el => alert('safa'));
    console.log($('main'))       // gets single element

// Instead of using
    document.getElementById('mybutton').addEventListener('click' , () => {
      document.querySelector('section').style.background="cyan";
      // console.log('hhoveriing')
    });

// write this
    $('#mybutton').on('click' , () => {
      $('main').style.background = "purple";
    });


// NodeList.prototype.__proto__ = Array.prototype;
// This Gives us all array functions to use in our NodeLists
// like map filter etc
// sweet isnt it

    let i = 1;
    $$('p').map(single_p => {
     single_p.textContent = `This is line ${i}`
      i++
    });


// Earlier we use to Use Huge syntax for adding event listeners to multiple buttons of the same class
// not anymore

// Earlier we wrote

    document.querySelectorAll('.yolo').forEach((btn) => {
      btn.addEventListener('click' , () => alert('I was clicked 😋'))
    });

// With Modified Bling JS

    $('.yolo').on('click' , () => alert('I was clicked but you sweat less 😋') )

## Example of a calculator that performs addition, subtraction, multiplication and division operations on binary numbers in JS.

![Problem description](https://github.com/girls-incode/js-binary-numbers-operations/blob/master/hackerrank-challenges-js10-binary-calculator.png)

It can be found on [hackerrank.com](https://www.hackerrank.com/challenges/js10-binary-calculator/problem)

## index.html:

```html
<html>
    <head>
        <meta charset="utf-8">
        <title>Binary Calculator</title>
        <link rel="stylesheet" href="css/binaryCalculator.css" type="text/css">
    </head>
    <body>
        <div id="calc">
            <div id="res"></div>
            <div id="btns">
                <button id="btn0">0</button>
                <button id="btn1">1</button>
                <button id="btnClr">C</button>
                <button id="btnEql">=</button>
                <button id="btnSum">+</button>
                <button id="btnSub">-</button>
                <button id="btnMul">*</button>
                <button id="btnDiv">/</button>
            </div>
        </div>
        <script src="js/binaryCalculator.js" type="text/javascript"></script>
    </body>
</html>
```
## binaryCalculator.css:

```css
body {
 width: 33%   
}

#res {
    height: 48px;
    border: solid;
    background-color: lightgray;
    font-size: 20px;
}

#btn0, #btn1 {
    background-color: lightgreen;
    color: brown;
}

#btnClr, #btnEql {
    background-color: darkgreen ;
    color: white;
}

#btnSum, #btnSub, #btnMul, #btnDiv {
    background-color: black;
    color: red;
}

#btns button {
    width: 25%;
    height: 36px;
    float: left;
    margin: 0;
    font-size: 18px;
}
```

## binaryCalculator.js:

```javascript
let res = document.getElementById('res');
let btns = document.querySelector('#btns');

function print(ev) {
    let btn = ev.target;
    switch(btn.id) {
        case 'btns':
            return;
        case 'btnClr':
            res.innerHTML = '';
            break;
        case 'btnEql':
            if (res.innerHTML) {
                let op = (res.innerHTML).match(/\D{1}/g);
                if (op && op.length == 1) {
                    op = op[0];
                    let [num1, num2] = (res.innerHTML).split(op).map(n => Number(parseInt(n, 2)));
                    if (!Number.isNaN(num1) && !Number.isNaN(num2) && 
                        num1 > 0 && num2 > 0 && 
                        num1.toString().length <= 15 && num2.toString().length <= 15) {
                            let total = Math.floor(eval(num1 + op + num2));
                            // max length of an integer: 15
                            if (total.toString().length <= 15) {
                                res.innerHTML = total.toString(2);
                            }
                    }
                }
            }
            break;
        default:
            res.innerHTML += btn.innerHTML;
            break;
    }
}

btns.addEventListener('click', print);
```

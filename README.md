# CURRENCY CONVERTER-TASK-2

#Create a currency converter app that convertsbetween different currencies.

#CODE:

INDEX.HTML:
```
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="initial-scale=1.0 ,maxinum-scale=1.0,user-scalable=1">
        
        <link rel="stylesheet" href="style.css">
    <body>
        <div class="container">
            <h1>currency converter</h1>
            <div class="box">
              <div class="left-box">
                  <select name="currency" class="currency">
                  </select>
                  <input type="number" name="" id="input">
              </div>
              <div class="right-box">
                  <select name="currency" class="currency"></select>
                  <input type="number" name="" id="result">
              </div>
          </div>
          <div class="btn">
              <button id="btn">Convert</button>
          </div>
          
            

      </div>
      <script  src="script.js"></script>
  </body>
</html>
```
STYLE.CSS:
```
html,
body{
   font-family: 'Poppins', sans-serif;
   background: color #9be1e1e2;
   margin: 0;
   padding: 0;
   box-sizing: border-box;
}
  
  body{
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .container{
    background-color:#50589c;
    padding: 15px 24px;
    border-radius: 0px;
    width: 500px;
  }
  
  h1{
    color:#a7f9ff;
    text-align: center;
    margin-bottom: 0.5em;
    font-family: sans-serif;
  }
  .container .box{
    width: 100%;
    display: flex;
  }
  .box div{
    width: 100%;
  }
  
  select{
    width: 95%;
    height: 40px;
    font-size: 1.2em;
    cursor: pointer;
    background-color:rgb(145, 237, 176);
    outline: none;
    color: black;
    margin: 0.2em 0;
    padding: 0 1em;
    border-radius: 0px;
    border: none;
  }
  
  
  input{
    width: 80%;
    height: 40px;
    font-size: 1em;
    margin: 0.2em 0;
    border-radius: 0px;
    border: none;
    background: #dbdedb;
    outline: none;
    padding: 0 1em;
  }
  
  .btn{
    display:flex;
    justify-content: center;
  }
  
  button{
    width: 50%;
    height: 40px;
    background-color:#a7e5ff;
    color: #102770;
    border-radius: 0px;
    border: none;
    cursor: pointer;
    font-size: 1em;
    margin: 0.5em 0;
  
  }
```
SCRIPT.JS:
```
let select = document.querySelectorAll('.currency')
let btn = document.getElementById('btn')
let input = document.getElementById('input')
fetch('https://api.frankfurter.app/currencies')
.then(res=>res.json())
.then(res=>displayDropDown(res))

function displayDropDown(res){
  //console.log(Object.entries(res)[2][0])
  let curr = Object.entries(res)
  for(let i=0;i<curr.length;i++){
    let opt = `<option value="${curr[i][0]}">${curr[i][0]}</option>`
    select[0].innerHTML += opt
    select[1].innerHTML += opt
  }
}

btn.addEventListener('click',()=>{
  let curr1 = select[0].value
  let curr2 = select[1].value
  let inputVal = input.value
  if(curr1===curr2)
    alert("Choose different currencies")
  else
    convert(curr1,curr2,inputVal)
});

function convert(curr1,curr2,inputVal){
  const host = 'api.frankfurter.app';
  fetch(`https://${host}/latest?amount=${inputVal}&from=${curr1}&to=${curr2}`)
  .then(resp => resp.json())
  .then((data) => {
    document.getElementById('result').value = Object.values(data.rates)[0]
  });

}
```
#OUTPUT:
![image](https://github.com/ssnithyaasri/CURRENCY-CONVERTER-TASK-2/assets/119122478/0df053f2-c64c-42f5-8243-abec223a8900)



![image](https://github.com/ssnithyaasri/CURRENCY-CONVERTER-TASK-2/assets/119122478/4a0003e1-6961-4a1f-8e04-59dbc448a26c)


![image](https://github.com/ssnithyaasri/CURRENCY-CONVERTER-TASK-2/assets/119122478/418fa382-00d3-4cbe-ba7a-08ad9ea1a9fc)

![image](https://github.com/ssnithyaasri/CURRENCY-CONVERTER-TASK-2/assets/119122478/29becb53-5bb5-469d-8fd2-6074c0b62d24)

![image](https://github.com/ssnithyaasri/CURRENCY-CONVERTER-TASK-2/assets/119122478/79c1452e-f7c2-463c-a7a2-c9ec6518849d)









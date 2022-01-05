---
title: "Kata: Minimum Number of Coins"
date: 2022-01-05T22:39:47Z
---
This evening I decided to have a go at the kata ["Minimum Number of Coins"][a_src]. The first challenge in this kata is to validate the number given
which can be quite varied. The amount may be either a number or a string. If it is a string, it may or may not be prefixed with "£" or suffixed with "p". 
If it is a number, it can be either an integer or a float. If it's an integer, then it's the number of pennies. If it's a float, then the whole part of
the number is pounds and the fraction is pence. Distinguishing between these two cases is where I currently am with the kata.

As can be seen below, I had to do some work to get the formating of the return string correct. Having solved that problem, I was very pleased to see it 
passed the first set of tests. However, when I ran the full test suite it immediately failed on '4', the number 4 passed in as a string. My regex at the 
beginning is matching this as £4 rather than 4p. I have decided to pause here for the night because it is getting quite late and I have to be up early for
the Northcoders bootcamp. I have an idea of how to fudge it but might come up with something more elegant if I sleep on it.

[a_src]:https://www.codewars.com/kata/557f138eb472f5caa7000062
```
function minCoins(amount){
// use regex to capture pounds and pence
  console.log(typeof amount)
  const regex = /^£*(\d*)\.*(\d*)p*$/
  var total = 0;

  if (typeof amount === "string" && amount.match(regex)){  
    const match = amount.match(regex);
    const pounds = Number(match[1]);
    const pence = Number(match[2]);
    amount = 100*pounds+pence 
  } else if (typeof amount === "string" && !amount.match(regex)){
    return `Invalid input - enter a positive amount of money`
  }
  console.log(amount)
  if (typeof amount === "number" && amount<0){
    return `Invalid input - enter a positive amount of money`
  }
      
  if (typeof amount === "number" && amount%1!==0){    
    amount = amount.toFixed(2)*100
  }
  console.log(amount)

  const coins = {"£2 coin":0, "£1 coin":0, "50p coin":0, "20p coin":0, "10p coin":0, "5p coin":0, "2p coin":0, "1p coin":0}
  var remaining = 0;
  

  coins["£2 coin"] = Math.floor(amount/200)
  remaining = amount%200
  coins["£1 coin"] = Math.floor(remaining/100)
  remaining = remaining%100
  coins["50p coin"] = Math.floor(remaining/50)
  remaining = remaining%50
  coins["20p coin"] = Math.floor(remaining/20)
  remaining = remaining%20
  coins["10p coin"] = Math.floor(remaining/10)
  remaining = remaining%10
  coins["5p coin"] = Math.floor(remaining/5)
  remaining = remaining%5
  coins["2p coin"] = Math.floor(remaining/2)
  remaining = remaining%2
  coins["1p coin"] = Math.floor(remaining)
  
  console.log(coins)
  
  for (denomination in coins){
    if (coins[denomination] === 0){
      delete coins[denomination]
    }
  }
  console.log(coins)
  
  var returnStr = ""
  
  for (denomination in coins){
    returnStr+= `${coins[denomination]} ${denomination}, `
  }
  
  returnStr = returnStr.slice(0,returnStr.length-2)
  console.log(returnStr)
  
  //comment 1: so close!! but it wants me to pluaralise coins if there is more than 1.
  //I don't want to mess with the object bc i think it will change the order, 
  //so before we add the " and " I will split the string, pluralise where necessary,
  // and join again
  
  returnStr = returnStr.split(", ")
  console.log(returnStr)
  for (entry in returnStr){
    if (returnStr[entry][0]>1){
      returnStr[entry]+="s"
    }
  }
  returnStr = returnStr.join(", ")
  
  if (returnStr.lastIndexOf(",")>-1){
    returnStr = returnStr.split("")
    returnStr.splice(returnStr.lastIndexOf(","),2," and ")
    returnStr = returnStr.join("")
  }
   
  return returnStr;
  
} // comment 2: I have sorted the output formatting but now I'm Failing on integers-as-strings because 
  // the regex match saves it as pounds and not pence, so I need to fix the first part.
  // I'm going to add this to my blog before I tackle those changes.
```

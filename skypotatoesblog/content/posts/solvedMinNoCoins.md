---
title: "Solved Minimum Number of Coins Kata"
date: 2022-01-09T02:11:04Z
---

I eventually solved this Kata and it's the first one I have come across which I didn't enjoy doing. I found the challenge to lack any consistency in what inputs were
considered valid or invalid, and in the end it became a case of simply filtering out the edge cases through if-statements. It seemed entirely capricious as to why it
wouldn't accept .5 but would accept .16, £1p was valid but £.70p wasn't - or maybe it was. I couldn't make sense of why some were acceptable and others not.
I didn't see the point of this at all and while, at first, it was an interesting exercise in using
regex, it became clear from how ridiculous the edge cases were that regex wouldn't be enough. Simply tweaking the if-statements to get round inconsistent rules around
valid inputs wasn't a fun exercise and only served to annoy me. I'm glad I solved it, but only because I don't have to work on it anymore. I don't feel this was really
a learning experience as other katas have been.

```
function minCoins(amount){

  console.log(typeof amount)
  const regex = /(^£*)(\d*\.*\d*)(p*)$/     
  if (typeof amount === "string" && amount.match(regex)){  


  const match = amount.match(regex);
  const sign = match[1];
  const pennies = match[3];
      console.log("sign: "+sign)
      console.log(match)
    amount = (match[2])
    
    if (match[3].length>1){
      console.log("You are here 1")
      return 'Invalid input - enter a positive amount of money'
    }
    
    if (sign.length>1){
      return 'Invalid input - enter a positive amount of money'
    }
    
    if (amount.indexOf(".")!==amount.lastIndexOf(".")){
      return 'Invalid input - enter a positive amount of money'
    }
    
    const dot = match[2].indexOf(".")
    const b4dot = match[2].slice(0, dot)
    const sliceDot = match[2].slice(dot+1)
    if ( match[2]<1 && match[2].indexOf(".")>-1 && match[1]==="" && sliceDot.length<2){
      console.log("You are here 0")
      return 'Invalid input - enter a positive amount of money'      
    }
    
    if (sign === "£" && pennies ==="p" && b4dot.length <1 && dot!== -1){
      return 'Invalid input - enter a positive amount of money'     
    }
 
    amount = Number(match[2]) 
       
    if (sign==="£" && amount%1===0){
      amount *= 100
    }
    

    
  } else if (typeof amount === "string" && !amount.match(regex)){
    return `Invalid input - enter a positive amount of money`
  }
  console.log("am:"+amount)

  console.log("you are here 0," +typeof amount)
  if (typeof amount === "number" && amount%1!==0){    
    console.log("you are here 1")
    amount = amount.toFixed(2)*100
  }
  console.log("amount"+amount)
  if (typeof amount === "number" && amount<1){
    return `Invalid input - enter a positive amount of money`
  }
      
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
  
  returnStr = returnStr.split(", ")
  console.log(returnStr)
  for (entry in returnStr){
    split=returnStr[entry].split(" ")  
    console.log(split)
    console.log(returnStr[entry])
    if (split[0]>1){
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
  }
```
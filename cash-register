function checkCashRegister(price, cash, cid) {
  var change=cash-price;
  var change_in_currency=[];
  var total=0;
  var currency = {
    "PENNY": 0.01, 
    "NICKEL": 0.05,
    "DIME": 0.1, 
    "QUARTER": 0.25,
    "ONE": 1, 
    "FIVE": 5, 
    "TEN": 10, 
    "TWENTY": 20,
    "ONE HUNDRED": 100
  }

  for(var i=cid.length-1; i>=0; --i)
    total+=cid[i][1];
  if(total==change)
    return {status: "CLOSED", change: cid};
  else if(change>total)
    return {status: "INSUFFICIENT_FUNDS", change: []};

  for(var i=cid.length-1; i>=0; --i) {
    if(change>=currency[cid[i][0]]) {
      var temp=cid[i][1];
      if(change<temp)
        temp=Math.floor(change/currency[cid[i][0]])*currency[cid[i][0]];
      change=(change-temp).toFixed(2);
      change_in_currency.push([cid[i][0], temp]);
    }
    if(change==0) break;
  }

  if(change>0) 
    return {status: "INSUFFICIENT_FUNDS", change: []};
  else
    return {status: "OPEN", change: change_in_currency};
}

checkCashRegister(19.5, 20, [["PENNY", 0.5], ["NICKEL", 0], ["DIME", 0], ["QUARTER", 0], ["ONE", 0], ["FIVE", 0], ["TEN", 0], ["TWENTY", 0], ["ONE HUNDRED", 0]])

# Javascript Useful Snippets

## Objects

<details><summary>Generating unique IDs for objects</summary>

  - Use cases: 
    - Object queries in REST APIs
  
  ```js
  let store = {
    nextId: 1,
    cache: {},
    add: function(obj){
      if(!obj.id){
        obj.id = this.nextId++;
        this.cache[obj.id] = obj;
        return true;
      }
    }
  }

  const obj1 = {name: 'John'};
  const obj2 = {name; 'Doe'};
  
  store.add(obj1);
  store.add(obj2);
  
  console.log(Object.values(store.cache)); // output: [ { name: 'John', id: 1 }, { name: 'Doe', id: 2 } ]
  ```
</details>

## Performance

<details><summary>Self-memoization (caching computation results)</summary>
  
  - Memoization: process of building a function that's capable of remembering its previously computed values
  - When function invocation occurs for same set of args, then you can return previously stored result instead of running the function again
  - Some Use cases: 
    - animations
    - data queries
    - time-consuming math operations
  - Function pattern:
  ```js
  function heavyOperation(arg){
    if(!heavyOperation.savedResults)
      heavyOperation.savedResults = {};
  
    if(heavyOperation.savedResults[arg] !== undefined)
      return heavyOperation.savedResults[arg];
  
    let results = defaultValue;
    // execute function's heavy operation here
  
  
    return heavyOperation.savedResults[arg] = result
  }
  ```
  
  - Example:
  ```js
  function isPrime(arg){
    // Create the cache if doesn't exist
    if(!isPrime.resultsCache){
      isPrime.resultsCache = {};
    }
  
    // if we already calculated for the same arg before, 
    //   then just retrieve its results and skip running the function again
    if(isPrime.resultsCache[arg] !== undefined) 
      return isPrime.resultsCache[arg];
    
    // 1 is not a prime, so we set this
    let argIsPrime = arg !== 1;
  
    // Algorithm for determining if number is prime
    for(let i = 2; i lessThan arg; i++){
      if(arg % i === 0){
        argIsPrime = false;
        break;
      }
    }
  
    // Set the results into the cache and return primeStatus
    return isPrime.resultsCache[arg] = argIsPrime;
  }
  
  console.log(isPrime(2));  // true
  console.log(isPrime(4));  // false
  console.log(isPrime(17)); // true
  console.log(isPrime(1));  // false
  ```
  
</details>
  
  

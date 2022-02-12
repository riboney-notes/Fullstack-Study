# Javascript Features

## Compatibility

**Transpilation**
  -  using a tool to convert source code of a program from newer syntax to older syntax to solve forwards-compatibility problems (problems from using new features not able to run on older engines)
  -  Ex:
  ```js
      // original code
      if (something){
        let x = 3;
        console.log(x);

      // transpiled code
      var x$0;
      if(something){
        x$0 = 3;
        console.log(x$0);
  ```
 
**Polyfills**
  - providing definitions for newer API methods that don't exists in older engines so that the definition implements the new API and allows the code to work
  - Ex: 
  ```js
     // polyfill for the ES2019 `.finally()` method that you would find in a browswer that doesn't impleement ES2019
     if (!Promise.prototype.finally) {
     Promise.prototype.finally = function f(fn){
          return this.then(
              function t(v){
                  return Promise.resolve( fn() )
                      .then(function t(){
                          return v;
                      });
              },
              function c(e){
                  return Promise.resolve( fn() )
                      .then(function t(){
                          throw e;
                      });
              }
          );
      };
     }
   ```

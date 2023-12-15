# Javascript-Notes
Observations on my Journey from C# into JavaScript

## Avoid funny behavior:
 - ```parseInt('2') // only works if no text```

## ES6 template literal form:
 - ```console.log(`${welcomeMessage1} ${name} ${welcomeMessage2}`); // backticks, $ on each, all "" '' in backticks allowed```

## Math accuracy pitfall:
 - ```0.362 * 100; 			 // 36.199999999999996 // (expected: 36.2)```
 - ```(Math.round(0.362 * 1000) / 10); // 36.2 // (workaround 1)```
 - ```0.362 * 1000 / 10; 		 // 36.2 // (workaround 2)```

## C# to JS:
 - `dynamic` - `let`
 - `double` - `float`
 - `true` - number `1` to be equal to `true`
 - `null` - `null`
 - not initialized - `undefined``
 - `Console.WriteLine();` - console.log();
 - `@"..."` - ``` `...` ```
 - ```$"...{var1}...{var2}."``` - ``` `...${var1}...${var2}.` ```

## Objects and collections(array):
 - ```js
   let object = {
     key: 'someValue',
     anything: 'stringType',
     newObject: {
       childObject: 1.1,
       collection: [1, 2, 3]
     }
   }; // no = just : for the properties (!)
   ```
 - ```js
   let objectAndMixedArray = [
     { type: 'objectInArray0', position: 0, aggregatedIn: 'objectArray' },
     { type: 'objectInArray1', position: 1, aggregatedIn: 'objectArray' },
     [1, 2, 3],
     [a, b, c],
     'this is a mixed array'
   ]; // no object names needed since array enumerated, use = to initialize (!)
   ```
 - ```js
   console.log(object.newObject.collection); // [1, 2, 3]
   delete object.anything;
   console.log(object.anything); // undefined
   /* if the property name is not a valid identifier (doesn’t start with a letter), it's only accessible through obj[_property_name] but not obj.property_name: */
   ```
 - ```js
   console.log(objectAndMixedArray[3][1]); // b
   // https://www.codingame.com/playgrounds/6181/javascript-arrays---tips-tricks-and-examples
   ```

## Primitive types vs. complex types (C# `value(struct)` vs. `object(class)`):
 - value(`struct`) - `primitive` type (`boolean`, `number`, `string`, `null`, undefined)
 - object(`class`) - `complex` type (`array`, *`customClasses`*)
 - string(`object`) - string(`primitive`)
 - ```js
   let aPrim = 1;
   let bPrim = aPrim; // copy value directly to stack
   aPrim = 0;
   ```
 - ```js
   console.log(b); // 1
   let firstComplex = {
     property0: firstObject,
     someBool: true
   }
   let secondComplex = firstComplex; // copies only reference to heap-storage-place
   firstComplex.someBool = false;
   console.log(secondComplex); // { property0: firstObject, someBool: false }
   ```

## Dynamic type determination via `typeof variable` (C# `variable.GetType()`):
 - ```js
   let dynamicType = 10;
   console.log(typeof dynamicType); // number
   dynamicType = 'some string';
   console.log(typeof dynamicType); // string
   ```

## C#(static) vs. JS(dynamic) naming:
 - describe `var` **contents** use only - make `var` **containing data type** obvious
 - **`MethodPascalCase()`** - **`methodCamelCase()`**

## Semicolon syntax JS:
 - ```js
   class var obj = {};
   ```

## Conditionals & Comparisons C# vs. JS:
 - `==` - `===`	// `==` in JS `parses` the `type` and thus ignores type-indifference
 - `!=` - `!==`	// `5 != '5'` => `false` (same **content**) `5 !== '5'` => `true` (other **type**)
 - ```js
   if ('') rePromptUser(); else processForm(); // for user input that is only string type
   ```
 - `===` **compares reference** pointers for objects, **not** their **content** respectively

## Assignment via logic operators:
 - ```js
   let name = 'FirstName' || 'LastName'   // 'FirstName'
   let result = denominator && (6/denominator)   // if denominator == 0 => result = 0 (avoids division by zero)
   ```

## Loop specialties:
 - ```js
   let veggies = ["tomato", "cucumber", "potato"]; let text3 = ""; 
   let a = 0;
   for (/*let a = 0*/ ; veggies[a];) text3 +=			// ';' remains
      (veggies.indexOf(veggies[a]) ? ", " : "") + veggies[a++];	// skip first in array via 'indexOf'
   ```
   (here `(a ? ", " : "") + veggies[a++];` would have done the trick as well)


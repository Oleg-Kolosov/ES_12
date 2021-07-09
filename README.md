# String.prototype.replaceAll()

```javascript
    // Task is to change all rabbits to monkeys
    const word = '🐰🐰🐰🐼🐼🐼'

    // Problem
    word.replace('🐰', '🦧')    // '🦧🐰🐰🐼🐼🐼'

    // Solution with regular exspression
    word.replace(/🐰/g, '🦧')   // '🦧🦧🦧🐼🐼🐼'

    // ES 12
    word.replaceAll('🐰', '🦧') // '🦧🦧🦧🐼🐼🐼'
```

# Logical assigment operators 

### ??=

```javascript
    let userName;

    // If statemets
    if(userName === undefined || userName === null){
        userName = 'Kate'
    }

    // Nullish coalescing operator
    username = userName ?? 'Kate'

    // ES 12 logical assignment operator
    username ??= 'Kate'
```

### &&=

```javascript
    let person = 'Kate'

    // If statement
    if(person){ 
        person = 'Kate Lonsible'
    }
    // Logical operator
    person = person && 'Kate Lonsible'

    // ES 12 logical assignment operator
    person &&= 'Kate Lonsible'
```

### ||=

```javascript
    let userName = ''

    // If statement
    if(!userName){
        userName = 'Kate'
    }

    // Logical operator
    userName = userName || 'Kate'

    // ES 12 logical assignment operator
    userName ||= 'Kate'
```

### Separators for numeric literals

```javascript
    const WORTH_1 = 91_000_000_000
    const WORTH_2 = 91000000000

    WORTH_1 === WORTH_2 // true
```

### Promise.any() 
##### Promise combinator that short-circuits when an input value is fulfilled

```javascript
    const createPromise = (value, delay) => {
        return new Promise(resolve => {
            setTimeout(() => {
                resolve(value);
            }, delay);
        });
    };

    let car = createPromise('car driving time', 1000);
    let train = createPromise('train driving time', 6000);
    let byke = createPromise('byke driving time', 3000);

    Promise.any([car, train, byke]).then(value => {
        console.log(value); // car driving time
    });
```

### AggregateError 
##### a new Error type to represent multiple errors at once

```javascript
    const createPromise = (value, delay) => {
        return new Promise((resolve, reject) => {
            setTimeout(() => {
                reject(value); // change resolve to reject
            }, delay);
        });
    };

    let car = createPromise('car driving time', 1000);
    let train = createPromise('train driving time', 2000);
    let byke = createPromise('byke driving time', 500);

    Promise.any([car, train, byke]).catch(err => console.log(err));

    // ! AggregateError: All promises were rejected
```

### WeakRef
##### is an object that is used to refer to a target object without preserving it from garbage collection.

```javascript
    // The WeakRef constructor creates a WeakRef instance for the given target object:
    let ref = new WeakRef(someObject); 

    // The deref method returns the WeakRef instance's target object, or undefined 
    // if the target object has been reclaimed:
    targetOrUndefined = ref.deref();
```


### FinalizationRegistry
##### A finalization registry provides a way to request that a cleanup callback get called at some point after an object registered with the registry has been reclaimed (garbage collected)

```javascript
    // A FinalizationRegistry instance (a "registry") lets you get cleanup callbacks 
    // after objects registered with the registry are reclaimed. You create the 
    // registry passing in the callback:

    const registry = new FinalizationRegistry(heldValue => {
        // ....
    });

    // Then you register any objects you want a cleanup callback for by calling the 
    // register method, passing in the object and a held value for it:

    registry.register(theObject, "some value");
```
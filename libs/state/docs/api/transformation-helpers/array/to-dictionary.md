---
filename: toDictionary
---

# toDictionary

Converts an array of objects to a dictionary {[key: string]: T}.
Accepts array T[] and key of type string, number or symbol as inputs.

_Example_

```TypeScript
const creatures = [{id: 1, type: 'cat'}, {id: 2, type: 'dog'}, {id: 3, type: 'parrot'}];

const creaturesDictionary = toDictionary(creatures, 'id');

// creaturesDictionary will be:
// {
//  1: {id: 1, type: 'cat'},
//  2: {id: 2, type: 'dog'},
//  3: {id: 3, type: 'parrot'}
// };
```

_Example_

```TypeScript
// Usage with RxState

export class ListComponent {

   readonly convertToDictionary$ = new Subject();

   constructor(private state: RxState<ComponentState>) {
     // Reactive implementation
     state.connect(
       'creaturesDictionary',
       this.convertToDictionary$,
       ({ creatures }) => {
           return toDictionary(creatures, 'id');
       }
     );
   }

   // Imperative implementation
   convertToDictionary(): void {
       this.state.set({ creaturesDictionary: toDictionary(this.state.get().creatures, 'id'});
   }
}
```

## Signature

```TypeScript
function toDictionary<T extends object>(source: T[], key: | OnlyKeysOfSpecificType<T, number>
    | OnlyKeysOfSpecificType<T, string>
    | OnlyKeysOfSpecificType<T, symbol>): { [key: string]: T }
```

## Parameters

### source

##### typeof: T[]

### key

##### typeof: | OnlyKeysOfSpecificType&#60;T, number&#62;

     | OnlyKeysOfSpecificType&#60;T, string&#62;
     | OnlyKeysOfSpecificType&#60;T, symbol&#62;

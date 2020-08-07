---
filename: toggle
---

# toggle

Toggles a boolean property in the object.
Accepts object of type T and key value of which is boolean.
Toggles the property and returns a shallow copy of an object, while not mutating the original one.

_Example_

```TypeScript
const state = {items: [1,2,3], loading: true};

const updatedState = toggle(state, 'loading');

// updatedState will be:
// {items: [1,2,3], loading: false};
```

_Example_

```TypeScript
// Usage with RxState

export class ListComponent {
   readonly loadingChange$ = new Subject();

   constructor(
     private state: RxState<ComponentState>
   ) {
     // Reactive implementation
     state.connect(
       this.api.loadingChange$,
       (state, _) => {
           return toggle(state, 'isLoading');
       }
     );
   }

   // Imperative implementation
   toggleLoading(): void {
     this.set(toggle(state, 'isLoading'));
   }
}
```

## Signature

```TypeScript
function toggle<T extends object>(object: T, key: OnlyKeysOfSpecificType<T, boolean>): T
```

## Parameters

### object

##### typeof: T

### key

##### typeof: OnlyKeysOfSpecificType&#60;T, boolean&#62;

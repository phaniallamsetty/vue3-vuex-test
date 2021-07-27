# vue3-vuex-test

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).


### About VueX
VueX is a library which helps us manage the state of a Vue app.
Any data can be transmitted across components using props. However, if the nesting of the components is too complex, it could become confusin and difficult to keep track of the changes made to the props field.

Consider the following component diagram:

                                                                C1
                                                /                               \
                                            **C2**                              C3
                                        /       |       \               /       |       \
                                        C4      C5      C6              C7      C8      C9
                                        |                                               |
                                        C10                                             C11
                                        |                                               |
                                      *C12*                                           *C13*


Consider a props field in the component C2. If the same field needed to be used by C12, it can be passed down in the hierarchy to the child component
But if the same field was required in C13, it would be very difficult to pass the props since data can be transmitted up to the parent or down to the child components. The only way to pass the data to C13 would be to pass it all the way up to C1 and then down to C13. This gets tediuos as the application grows in size and complexity. VueX solves this problem. The *state* is housed separately from the component chain and is accessible globally to all the components.

#### state
state object essentially holds the state elements in the app. These objects are made available throughout the application through vuex. In this app, the state objects are included in src\store\index.ts

#### mapState
mapState lets you map the state into your component. This will come in handy if there are quite a few elements in the state. You can decide which objects to map to the component using mapState(). Refer to 'computed()' in Counter.vue for an example.

#### mutations
mutations are methods defined in the store which lets you make changes to the state elements. Just like the state, these elements are also available throughout the app. In this example, mutations are defined in src\store\index.ts. One restriction for mutations is that they cannot have asynchronous methods. Use 'actions' for async code.

#### mapMutations
Works in the same way as mapState. As the name suggests, it is used to map the mutations defined in the store to be used inside a component. Refer to 'methods' in Counter.vue.

#### actions
Lets you call a mutation asynchronously. Since mutations cannot have async methods, the async calls are performed by actions and the mutations can then be called by the async methods to perform any other operations. In this example, actions are defined along with state and mutations in src\store\index.ts

#### mapActions
Lets you map actions defined in the store to the component to be used there.

#### getters
Gives you a way of getting the data in the state with manipulations done on it without actually changing the state.

#### mapGetters
Lets you map getters from store to a component.

#### modules
A way of making the state available to different modules. Modules also let the user maintain different states specific to each module thereby enabling separation of concerns.


# The Component Lifecycle
 Each component in React has a lifecycle which you can monitor and manipulate during its three main phases.
 The three phases are: Mounting, Updating, and Unmounting.

 ## The component lifecycle goes through the following phase
 
- Mounting
- Updating
- Unmounting

## Mounting
The component rendered to the DOM for the first time. This is called mounting. These methods are called in the following order when an instance of a component is being created and inserted into the DOM.

- constructor()
- static getDerivedStateFromProps() rarely case use
- render()
- componentDidMount()

## Updating
An update can be caused by changes to props or state. These methods are called in the following order when a component is being re-rendered

- static getDerivedStateFromProps() rarely case use
- shouldComponentUpdate() rarely case use
- render()
- getSnapshotBeforeUpdate() rarely case use
- componentDidUpdate()

## Unmounting
When component removed from DOM. This is called unmounting. Below method is called in this phase.

- componentWillUnmount()

## Component Lifecycle Diagram

![lifecycle-diagram](https://user-images.githubusercontent.com/69896600/155375420-5630aeec-f66f-445a-a45d-c75717b2efea.png)



# Lifecycle Methods

## constructor()
The constructor for a React component is called before it is mounted. The constructor call only once in whole lifecycle. You and set initial value for this component.

Constructors are only used for two purposes 1. Initializing local state by assigning an object to this.state 2. Binding event handler methods to an instance.

```javascript
constructor(props){
	super(props);
	this.state = {qty: this.props.qty}
	this.clickHandling = this.clickHandling.bind(this);
}
```

## static getDerivedStateFromProps()

It is invoked before calling render method. This method is used when state depends on props, whenever props is changed, then state automatically will be changed. getDerivedStateFromProps method use for both phase mounting and updating of the component. If null is returned then nothing is changed in the state.

```javascript

static getDerivedStateFromProps(props, state) {
	if(props.qty !== state.qty) {
	  return {qty: props.qty}
	}
	return null;
}

```
## render()

This method is the only required method in a class component. The render() function should be pure, meaning that it does not modify component state, which means it returns the same output each time it’s invoked.

```javascript


render(){
    return(
      <div>
        <h2>Cart Items ({this.state.qty})</h2>
      </div>
    )
  }

}

```
## componentDidMount()
This is invoked immediately after the component is mounted. If you load data using api then it right place for request data using api.

```javascript
componentDidMount() {
    console.log('Execute this method after component render');
}
```

## shouldComponentUpdate()
This is invoked before rendering when new props or state are being received. This methods return true or false according the component re-render or skipped. By default, this method returns true. This method is not called for the initial render.

```javascript

shouldComponentUpdate(nextProps, nextState) {
    if(this.props.qty !== nextProps.qty) {
      console.log('should component update');
      return true;
    }
    return false;
}

```
## componentDidUpdate()
This method immediately executed on the DOM when the component has been updated. Update occurs by changing state and props. This method is not called for the initial render. This is a good place for compare the current props to previous props.

```javascript


componentDidUpdate(prevProps, prevState){
    if(this.props.productId !== prevProps.productId){
      console.log('component updated');
    }
}


```

## componentWillUnmount()
This method immediately executed when the component is unmounted and destroy from the DOM. Means this method is called when a component is being removed from the DOM.

```javascript


componentDidUpdate(prevProps, prevState){
    if(this.props.productId !== prevProps.productId){
      console.log('component updated');
    }
}


```
Posted By: @mian-ali `(Ali Ahmad)`

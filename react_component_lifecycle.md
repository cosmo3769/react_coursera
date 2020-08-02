# React Components Lifecycle

React Component goes through the following lifecycle stages(it is the heirarchy of the particular code being invoked by react application)

**MOUNTING**

**UPDATING**

**UNMOUNTING**

## MOUNTING lifecycle methods

Called when an instance of a component is being created and inserted into the DOM

```
constructor()
```

```
getDerivedStateFromProps()
```

```
render()
```

```
componentDidMount()
```

***componentDidMount() will be used when you need to execute something after the component gets added into the DOM***

***when our React application gets created, the App.js will mount the menu component into its view, and so at that point the menu component gets created and added into our overall DOM for our React application***

## changes

**MenuComponent.js**

```
import React, { Component } from 'react';
import { 
  Card, 
  CardImg, 
  CardImgOverlay, 
  CardText, 
  CardBody,
  CardTitle 
} from 'reactstrap';


class Menu extends Component {
  constructor(props) {
    super(props);

    this.state = {
        selectedDish: null
    }
    console.log('Menu component constructor is invoked');
}

componentDidMount() {
  console.log('Menu component componentDidMount is invoked');
}

onDishSelect(dish) {
  this.setState({ selectedDish: dish});
}

renderDish(dish) {
  if (dish != null)
      return(
          <Card>
              <CardImg top src={dish.image} alt={dish.name} />
              <CardBody>
                <CardTitle>{dish.name}</CardTitle>
                <CardText>{dish.description}</CardText>
              </CardBody>
          </Card>
      );
  else
      return(
          <div></div>
      );
}

      render() {
        const menu = this.props.dishes.map((dish) => {
            return (
              <div  className="col-12 col-md-5 m-1">
                <Card key={dish.id}
                  onClick={() => this.onDishSelect(dish)}>
                  <CardImg width="100%" src={dish.image} alt={dish.name} />
                  <CardImgOverlay>
                      <CardTitle>{dish.name}</CardTitle>
                  </CardImgOverlay>
                </Card>
              </div>
            );
        });

        console.log('Menu component render is invoked');

        return (
          <div className="container">
              <div className="row">
                  {menu}
              </div>
              <div className="row">
                <div  className="col-12 col-md-5 m-1">
                  {this.renderDish(this.state.selectedDish)}
                </div>
              </div>
          </div>
      );
  }
}

export default Menu;
```

###### heirarchy

Menu component constructor is invoked

Menu component render is invoked

Menu component componentDidMount is invoked

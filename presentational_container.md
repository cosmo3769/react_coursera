# Presentational and Container Components

## component types

It can be classified based how theu are used-->

Presentational(for rendering the view based on the props that they are passed in) vs Container(make use of presentational components and pass props to them and they are responsible for storing the state)

Skinny(purely responsible for rendering the view) vs Fat(having a lot more information being tracked there in the form of state)

Dumb vs Smart

Stateless vs Stateful

###### presentational component

These are mostly for markup and styles, how data is presented on screen(rendering the view to the screen). We passed that selected dish details through props to the dish detail components. They don't maintain their own local state.

###### container component

These are responsible for tracking the state or at least a part of the state of our application. So, they are responsible for making things work. So, they are more worried about fetching the data, say for example, from a server and then using the data within the application or to set up the state or maybe taking care of updating the state in response to any user interactions on the screen or updating the states based upon the data sent back from the server. They make use of presentational components for actually rendering the view. So, they could wrap the information sent in by the presentational components in their own wrapping divs within the container component in order to position the views that are rendered by the presentational component on the screen, but beyond that they will not be responsible for actually constructing the views.
They delegate that responsibility to the presentational component, and also they are responsible for providing the data to the presentational component in the form of props that can be passed in to the child component there.

## changes

src->components->MainComponent.js

**MainComponents.js**--container component

```
import React, { Component } from 'react';
import { Navbar, NavbarBrand } from 'reactstrap';
import Menu from './MenuComponent';
import DishDetail from './DishdetailComponent';
import { DISHES } from '../shared/dishes';

class Main extends Component {

  constructor(props) {
    super(props);
    this.state = {
        dishes: DISHES,
        selectedDish: null
    };
  }

  onDishSelect(dishId) {
    this.setState({ selectedDish: dishId});
  }

  render() {
    return (
      <div>
        <Navbar dark color="primary">
          <div className="container">
            <NavbarBrand href="/">Ristorante Con Fusion</NavbarBrand>
          </div>
        </Navbar>
        <Menu dishes={this.state.dishes} onClick={(dishId) => this.onDishSelect(dishId)} />
        <DishDetail dish={this.state.dishes.filter((dish) => dish.id === this.state.selectedDish)[0]} />
      </div>
    );
  }
}

export default Main;
```


# react components

## changes 

public->assets->images->put all the images in here

src->components->MenyComponent.js

**MenuComponent.js**

```
import React, { Component } from 'react';
import { Media } from 'reactstrap';

class Menu extends Component {
    constructor(props) {
        super(props);
        this.state = {
            dishes: [
                {
                  id: 0,
                  name:'Uthappizza',
                  image: 'assets/images/uthappizza.png',
                  category: 'mains',
                  label:'Hot',
                  price:'4.99',
                  description:'A unique combination of Indian Uthappam (pancake) and Italian pizza, topped with Cerignola olives, ripe vine cherry tomatoes, Vidalia onion, Guntur     chillies and Buffalo Paneer.'                        
                },
               {
                  id: 1,
                  name:'Zucchipakoda',
                  image: 'assets/images/zucchipakoda.png',
                  category: 'appetizer',
                  label:'',
                  price:'1.99',
                  description:'Deep fried Zucchini coated with mildly spiced Chickpea flour batter accompanied with a sweet-tangy tamarind sauce'                        
                },
               {
                  id: 2,
                  name:'Vadonut',
                  image: 'assets/images/vadonut.png',
                  category: 'appetizer',
                  label:'New',
                  price:'1.99',
                  description:'A quintessential ConFusion experience, is it a vada or is it a donut?'
               },
              {
                    id: 3,
                    name:'ElaiCheese Cake',
                    image: 'assets/images/elaicheesecake.png',
                    category: 'dessert',
                    label:'',
                    price:'2.99',
                    description:'A delectable, semi-sweet New York Style Cheese Cake, with Graham cracker crust and spiced with Indian cardamoms'                        }
              ],
          };
      }

      render() {
        const menu = this.state.dishes.map((dish) => {
            return (
              <div key={dish.id} className="col-12 mt-5">
                <Media tag="li">
                  <Media left middle>
                      <Media object src={dish.image} alt={dish.name} />
                  </Media>
                  <Media body className="ml-5">
                    <Media heading>{dish.name}</Media>
                    <p>{dish.description}</p>
                  </Media>
                </Media>
              </div>
            );
        });

        return (
          <div className="container">
            <div className="row">
              <Media list>
                  {menu}
              </Media>
            </div>
          </div>
        );
    }
}

export default Menu;
```

**App.js**

```
import React from 'react';
import logo from './logo.svg';
import './App.css';

import { Navbar, NavbarBrand } from 'reactstrap';
import Menu from './components/MenuComponent';


function App() {
  return (
    <div>
      <Navbar dark color="primary">
          <div className="container">
            <NavbarBrand href="/">Ristorante Con Fusion</NavbarBrand>
          </div>
      </Navbar>
      <Menu />
    </div>
  );
}

export default App;
```

App.css->delete all the code

## state

Each component can store it's own local information in it's state.

private and fully controlled by the component

can be passed as props to children

only class components can have local state

state is declared within the constructor of the class component

state should only be modified using setState(), when modified the changes will happen to the original state and the information stored in will be modified.

## props

jsx attributes are passed into a component as a single object

available in the component as props

can pass in multiple attributes

cannot modify props within the component

***parent component having state which is storing information can be passed on to the child component with the use of props in the form of attributes that you are specifying to the jsx statements.***

```
<Menu dishes={this.state.dishes}/>
```

Here the dishes are available as props within the Menu Component and can be accessed as this.props.dishes

```
<Dishdetail dish={this.state.dish} comments={this.state.comments}/>
```

Here dish is available as props within the Dishdetail Component and can be accessed as this.props.dish and comments as this.props.comments

## Handling Events

It's similar to the way you handle events on DOM elements

use camelCase to specify events

pass function as the event handler

```
<Card onClick={() => this.onDishSelect(dish)}>
```

## Lifting state up

sometimes several componets may share the same data, changes to data in one component needs to be reflected to another component, best to move the shared state to a common ancestor component so every component can share the same data at one go

In previous changes made, **menu** component was being used by the **App** component in order to render the list of dishes. So the **App** component becomes the parent for the **menu** component, So if there are other components that will share the same state information as the **menu** component, instead of storing the state infoemation in the menu component, we can lift the state up to the **App** component and make it available to all other components that are children of the **App** component through props.

## changes

src->shared->dishes.js

**dishes.js**

```
export const DISHES =
    [
        {
        id: 0,
        name:'Uthappizza',
        image: 'assets/images/uthappizza.png',
        category: 'mains',
        label:'Hot',
        price:'4.99',
        description:'A unique combination of Indian Uthappam (pancake) and Italian pizza, topped with Cerignola olives, ripe vine cherry tomatoes, Vidalia onion, Guntur chillies and Buffalo Paneer.',
        comments: [
            {
            id: 0,
            rating: 5,
            comment: "Imagine all the eatables, living in conFusion!",
            author: "John Lemon",
            date: "2012-10-16T17:57:28.556094Z"
            },
            {
            id: 1,
            rating: 4,
            comment: "Sends anyone to heaven, I wish I could get my mother-in-law to eat it!",
            author: "Paul McVites",
            date: "2014-09-05T17:57:28.556094Z"
            },
            {
            id: 2,
            rating: 3,
            comment: "Eat it, just eat it!",
            author: "Michael Jaikishan",
            date: "2015-02-13T17:57:28.556094Z"
            },
            {
            id: 3,
            rating: 4,
            comment: "Ultimate, Reaching for the stars!",
            author: "Ringo Starry",
            date: "2013-12-02T17:57:28.556094Z"
            },
            {
            id: 4,
            rating: 2,
            comment: "It's your birthday, we're gonna party!",
            author: "25 Cent",
            date: "2011-12-02T17:57:28.556094Z"
            }
        ]                        },
        {
        id: 1,
        name:'Zucchipakoda',
        image: 'assets/images/zucchipakoda.png',
        category: 'appetizer',
        label:'',
        price:'1.99',
        description:'Deep fried Zucchini coated with mildly spiced Chickpea flour batter accompanied with a sweet-tangy tamarind sauce',
        comments: [
            {
            id: 0,
            rating: 5,
            comment: "Imagine all the eatables, living in conFusion!",
            author: "John Lemon",
            date: "2012-10-16T17:57:28.556094Z"
            },
            {
            id: 1,
            rating: 4,
            comment: "Sends anyone to heaven, I wish I could get my mother-in-law to eat it!",
            author: "Paul McVites",
            date: "2014-09-05T17:57:28.556094Z"
            },
            {
            id: 2,
            rating: 3,
            comment: "Eat it, just eat it!",
            author: "Michael Jaikishan",
            date: "2015-02-13T17:57:28.556094Z"
            },
            {
            id: 3,
            rating: 4,
            comment: "Ultimate, Reaching for the stars!",
            author: "Ringo Starry",
            date: "2013-12-02T17:57:28.556094Z"
            },
            {
            id: 4,
            rating: 2,
            comment: "It's your birthday, we're gonna party!",
            author: "25 Cent",
            date: "2011-12-02T17:57:28.556094Z"
            }
        ]
        },
        {
        id: 2,
        name:'Vadonut',
        image: 'assets/images/vadonut.png',
        category: 'appetizer',
        label:'New',
        price:'1.99',
        description:'A quintessential ConFusion experience, is it a vada or is it a donut?',
        comments: [
            {
            id: 0,
            rating: 5,
            comment: "Imagine all the eatables, living in conFusion!",
            author: "John Lemon",
            date: "2012-10-16T17:57:28.556094Z"
            },
            {
            id: 1,
            rating: 4,
            comment: "Sends anyone to heaven, I wish I could get my mother-in-law to eat it!",
            author: "Paul McVites",
            date: "2014-09-05T17:57:28.556094Z"
            },
            {
            id: 2,
            rating: 3,
            comment: "Eat it, just eat it!",
            author: "Michael Jaikishan",
            date: "2015-02-13T17:57:28.556094Z"
            },
            {
            id: 3,
            rating: 4,
            comment: "Ultimate, Reaching for the stars!",
            author: "Ringo Starry",
            date: "2013-12-02T17:57:28.556094Z"
            },
            {
            id: 4,
            rating: 2,
            comment: "It's your birthday, we're gonna party!",
            author: "25 Cent",
            date: "2011-12-02T17:57:28.556094Z"
            }
        ]
        },
        {
        id: 3,
        name:'ElaiCheese Cake',
        image: 'assets/images/elaicheesecake.png',
        category: 'dessert',
        label:'',
        price:'2.99',
        description:'A delectable, semi-sweet New York Style Cheese Cake, with Graham cracker crust and spiced with Indian cardamoms',
        comments: [
            {
            id: 0,
            rating: 5,
            comment: "Imagine all the eatables, living in conFusion!",
            author: "John Lemon",
            date: "2012-10-16T17:57:28.556094Z"
            },
            {
            id: 1,
            rating: 4,
            comment: "Sends anyone to heaven, I wish I could get my mother-in-law to eat it!",
            author: "Paul McVites",
            date: "2014-09-05T17:57:28.556094Z"
            },
            {
            id: 2,
            rating: 3,
            comment: "Eat it, just eat it!",
            author: "Michael Jaikishan",
            date: "2015-02-13T17:57:28.556094Z"
            },
            {
            id: 3,
            rating: 4,
            comment: "Ultimate, Reaching for the stars!",
            author: "Ringo Starry",
            date: "2013-12-02T17:57:28.556094Z"
            },
            {
            id: 4,
            rating: 2,
            comment: "It's your birthday, we're gonna party!",
            author: "25 Cent",
            date: "2011-12-02T17:57:28.556094Z"
            }
        ]
        }
    ];
 ```
 
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

**App.js**

```
import React from 'react';
import logo from './logo.svg';
import './App.css';

import { Navbar, NavbarBrand } from 'reactstrap';
import Menu from './components/MenuComponent';
import { DISHES } from './shared/dishes';


class App extends Component {
  constructor(props) {
    super(props);
    this.state = {
      dishes: DISHES
    };
  }
  render() {
    return(
    <div>
      <Navbar dark color="primary">
          <div className="container">
            <NavbarBrand href="/">Ristorante Con Fusion</NavbarBrand>
          </div>
      </Navbar>
      <Menu dishes={this.state.dishes} />
    </div>
  );
}
}

export default App;
```

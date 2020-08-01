# REACT

React is a javascript library/framework for building user interfaces.

**DECLARATIVE**

*It hels to design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes. This declarative views make your code more predictable and easier to debug.*

**COMPONENT BASED**

*We can easily build components that manage their own state, then compose them to make complex UIs. Since component logic is written in JavaScript instead of templates, you can easily pass rich data through your app and keep state out of the DOM.*

**Learn Once, Write Anywhere**

*We don’t make assumptions about the rest of your technology stack, so you can develop new features in React without rewriting existing code. React can also render on the server using Node and power mobile apps using React Native.*

###### setup

install create-react-app globally(via terminal command)

```
npx install -g create-react-app
```

Go to any directory where you wanna create react app(via terminal command), this will make a running react app skeleton.

```
create-react-app my-app
```

This will start the react app server and the frontend part will start showing in the browser at port 3000 as **http://localhost:3000**

###### configure react app to use reactstrap

install reactstrap(via terminal command)

```
npm install bootstrap reactstrap react-popper --save
```

###### configure react app to use bootstrap

**index.js**-add this line of code to import bootstrap.

```
import 'bootstrap/dist/css/bootstrap.min.css';
```

###### adding a navigation bar

**App.js**

```
import { Navbar, NavbarBrand } from 'reactstrap';

class App extends Component {
  render() {
    return (
      <div className="App">
        <Navbar dark color="primary">
          <div className="container">
            <NavbarBrand href="/">Ristorante Con Fusion</NavbarBrand>
          </div>
        </Navbar>
      </div>
    );
  }
}
```

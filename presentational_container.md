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

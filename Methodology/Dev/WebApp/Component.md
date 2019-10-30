# Components

Components can be developed with most of the well-known libraries and frameworks, such as React, Angular, Vue, WebComponents...

## Isolation / Modularity

It will help us to get the BestPractices of Component if we understand that this concept is here to implement the Modularity idea.

- Components should never know who's their parent
- The design and api should stand on it's own
  - In many time the components API tend to serve the exact parent's need, which could be alright, but not as a goal

## Interaction with parent

- Input
  - Components should always listen to input parameters, in case the parent has changed them.
  - Don't use many input parameters, it can be a sign to bad design.
- Output
  - The output parameters must be in a form of an callback function
  - The parent doesn't have to subscribe them
  - Use State/Store to tell parent and everyone else that a change in data has occurred.
- When should we Subscribe to our external data(store/state) and when to get it from parent?
  - Passing data between siblings
  - Heavy Prop-drilling
  - (?? Research more)

## Bindings

Parameters and Variables binding of HTML and Parent components:

- One Time > On Push > One Way > Two Way
- Try to avoid Two-Way biding
  - In most cases it is a sign to a bad code design.
  - Use one:way

\*\* These definitions and implementations are differ from library to library.

## Model and View

View - Html
Model - controller

- Make use of Dependency Injection while constructing the model
- Public fields and functions are those who exposed to the HTML
- Private fields and functions are those used for internal class purposes
- In your View(HTML), write only simple functionality. The complex things should be written in the model(controller)

## More benefits of components

- Helps to improve our bundle size, usually thanks to the capability to divide the bundle to better chunks

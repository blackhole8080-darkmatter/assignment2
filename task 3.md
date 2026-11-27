# Task 3: Responsibilities
## Class analysis

| Class | Responsibilities | Reasons to change |
|---|---|---|
| `Car` | Stores car state and controls speed, movement, turning, and boundary checking. | Speed rules, movement rules, or boundary-collision rules change. |
| `Movable` | Defines the methods of a moving object: `move()`, `turnLeft()`, and `turnRight()`. | Required methods of movement may change. |
| `Volvo240` & `Saab95` | Represent a Volvo or Saab car and decide how fast they accelerate; `Saab95` also handles turbo. | The car’s engine power, trim factor, colour, acceleration formula, or turbo behaviour changes. |
| `CarController` | Connects buttons to car actions and updates cars over time. | Button changes, movement rules change, or a new car type is added. |
| `CarView` | Creates and shows the window, buttons, and gas spinner. | Window layout, button names, or button positions change. |
| `DrawPanel` | Loads and draws car images at their positions. | Car images, image paths, or drawing positions change. |

## SoC and SRP analysis

| Class | SoC | SRP |
|---|---|---|
| `Car` | Mostly good: car behaviour is separated from the GUI, but `checkBounds()` mixes car behaviour with screen-boundary rules. | Mostly yes, but it could be improved by moving boundary checking to a separate class. |
| `Movable` | Good: it only defines movement. | Yes: it has one responsibility—defining movement. |
| `Volvo240` & `Saab95` | Good: each car type has its own acceleration behaviour. | Yes: each class represents one specific car. |
| `CarController` | Weak: it mixes user input, timer updates, boundary checking, and drawing logic. | No: it has several reasons to change. |
| `CarView` | Good: it handles the user interface. | Yes: it creates and shows the GUI. |
| `DrawPanel` | Mostly good: it handles drawing, but it knows the specific `Volvo240` and `Saab95` classes. | Mostly yes, but it could be more general. |

## Classes that should be split

`CarController` should be split because it handles several different concerns:

- User input from buttons.
- Timer updates.
- Movement of cars.
- Boundary checking.
- Deciding which drawing method to call for each car type.

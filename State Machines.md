#cs 
A state machine or finite state machine (FSM) is a [[Mathematics|Mathematical]] model of computation in which a machine can only exist in one of a finite number of states. The machine transitions between states in response to inputs, and can perform actions during transitions.

A state machine is fully defined by its list of states, initial state, and the conditions for transitioning between states and often used in [[Computer Science]] programming languages.

## State Machine Implementation
To translate a state machine into a C program, we can make use of an enumerated type. Enumerated types are a special type of data type that allows us to define a set of named constants.

Enumerated types can be used to implement a state machine as follows:
- Each enumerate can be used to represent a state
- A switch statement can be used to implement the behaviour in each state
- An if statement can be used to implement the conditions for transitioning between states
```c
typedef enum
{
	START,
	STATE1,
	STATE2
} state_t;

// Initial state 
state_t state = START;

while (1){
	// State machine
	switch (state)
	{
		case START:
			if (condition1){
				// Transition if condition is met
				state = STATE1;
			}
			break;
		case STATE1:
			if (condition2){
				// Transition if condition is met
				state = STATE2;
			}
			break;
		case STATE2:
			if (condition3){
				// Go back to start if condition is met
				state = START;
			}
			break;
		default:
			// Invalid state, reset to start
			state = START;
			break;
	}
}
```
## Enumerate Types
Enumerate types are defined similarly to [[C Programming#Structures|Structures]], via the `enum` keyword, and can be anonymous, or named. The values of an enumerated type are constants, called enumerators, that are assigned an integer value starting from 0.
```c
typedef enum
{
	FALSE,
	TRUE
} boolean_t;

boolean_t b = TRUE; // b is assigned the value 1

b == TRUE; // TRUE is assigned the value 1, so this is true
b == 0; // FALSE is assigned the value 0, so this is false
```
### Enum Example
```c
typedef enum
{
	RED,
	GREEN,
	BLUE
} colour;

colour my_colour = RED;

int main() {
	if (my_colour == RED) {
		printf("My colour is red");
	}
}
```
## Switch Statements
A switch statement is a control structure that allows us to select a block of code to execute based on the value of an expression. When a case is matched, a break statement may be used to prevent the program from falling through the case, however this may be omitted if two states perform the same tasks. The default case is executed if no case is matched.

## State Machine Example
1. Declare an enum type to hold all possible state values:
```c
typedef enum {
	FULL,
	HALF,
	EMPTY
} fuel_state;
```
2. Declare a variable of this type to hold the value of the current state. The variable should be initialised with the initial state.
```c
fuel_state state = FULL;
```
3. Implement a switch-case statement that tests the current state. Each case should handle once state; every state should be handled.
```c
int main(void){
	fuel_state state = FULL;

	while (1){
		switch (state){
			case FULL:
				break;
			case HALF:
				break;
			case EMPTY:
				break;
			default:
		}
	}
}
```
4. For each state, implement any transitions. Only transitions that exit the state need to be considered. You will usually have one branch of an if statement for each transition. For some transitions additional actions will need to be taken; in this example we need to update the display output based on the state we are entering.
```c
case FULL:
	if (!PORTA.IN & PIN4_bm)){
		// S1 pressed
		state = HALF; // Transition to HALF state
		display('H'); // Update display output
	}
	break;
```
5. Its good practice to ensure your state machine will always return to a valid state. We can ensure this by handling the default case in our switch statement.
```c
default:
	// We should never get here unless 'state' has an invalid value
	state = FULL;
	display('F');
```
### Studio Example
```c
typedef enum 
{
	INIT,
	THREE,
	TWO,
	ONE,
	GO
} state_type;

int main(void){
	state_type state = INIT;
	while (1){
		switch (state){
			case INIT:
				if (pb_rising & PIN4_bm){ // S1 released
					state = THREE; // Next state is THREE
					printf("3...");
					pattern1 = segs[0];
					pattern2 = segs[3];
				}
				break;
				
			case THREE:
				if (pb_rising & PIN4_bm){ // S1 released
					state = TWO; // Next state is TWO
					printf("2...");
					pattern1 = segs[0];
					pattern2 = segs[2];
				}
				break;
				
			case TWO:
				if (pb_rising & PIN4_bm){ // S1 released
					state = ONE; // Next state is ONE
					printf("1...");
					pattern1 = segs[0];
					pattern2 = segs[1];
				}
				break;
				
			case ONE:
				if (pb_rising & PIN4_bm){ // S1 released
					state = GO; // Next state is GO
					printf("GO!\n");
					pattern1 = segs[0];
					pattern2 = segs[0];
				}
				break;
				
			case GO:
				if (pb_rising & PIN7_bm){ // S1 released
					state = INIT; // Next state is INIT
					pattern1 = pattern2 = INIT_PATTERN;
					
				}
				break;

			default:
				state = INIT;
			
		
		}
	
	}
}
```
# CSCS3613 Fall 2025
## Khadija Ahmadova

### Question 1
a. **False**:
An agent is rational as long as it selects actions that maximize its performance measure given evidence provided by its percept sequence. In other words, it is rational if it makes good decisions given sensory information it received. Rational agents can completely ignore features of the environment that are not relevant to the problem at hand. 

b. **True**:
Simple reflex-based agents act solely based on the current percept and do not maintain the state of the environemnt. They only work in fully observable, static environments. If the environment is partially observable, the agent can be stuck in infinite loop.

c. **True**:
In environment where all possible actions have same reward every agent is rational.

d. **False**:
Agent program takes as input only current percept, agent function takes percept sequence up to this point.

e. **False**:


f.

g.

h.

i.

### Question 2
The simple reflex agent `ReflexVacuumAgent` reacts solely to the immediate percept, while the model-based reflex agent `ModelBasedVacuumAgent` maintains and updates an internal model of the state. Unlike simple reflex agent, model-based reflex agent maintains internal model as a dicitionary tracking status of the two locations.

```python
# simple reflex agent
def ReflexVacuumAgent():
    def program(percept):
        location, status = percept
        if status == 'Dirty':
            return 'Suck'
        elif location == loc_A:
            return 'Right'
        elif location == loc_B:
            return 'Left'
    return Agent(program)
```

```python
# model-based reflex agent
def ModelBasedVacuumAgent():
    model = {loc_A: None, loc_B: None} # internal state

    def program(percept):
        location, status = percept
        model[location] = status # model is updated
        if model[loc_A] == model[loc_B] == 'Clean':
            return 'NoOp'
        elif status == 'Dirty':
            return 'Suck'
        elif location == loc_A:
            return 'Right'
        elif location == loc_B:
            return 'Left'
    return Agent(program)
```

When both locations are clean, simple reflex agent keeps moving back and forth forever but model-based reflex agent stops (NoOp).

### Question 3
solution manual
page 13
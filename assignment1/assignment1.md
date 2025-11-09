# CSCS3613 Fall 2025
## Khadija Ahmadova

### Intelligent Agents

#### Question 1
a. **False**:
An agent is rational as long as it selects actions that maximize its performance measure given evidence provided by its percept sequence. In other words, it is rational if it makes good decisions given sensory information it received. Rational agents can completely ignore features of the environment that are not relevant to the problem at hand. 

b. **True**:
Simple reflex-based agents act solely based on the current percept and do not maintain the state of the environemnt. They only work in fully observable, static environments. If the environment is partially observable, the agent can be stuck in infinite loop.

c. **True**:
In environment where all possible actions have same reward every agent is rational.

d. **False**:
Agent program takes as input only current percept, agent function takes percept sequence up to this point.

e. **False**:
Agent functino is a mathematical description of agent's behavior. Agent program is real implementation. Some agent functions are not implementable because they require solving problems that are uncomputable or require infinite time and resrouces. Examples are the halting problem or NP-hard problems.

f. **True**:
Selecting randomly is rational if every action you take has same reward.

g. **True**:
Perfectly rational agent acts to maximize its performance measure. Environment includes states of the world, how actions affect states, percepts, and performance measure. For a given agent to be perfectly rational in distict task environments, parts of environment that are different should be parts that the agent does not reach and does not interact with.

h. **False**:
Unobservable environment means agent can't perceive environment's current state. Agent is rational if it is choosing best action given what it knows. This does not require observability. In unobservable environment rational agent still acts optimally based on prior knowledge or model of the environment

i. **False**:
Perfectly rational agent plays the best possible game given the cards it has, but it does not necessarily win every game.

#### Question 2
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

#### Question 3
**a.** Simple reflex agent acts only based on its current percept and does not keep track of what happend before. So, if it thinks the square is dirty, it it will keep sucking until it senses that the square is clean. But since sensors are wrong 1 out of 10 times, agents perception is not very reliable. Agent should check multiple times to be get a more reliable measurement.

**b.** Agent should revisit all squares regularly because the longer a square hasn't been cleaned, the more likely it's dirty again.


### Search
#### Question 1

<img src="https://github.com/khadija-ahmadova/csci3613-fall25/blob/main/assignment1/search_q1_greedy.jpg?raw=true" alt="alt text" width="500" height="300">

<img src="https://github.com/khadija-ahmadova/csci3613-fall25/blob/main/assignment1/search_q1_a_star.jpg?raw=true" alt="alt text" width="600" height="500">

#### Questions 2
A* search does not return the optimal path because given heuristic overestimates the cost.
In order for the A* algorithm to return the shortest path, heuristic must never overestimate the cost. 

### Constraint Satisfaction Problem
#### Question 1
**Scenario 1** - different session of one course cannot be taught by different professors

Variables:

    C1 - programming principles 1

    C2 - theory of computation

    C3 - artificial intelligence

    C4 - machine learning

    C5 - data mining


Domains: 

Which professor(s) is qualified to teach every class

    C1 = {A, C}

    C2 = {A}

    C3 = {B, C}

    C4 = {B, C}

    C5 = {A, B}

Constraints:

    C1 != C2 - Mon/Wed overlaps with Wed/Fri
    C3 != C4 - Tue/Fri both

**Scenario 2** - different session of one course can be taught by different professors

Variables:

    C1m - programming principles 1 Monday session

    C1w - programming principles 1 Wednesday session

    C2w - theory of computation Wednesday session

    C2f - theory of computation Friday session

    C3t - artificial intelligence Tuesday session

    C3f - artificial intelligence Friday session

    C4t - machine learning Tuesday session

    C4f - machine learning Friday session

    C5t - data mining Thursday session

    C5s - data mining Saturday session

Domains: 

    C1m = C1w = {A, C}

    C2w = C2f = {A}

    C3t = C3f = {B, C}

    C4t = C4f = {B, C}

    C5t = C5S = {A, B}

Constraints:

    wednesday sessions - C1w != C2w

    friday sessions - C2f != C3f

    tuesday session - C3t != C4t

    friday overlap - C3f != C4f


#### Question 2

<img src="https://github.com/khadija-ahmadova/csci3613-fall25/blob/main/assignment1/csp_q2.jpg?raw=true" alt="alt text" width="500" height="650">


For both scenarios constraint propagation reduces domain but does not solve problem completely.


#### Question 3

<img src="https://github.com/khadija-ahmadova/csci3613-fall25/blob/main/assignment1/csp_q3.jpg?raw=true" alt="alt text" width="600" height="600">

#### Question 4

### Adversarial Search
#### Question 1
#### Question 2

<img src="https://github.com/khadija-ahmadova/csci3613-fall25/blob/main/assignment1/adversarial_search_q2.jpg?raw=true" alt="alt text" width="600" height="300">


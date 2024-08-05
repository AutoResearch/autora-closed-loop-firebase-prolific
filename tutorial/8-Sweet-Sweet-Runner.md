# Sweet, sweet Runner

Now that we have the sweetPea and sweetBean function, we can use them in the experiment runner in `aurora_workflow.py`. 

## Update Website

First, we add dependencies to our website:

head over to `testing_zone` and install the jspsych dependency:

```shell
npm install @jspsych-contrib/plugin-rok
```

Also make sure to include the following lines in the `main.js` file in `testing_zone/src/design`:
```javascript
import jsPsychRok from '@jspsych-contrib/plugin-rok'
global.jsPsychRok = jsPsychRok
```

From now on, we also will use the full and do no processing in javascript: 
```javascript
const main = async (id, condition) => {
    const observation = await eval(condition['experiment_code'] + "\nrunExperiment();");
    return JSON.stringify(observation)
}
```

once this is done, rebuild and redeploy your websits:

```shell
npm run build
firebase deploy
```

## Update AutoRA workflow:

Let's import the functions:

```python
from trial_sequence import trial_sequences
from stimulus_sequence import stimulus_sequence
```

First, update the variables:

```python
variables = VariableCollection(
    independent_variables=[
        Variable(name="S1", allowed_values=np.linspace(1, 100, 100)),
        Variable(name="S2", allowed_values=np.linspace(1, 100, 100)),
        ],
    dependent_variables=[Variable(name="rt", value_range=(0, 10000))])
```

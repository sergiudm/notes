## Context windows handling
```python
if len(self.observations) > self.max_trajectory_length:
	if self.max_trajectory_length == 0:
		_observations = []
		_actions = []
		_thoughts = []
	else:
		_observations = self.observations[-self.max_trajectory_length:]
		_actions = self.actions[-self.max_trajectory_length:]
		_thoughts = self.thoughts[-self.max_trajectory_length:]
else:
	_observations = self.observations
	_actions = self.actions
	_thoughts = self.thoughts
```


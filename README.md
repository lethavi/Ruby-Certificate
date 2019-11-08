## This is just some notes for who want to get Ruby Certificate

#### 1. Identify

- 0..9
- A-Z, a-z
- underscore
- Number is not placed in the first
- Do not same with key of Ruby

- Example for wrong identify:
  - 1_to_100
  - abc?
  - abc-1

#### 2. Scope of variable, constant

| Type           | Identify rules                           | Scope                                        | Value when do not init                     |
| -------------- | ---------------------------------------- | -------------------------------------------- | ------------------------------------------ |
| Local variable | First character: alphabeta or underscore | The nearest scope(where variable is defined) | If defined -> nil, else -> raise exception |

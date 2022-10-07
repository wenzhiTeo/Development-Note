# Way to use the PDB

- import pdb; pdb.set_trace()
  
python>3.7
- breakpoint()

## Related command in Debug

Operation | Code | Example
---------|----------|---------
 Inspect the value of variable | p [variable name] | p var1 **or** p var1,var
 [enter] | _If click enter without any changes will execute the previous command _||
 list 11 line of code around the break | l | use **l .** redirect to start point
 list the code just in the function | ll | use **l .** redirect to start point
 Print valid Python expression | p [method] | p getattr(get_path, '\_\_doc\_\_')
 Prety Print nicely format out put | pp |-

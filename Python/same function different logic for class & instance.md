# Allow a funtion handling the logic separately between class and instance call

**Description**
- There is some situation we need a function that able to call by class & instance simultaneously. 
- And the function might also need to handle different logic when called by either class or instance

### Workable sample usecase

``` Python
class GetAvailableIntVariable(object):
    def __get__(self, object, object_type):
        def get_available_variables():
            caller_type = object_type if object is None else object

            # handle called by class
            if object is None:
                print("Nothing to do when called by class")
                return None

            # handle called by instance
            else:
                caller_type.available_variables_dict = {}

                for attribute in dir(caller_type):
                    if attribute.startswith("__"):
                        continue
                    if not isinstance(getattr(caller_type, attribute), int):
                        continue

                    value = getattr(caller_type, attribute)
                    caller_type.available_variables_dict[attribute] = value

                print("Return all the available int variable")
                return caller_type.available_variables_dict

        return get_available_variables


class TestA(object):
    get_available_int_variables = GetAvailableIntVariable()

    # Generate int variable for testing
    def __init__(self, variable_num=1):
        num = 0
        for x in range(variable_num):
            setattr(self, f"var_{num}", num * 3)
            num += 1


# An instace that having 3 int variable
instanceA = TestA(3)

# Supposed should print out the 3 generated int variables
print(instanceA.get_available_int_variables())

# Supposed should print out "None" as it called by class
print(TestA.get_available_int_variables())

```


### Simplyfy version

```Python
class TestB(object):
    def print_type(self,obj, obj_type):
      print(f"The type of {obj} is {obj_type}")
      
    def __get__(self, obj, obj_type):
        def print_type_method():
            return self.print_type(obj, obj_type)

        return print_type_method

class TestA:
    test_b = TestB()
    
instanceTestA = TestA()

TestA.test_b()
instanceTestA.test_b()
```

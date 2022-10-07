# Allow Different Operation Logic in Same method for called by class and called by instance
### Python Descriptor

``` Python
class GetAvailableEmvVariable(object):
    def __get__(self, object, object_type):
        def get_available_emv_variables():
            caller_type = object_type if object is None else object

            if object is None:
                print(object_type)
                print("called by class")

            caller_type.available_variables_dict = {}
            for attribute in dir(caller_type):
                if attribute.startswith("__"):
                    continue
                if not isinstance(
                    getattr(caller_type, attribute), EnhancedMessageVariable
                ):
                    continue
                emv = getattr(caller_type, attribute)
                caller_type.available_variables_dict[attribute] = emv

            return caller_type.available_variables_dict

        return get_available_emv_variables
```

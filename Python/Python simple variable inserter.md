```Python
import re

class Variable(object):
    def __init__(self,name=None,value=None,):
        self.name = name
        
class VariableInserter(object):
    def __init__(self,context={}):
        self.variable_dict={}
        
        for attribute_name in dir(self):
            attribute = getattr(self,attribute_name)
            
            if isinstance(attribute,Variable):
                variable_name = attribute.name
                value = context.get(variable_name)
                
                self.variable_dict[variable_name] =value
                
    
    def get_available_variables(self):
        print(self.variable_dict)
    
    def replace_text(self,text):
        placeholders = re.findall(r'{(.+?)}', text)
        
        for placeholder in placeholders:
            value = self.variable_dict.get(placeholder)
            text = text.replace(f"{{{placeholder}}}",value)
        
        return text
        
        
class TestInserter(VariableInserter):
    var_a = Variable(name="AAA")
        

inserter= TestInserter(context={"AAA":"12377"})
print(inserter.replace_text("The value is {AAA}"))
```

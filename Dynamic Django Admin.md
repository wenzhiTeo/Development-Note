``` Python

# Add choice dynamically for Django Admin
# add init function to the specific model
def __init__(self, *args, **kwargs):
  super(MODEL_NAME, self).__init__(*args, **kwargs)
  self._meta.get_field("FIELD_NAME").choices = CHOICES_OPTION

```

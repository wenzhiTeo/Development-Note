
Add `custom flag` as custom argument

```python
    xxx = xxxSerializer(
        many=False,
        required=False,
        allow_null=True,
        custom_flag=True,
    )
```

Use custom flag
```python
class xxxSerializer(NestedModelSerializer):
    # add init function to receive custom argument
    def __init__(self, *args, **kwargs):
        self.custom_flag = kwargs.pop(
            "custom_flag", None
        )

        super().__init__(*args, **kwargs)
    
    # use custom argument to update display result -> reorder the `unordered_result` based on its order field
    def to_representation(self, instance):
        response = super().to_representation(instance)

        if self.custom_flag:
            response["unordered_result"] = sorted(
                response["unordered_result"], key=lambda x: x["order"]
            )

        return response
```

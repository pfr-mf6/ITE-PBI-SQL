# ProQA-augmentation


```m
let
    Source = Sql.Database("pfbsql3", "Elite_DWPortland", [Query="

Put your sql here but PLEASE ensure there are no double quotes - single quotes only!

    "])
in
    Source
```


## DAX measures:

The `res` measures take the boolean columns created from the "merge" and count them to be used in the report as the "blue", "red", etc counts.

```m
res Cancel OS = 
CALCULATE(
    COUNT(ProQA_Merge[result]),
    ProQA_Merge[result] = "Cancel OS"
)
```

# Debugging Python via VSCode

##### [Back to Home](README.md)

### Debug Over Multiple Files
By default, you can set break points within the file working on.

But, in most case, multiple files are associtated in a single project.
Thus, setting up break points in the files other than main running file shall not be stopped during debugging.

Then, how to investigate variables while running the project. 

##### launch.json

VSC runs under some environment setting like settings.json, launch.json, task.json etc.
Among then, launch.json defines debugging environment.

Typical ```launch.json``` file:

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Current File",
      "type": "python",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal",
      "justMyCode": true
    }
  ]
}
```

To work over multiple files, change the value of ```justMyCode``` to true. 
**Note** This works on the files in the project only.

```json
{
  // Use IntelliSense to learn about possible attributes.
  // Hover to view descriptions of existing attributes.
  // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
  "version": "0.2.0",
  "configurations": [
    {
      "name": "Python: Current File",
      "type": "python",
      "request": "launch",
      "program": "${file}",
      "console": "integratedTerminal",
      "justMyCode": false
    }
  ]
}
```


##### [Back to Home](README.md)

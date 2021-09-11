# Xdebug (VBA Immediate Window in Output VSCode Window)
    
## Description
 - This package provides a way to simulate VBA Immediate Window in Output VSCode window
 - Find the Output window (VBA Immediate Window)

 ## Methods

 <p>
<img src="https://github.com/Aeraphe/xdebug/blob/main/images/immediate.gif" alt="VBA immediate Window">
</p>


 ### Xdebug.printx

- This method print any type os variable


```

Public Sub index()


  Dim test(1) As Variant

  'Add an Object
  Set test(0) = Sheets(1)
  'Add a String
  test(1) = "Test Xdebug Output"
  
  Xdebug.printx test

End Sub

```


 ### Xdebug.printError

- This method is use for print error


```
 Public Sub index()
  
  On Error GoTo ErrorHandle:
    'throw an error
    d = 1/0
    'Your code here
  
  
 ErrorHandle:
    Xdebug.errorSource = "pageConsoller.index"
    Xdebug.printError

 End Sub
```


 ### Xdebug.printErrorAndRaise

- This method is use for print error and raise the error to the "parent" function/sub/method
- Just used for "children"  function/sub/method


```
 Public Sub index()
  
  On Error GoTo ErrorHandle:

  'Children Function Call that will throw an Error and Raise to the Sub
  Call errorSimulation

  
 ErrorHandle:
    Xdebug.errorSource = "pageConsoller.index"
    Xdebug.printError

 End Sub


'Throw an Error and Raise the his parent
 Public Function errorSimulation()
  
  On Error GoTo ErrorHandle:
    'throw an error
    d = 1/0  
  
 ErrorHandle:
    Xdebug.errorSource = "pageConsoller.errorSimulation"
    Xdebug.printErrorAndRaise

 End Function


```
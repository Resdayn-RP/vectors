# Vectors

## Prelude

This is my vectors library for lua, I currently am integrating this into my own roleplay core for tes3mp.

This is very early in development but it has some useful features to make life easier for some tes3mp developers.

## Installation

For tes3mp, this should be required in the custiomScripts.lua, at the very top of the file.
```lua
vec3 = require("custom/vectors/main")
```

## Usage

### Creating Vectors
To create a vector, just do call vec3 with the dimensions of the vector.
```lua
vec3(x, y, z)
```
You can also assign them to a variables:
```lua
local v1 = vec3(1, 2, 3)
```
You can also use vec3 to create a 2d vector
```lua
local v2 = vec3(1, 2)
```
### Arithmatic
You can perform arithmetic on vectors as well!
#### Addition
```lua
local v1, v2 = vec3(1, 2, 3), vec3(3, 2, 1)
print(v1 + v2) -- outputs: vec3(4, 4, 4)
```
#### Subtraction
```lua
local v1, v2 = vec3(1, 2, 3), vec3(3, 2, 1)
print(v1 - v2) -- outputs: vec3(-2, 0, 2)
```
#### Multiplication
```lua
local v1, v2 = vec3(1, 2, 3), vec3(3, 2, 1)
print(v1 * v2) -- outputs: vec3(3, 4, 3)
```
#### division
Division does not work on vectors, but you can divide a vector by a whole number
```lua
local v1, a = vec3(1, 2, 3), 3
print(v1 / a) -- outputs: vec3(0.333, 0.666, 1)
```
#### Magnitude of a vector
You can get the length of a vector using the ```#``` operand:
```lua
local v1 = vec3(1, 2, 3)
print(#v1) -- outputs: 3.742
```
You can also take the length of 2 vectors subtracted by eachother to figure out how far they are from eachother.
```lua
local v1, v2 = vec3(1, 2, 3), vec3(3, 2, 1)
print(#(v1 - v2)) -- outputs: 2.828
```
### Conditionals
You can also compare 2 vectors together for if statements.
```lua
local v1, v2 = vec3(1, 2, 3), vec3(3, 2, 1)
if v1 == v2 then
    return true
else
    return false
end
--This code will return false
```
This only directly works for vectors when checking if they are equal, if you need to do "<=", "=>", etc, then take the magnitude of the vectors and compare their size.
```lua
local v1, v2 = vec3(1, 2, 3), vec3(2, 2, 1)
if #v1 <= #v2 then
    return true
else
    return false
end
--This code will return false
```

## Example for implementation in tes3mp scripts
This example will create a function that can be used to retrieve player locations
```lua
---@class functionsTable
local functionsTable  = {}

local functionsTable.getPlayerData(pid)
    return vec3(tes3mp.GetPosX(pid), tes3mp.GetPosY(pid), tes3mp.GetPosZ(pid))
end

return functionTable
```

Now you can benefit from the vectors library from the positional data from tes3mp.

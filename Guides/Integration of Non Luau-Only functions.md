# ⚠ This article is a stub/WIP. ⚠

### This guide will directly explain and help you with implementing `getcustomasset.lua`, `hookmetamethod.lua`, `getscriptclosure.lua`, `LoadLibrary`, `getsenv.lua` and `getfunctionhash.lua`, since they lack a direct code-only implementation here, and require more work (for example, a bridge)

###### (This is a high level guide, it will not get into details about how to hook functions, for example. But it will provide the base for the lua function.)

You will be told when an implementation is not fully functional, and why.

I will also try to spoon-feed here as much as possible since I want everyone to be able to use my code.

## 1. `getcustomasset.lua`
## 2. `hookmetamethod.lua` (Semi-Functional and functional)

Before we get into this, I have to state that (as also said in this project's README.md), replacing the metamethod is NOT enough.

You need to ACTUALLY HOOK the metamethod. There are 2 ways to do this, first one:
```lua
local hookmetamethod = function(first, metamethod, func)
	local mt = getrawmetatable(first)
	local backup = clonefunction(mt[metamethod])
	
	hookfunction(mt[metamethod], func)

	return backup
end
```
This is the traditional way. It requires `getrawmetatable`, `clonefunction` and `hookfunction`.

Second way:

```lua

```
It requires `clonefunction` and `hookfunction`.
A common misconception is that hookmetamethod is ONLY for `game`, actually every instance, userdata and tables have metamethods. Why did I say this?

Because this method requires the metamethod to throw an error, so it appears in the call stack. However, userdatas can be created with `newproxy`, which lets the game create metamethods that don't throw errors, making it impossible. However, since most of the users are using hookmetamethod for a simple `game` metamethod hook. 



## 3. `getscriptclosure.lua`/`getscriptfunction.lua`
## 4. `LoadLibrary`
## 5. `getsenv.lua` (Semi-Functional)
## 6. `getfunctionhash.lua` (Semi-Functional)

# How to find Roblox addys to update your Roblox Exploit!

- mainly for [Nezy Exploit](https://github.com/NezyDev/Nezy-ExploitV2) (at least for now..)

- 1/6/2023
- version-f51be0bac4f14d35
- Volt was here
- Special Thanks to Nezy
- I will add more addys soon
- **Download IDA 7.7 [here](https://www.mediafire.com/file/zw1txf3fk9tr6t3/ida77.zip/file)**
- **Download PETOOLS [here](https://github.com/petoolse/petools/releases)**

# -= Print =- 

1. Search for the string `Video recording started`
2. Find then Ref, under that there should be a call double click the address it calls
3. Decompile it
4. now, scroll to the top. you should find something similar to this...

```cpp
unsigned int sub_######(int a1, int a2, ...)
```
![image](https://user-images.githubusercontent.com/77842492/211026718-865612c4-9665-47c4-b954-b043d8dfc934.png)

**the ###### is the addy. So it's 0x######**

# -= Logs =-

1. Search for the string `osVersion`
2. Find the Ref
3. Decompile it
4. scroll to the top and there u go! u should find smth like...

```cpp
// I'm not 100% sure about this addy but this should be it
int __thiscall sub_######(_DWORD **this)
```
![image](https://user-images.githubusercontent.com/77842492/211027193-5898b8d5-f40f-4f1c-9659-c5e2693d7cc5.png)

**the ###### is the addy. So it's 0x######**

# -= luavm_load =-

1. Search for the string `syntax error: %s` or `oldResult`
2. Find the Ref
3. Decompile it
4. Now, between these two strings you should find something like... 
```cpp
sub_######(int (__cdecl *)(char *, _DWORD))
```
(Not exactly that. Something like that), Wow!! Congrads! you just found the luavm_load addy!!!!! the ###### is the addy. **So it's 0x######**

![image](https://user-images.githubusercontent.com/77842492/211028854-0fdd994f-26a6-45fd-82e7-cae8fdcea472.png)

# -= TaskDefer =-

1. Search for the string `Maximum re-entrancy depth (%i) exceeded calling task.defer`
2. Find the Ref
3. scroll to the start of that thing

For example:
```cpp
.text:007B1C00                 push    ebp
```
well **7B1C00** is the addy, **So it's 0x7B1C00**

![image](https://user-images.githubusercontent.com/77842492/211036286-06dc9248-41e8-46f2-b27d-a9a2c105363b.png)

![image](https://user-images.githubusercontent.com/77842492/211036318-f5cec11e-89bf-45f2-9c61-e7ff9dacc58e.png)


# -= GetState =-

1. Search for the string `debug`
2. Find the string with all lowercase `debug`
3. Find the ref
4. Go above the `S U B R O U T I N E` thingy
5. Double click that one sub
6. Decompile it.

```cpp
int __thiscall sub_######(int this, _DWORD *a2)
```
**The ###### is the addy. So it's 0x######**

![image](https://user-images.githubusercontent.com/77842492/211151687-d1e0a552-4339-421d-80a7-98af14877def.png)

# -= Speaking of GetState... (LuaState) =-

**You can get the LuaState from GetState!**
1. Find **GetState**
2. In get state Right Click one of the `this`.
3. Click `Reset pointer type`
4. **The bottom one should be the LuaState.**

![image](https://user-images.githubusercontent.com/77842492/211151900-7720f7af-38b8-41de-818d-fb2c220c0fcc.png)

![image](https://user-images.githubusercontent.com/77842492/211152002-7c7ea8a3-454e-45be-8de0-f0abaf0dc3b7.png)


# -= GetScheduler =-

1. Search for the string `Watchdog` or `LuauWatchdog`
2. Find the ref
3. Go down to the *loc* thing, open the 2nd **sub**
4. Decompile it.
5. Go to the top (the start of the function) and you should find it. 

```cpp
int sub_######() 
{
 // the other code...
}
// ###### is the addy. So, it's 0x######
```

![image](https://user-images.githubusercontent.com/77842492/211193894-a60517ef-3ef0-4b8c-9218-06097319fbc3.png)
![image](https://user-images.githubusercontent.com/77842492/211193901-8b83d281-0845-48da-bfa2-394a06ff85ff.png)

# -= LuaState Offsets =-

1. Search for the string `Argument 3 missing or nil`
2. Find the Ref
3. Decompile it (it may take some time...)
4. Above the if statement you should see a virable. 
5. The first number you see is the `lua_state_top` and the second number is the `lua_state_base`.

**For example:**

```cpp
 //                     top                    base 
 //                     vvvv                   vvvv
  v3 = (*(_DWORD *)(a2 + 12) - *(_DWORD *)(a2 + 28)) >> 4;
  if ( v3 < 4 )
  {
    sub_000000("Argument 3 missing or nil");
    goto LABEL_000;
  }
  ```
  
  ![image](https://user-images.githubusercontent.com/77842492/211194550-f2cc9d6e-a27a-42d8-87ed-bb551a06aa64.png)


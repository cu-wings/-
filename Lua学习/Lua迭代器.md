### 迭代器

lua中，泛型for的语义类似于

```lua
for a,b,c... in explist do block end
```

其等价于

```lua
do
    local _f, _s, _var = explist
    while true do
        local a,b,c... = _f(_s, _var)
        _var = a
        if _var == nil then break end
        block
    end
end
```
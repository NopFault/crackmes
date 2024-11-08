# Some Crackmes

I'm starting to learn reverse engineering. This repository is fork from https://github.com/NoraCodes/crackmes i will use this for my learning path by using my apple macbook M1 Aarch64. 

# Solved ones

### cracmes01

Probably strings command would be enough.

```
;-- str.password1:                                                      │ =  Symbols                   [& cache] │
│             ; STRN XREF from main @ 0x100003e90(w)                                  │ 0x100000000 0 __mh_execute_header      │
│             0x100003f70     .string "password1" ; len=10                            │ 0x100003e48 0 _main                    │
│             ;-- str.No___s_is_not_correct._n:

```

### crackmes01e

```
;-- str.slm_paas.k:                                                     │ 0x100003f3c 0 imp.strlen               │
│             ; STRN XREF from main @ 0x100003e90(w)                                  │ 0x100003f48 0 imp.strncmp              │
│             0x100003f70     .string "slm!paas.k" ; len=11                           │ 0x100003e48 0 func.100003e48           │
│             ;-- str.No___s_is_not_correct._n:
```

### crackmes02

ghidra:

```
...
if ("password1"[local_2c] + -1 != (int)*(char *)(*(long *)(param_2 + 8) + (long)local_2c))
    break
...
```
solved:

```
>>> l1 = list("password1")
>>> ats=''
>>> for char in l1:
...     ats += chr(ord(char) - 1)
...
>>> ats
'o`rrvnqc0'
>>>
```



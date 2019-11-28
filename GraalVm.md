# GraalVM

Set of tools 

- Truffle
- New Compiler
- AOT

# New Compiler

JVMCI 

```
interface JVMCICompiler {
    byte[] compileMethod(byte[] bytecode);
}
```

# Graal Compiler

- Written in Java
- Very good scape analisis
- Especulative optimization (Code inlining)


# Truffle

Framework to build new languages using AST Interpreters

- R
- Ruby
- JavaScript
- Sulong (BitCode interpreter)
- Smalltak

# AOT

- Ahead of time compiling
- No need for runtime
- Some limitations


# Links

https://www.youtube.com/watch?v=SYg4KO8Z2Ts
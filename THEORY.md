# Nitro Parts Spec

Pattern for constructing new Nitro Parts for library assembly.

## General Structure
```

+----------------------------------------------+
|                                              |
|                                              |
|     [+] <nitro-part>                         |
|      |                                       |   bin        = comopnent specific executable utility files
|      +------>[ ] bin                         |
|      |                                       |   src        = part implementation code and libs live here
|      +------>[ ] docs                        |
|      |                                       |   src/lib    = common js files across implementations
|      +------>[+] src                         |
|      |        |                              |   src/res    = common media/images for implementations
|      |        |                              |
|      |        +------>[ ] lib                |   src/impl   = implementations supported by this componen
|      |        |                              |
|      |        +------>[ ] tag                |   build.json = config for building implementation version
|      |        |                              |
|      |        +------>[+] impl               |   part.json  = part definition config for Nitro assembly
|      |                 |                     |
|      |                 +--->[+]<name>        |   impl/test  = all unit tests for specific implementation
|      |                 |     |               |
|      |                 |     +-->build.json  |   t/index.js = main test file (for running all tests)
|      |                 |                     |
|      |                 +--->[+]test          |
|      |                       |               |   res/zero   = default skin for component - structure only
|      |                       +-->index.js    |                no style features
|      |                                       |
|      +------>[+] res                         |   res/<name> = specific style features based on a particular
|      |        |                              |                theme.
|      |        +------>[+] zero               |
|      |        |        |                     |   test       = top-level tests for integration testing
|      |        |        +-->mytag.zero.css    |
|      |        |                              |
|      |        +------>[+] <skin>             |   Generated Files
|      |                 |                     |
|      |                 +-->mytag.<skin>.css  |   dist       = generated dirst dir gets assembled parts that
|      |                                       |                can be deployed in a ui sandbox, to larger
|      |                                       |                deployed library or to test suite
|      |                                       |
|      +------>[ ] part.json                   |   .nitro     = generated partid & semvar number
|      |                                       |
|      +------>[G] .nitro                      |
|      |                                       |
|      +------>[G] dist                        |
|                                              |
|                                              |
|                                              |
+----------------------------------------------+


```

## Simple Parts Specification

The Simple Parts Specification outlines the *draft* guidance for creating, testing, and publishing new Parts. Because this pattern will be foundational to the entire system, we'll need a strategy to safely synchronize updates (probably via an update/migrate script and other semver-friendly strategies)

This current draft specification can be found in the [Nitro Parts Spec](https://github.com/nitroUI/nitro-parts-spec/blob/master/README.md) repo.


## Atomic Parts Hierarchy 

The Atomic Parts Hierachy is a language for describing objects and relationships in the Nitro component assembly system. In their minimal form, **Elements** are abstract (dumb) containers with a special property called **Data**; this definition helps reinforce Nitro's *Data-First Strategy*. 

By organizaing and grouping these elements into more complex **Parts**, we can create higher-order elements called **Modules**. Modules can be customized, decorated or grouped together to create supermodules called **Applications** -- just to give you an idea of some basics. Underneath it all, we try to stay focused on the flow of data between related parts.

## Sub-Atomic Parts Hierarchy 

Looks like this:

```
                         +
                         |
                         +
                     [--ABS--]
                     |   |   |
                     |   |   |
       +-------------+   |   +-----------------------+
       |                 |                           |
       |                 |                           |
       v                 v                           v
[VirtualEvent]    [VirtualElement]            [VirtualProperty]
       |                 |                           |
       |                 |                           |
      ...                |                           |
                     {Element}                   {Property}
                      |  |  |                     |  |  |
                      |  |  |                     |  |  |
                      |  |  |                     |  |  |
             +--------+  |  +-------+         +---+  |  +----+
             |           |          |         |      |       |
             v           v          v         v      v       v
    ...  {ATOMIC}   {COMPOSITE}  {NESTED}   {POS}  {SKIN} {GEOMTR} ...

```


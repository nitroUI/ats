# Nitro Parts Template

Pattern for constructing new Nitro Parts for library assembly.

## General Structure
```

+----------------------------------------------+
|                                              |
|                                              |
|     [+] <nitro-part>                         |
|      |                                       |   bin        = component specific executable utility files
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


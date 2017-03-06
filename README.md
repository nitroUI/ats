# Nitro Abstract Part Specification

A Part is a pre-compiled tag, when a part is compiled/published, it is packaged as a tag.

Pattern for constructing new Nitro Abstract Tags for library assembly.

## General Structure
```

+----------------------------------------------+
|                                              |
|                                              |
|     [+] <nitro-part>                         |
|      |                                       |   bin        = component specific executable utility files
|      |                                       |
|      +------>[ ] bin                         |   tag        = sandbox tag and subtag templates (html)
|      |                                       |   src        = tag implementation code and libs live here
|      +------>[ ] docs                        |
|      |                                       |   src/lib    = shared js files across implementations
|      +------>[+] src                         |
|      |        |                              |   src/res    = shared media/images for implementations
|      |        |                              |
|      |        +------>[ ] lib                |   src/impl   = implementations supported by this component
|      |        |                              |
|      |        +------>[ ] tag                |   build.json = config for building implementation version
|      |        |        |                     |
|      |        |        |____ tag.html        |
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


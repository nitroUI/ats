
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


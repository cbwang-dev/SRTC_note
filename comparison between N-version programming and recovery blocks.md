|                     | N-version                                                                    | recovery blocks                                                      |
| ------------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| redundancy          | static                                                                       | dynamic                                                              |
| design overhead     | development comparison model                                                 | acceptance test                                                      |
| execution overhead  | N-times more resources                                                       | ask resources for creation of checkpoints and for restoration itself |
| deversity of design | both                                                                         | both, so they are both sensitive to errors in specification          |
| error detection     | compares different results                                                   | acceptance test, more flexible                                       |
| atomicity           | compute and choose before interaction with environment, atomicity guaranteed | interaction is only after acceptance test, atomicity can be structured                                                                    |

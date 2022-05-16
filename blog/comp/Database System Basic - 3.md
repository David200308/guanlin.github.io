<center>
  <h1><b>Database System Basic - 3 </b></h1>
  <h2>Database Storage II</h2>
</center>

---

<center><h1>Page Base Storage</h1></center>

---

## A. Disk-oriented Architecture

The DBMS assumes that the primary storage location of the database is on non-volatile disk.

The DBMS's components manage the movement of data between non-volatile and volatile storage.



## B. Log-structured File Organization

Instead of storing tuples in pages, the DBMS only stores **log records**

### 1. Update / Write Log

The system appends log records to the file of how the database was modified:

--> Inserts store the entire tuple

--> Deletes mark the tuple as deleted

--> Updates contain the delta of just the attributes that were modified

For example:

<img src="./img/image-20220516140754074.png" alt="image-20220516140754074" style="zoom:50%;" />



### 2. Read

#### a) To read a record, the DBMS scans the log backwards and "recreates" the tuple to find what it needs

For example: 

<img src="./img/image-20220516141333618.png" alt="image-20220516141333618" style="zoom:50%;" />

#### b) Build index to allow it to jump to location in the log

For example:

<img src="./img/image-20220516141613525.png" alt="image-20220516141613525" style="zoom:50%;" />

### c) Periodically compact the log

For example:

<img src="./img/image-20220516142235795.png" alt="image-20220516142235795" style="zoom:67%;" />



## C. Log-structured Compaction

Compaction coalesces larger log files into smaller files by removing unnecessary records



| Level Compaction                                             | Universal Compaction                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| <img src="./img/image-20220516142552544.png" alt="image-20220516142552544" style="zoom:50%;" /> | <img src="./img/image-20220516142716972.png" alt="image-20220516142716972" style="zoom:60%;" /> |



<center><h1>Data Resentation</h1></center>

---

**INTEGER / BIGINT / SMALLINT / TINYINT**

--> C / C++ Representation

**FLOAR / REAL vs. NUMERIC / DECIMAL**

--> IEEE-754 Standard / Fixed-point Decimals

**VARCHAR / VARBINARY / TEXT / BLOB**

--> Header with length, followed by data bytes

**TIME / DATE / TIMESTAMP**

--> 32 / 64-bit integer of (micro) seconds since Unix epoch



## A. Variable Precision Numbers

Inexact, variable-precision numeric type that uses the "native" C / C++ types

--> Ex: FLOAT / REAL / DOUBLE

### Example:

```c
#include <stdio.h>

int main(int argc, char* argv[]) {
  float x = 0.1;
  float y = 0.2;
  printf("x + y = %f\n", x + y);
  printf("0.3 = %f\n", 0.3);
}

// output: 
// x + y = 0.300000
// 0.3 = 0.300000
```

```c
#include <stdio.h>

int main(int argc, char* argv[]) {
  float x = 0.1;
  float y = 0.2;
  printf("x + y = %.20f\n", x + y);
  printf("0.3 = %.20f\n", 0.3);
}

// output: 
// x + y = 0.30000001192092895508
// 0.3 = 0.29999999999999998890
```



## B. Fixed Precision Numbers

Numeric data types with arbitrary precision and scale. Used when rounding errors are unacceptable

--> Ex. NUMERIC / DECIMAL

Many different implementations
















# C++ Debugging Guide
Author: Muhammad F. Kasim

## Inspecting Segmentation Fault
### Requirements
* `gdb`

### Steps
* Compile with `-g` flag
* Type in the terminal:
```
gdb ./executable
```

* In the `gdb` window, type:
```
r
bt
```

## Detect false sharing on Linux
### Requirements
* `perf`

### Steps
* Turn on the OpenMP parallelization by adding flag `-fopenmp`
* Compile with `-g` flag
* Type in the terminal:
```
sudo perf c2c record ./executable
sudo perf c2c report -i perf.data
```

## Detect memory leaks on Linux
### Requirements
* `valgrind`

### Steps
* Compile with `-g` flag
* Type in the terminal:
```
valgrind --leak-check=full --undef-value-errors=no -v ./executable
```
* `valgrind` will report the memory leaks in the stdout

## Speed performance profiling
### Requirements
* `gprof` (usually installed with `gcc`)

### Steps
* Compile with flags `-g -pg -no-pie`
* Type in the terminal:
```
./executable
gprof ./executable gmon.out > analysis.test
less analysis.test
```

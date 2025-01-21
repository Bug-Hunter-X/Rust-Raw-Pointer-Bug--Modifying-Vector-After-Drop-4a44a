# Rust Raw Pointer Bug: Modifying Vector After Drop

This repository demonstrates a common error in Rust when working with raw pointers: modifying the value pointed to by a raw pointer after the vector has been dropped or reallocated.  The code attempts to modify a value in a vector via a raw pointer after the vector's capacity is exceeded. This can lead to undefined behavior, crashes, or other unexpected results.

The `bug.rs` file contains the buggy code. The `bugSolution.rs` file provides a corrected version that uses safe Rust methods to avoid this issue.

## How to Reproduce

1. Clone this repository.
2. Navigate to the repository's directory.
3. Run `rustc bug.rs && ./bug` to compile and execute the buggy code.
4. Run `rustc bugSolution.rs && ./bugSolution` to compile and execute the corrected code. 

## Understanding the Problem

The unsafe code in `bug.rs` creates a raw pointer to the first element of the vector.  After the vector goes out of scope it is dropped, freeing up its memory. Then the program attempts to modify the memory using the raw pointer. This is a severe error in the code that is prone to undefined behavior. 

## Solution

The `bugSolution.rs` provides a corrected version. It shows how to avoid raw pointers and stick to safe Rust practices. 

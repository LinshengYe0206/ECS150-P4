# Project 4
## This project implements a file system 
##### Due to extraneous circumstances from both partners we were not able to 
implement these techniques. However, we at least discussed conceptually how we 
would have implemented the program for the first few phases. 

## Phase 0/Phase 1
The file system has four parts: Superblock, FAT, Root Directory and Data 
 blocks
 
### Superblock
For the superblock, we decided that we would have used a struct with the fields 
defined in the assignment in section 3.2.1. In the struct, we would use int8_t 
for the 1 Byte variables (number of blocks for FAT) and int16_t for the 2 Byte 
fields. 

### FAT
For the FAT data structure we would use an array of int16_t  to represent the 
data blocks. We would have a global variable free_blocks(int16_t)  to keep 
count of the number of free blocks. Each time a data block is allocated or 
freed this counter is updated.
 
### Root Directory
For the root directory we would define a 128 entry array of root_dir_struct_t, 
which has the fields defined in 3.2.3

### Data Blocks
We would create a global static variable data_block_start_offset which is used 
so that the block offset of the data block on the disk can be easily calculated 
by adding the offset to the data block number.

## Phase 1: 
The fs_mount() function will have a section that checks that the first block 
(superblock) contains the required signature

## Phase 2
In the function fs_create() we would,

1. Check that the file size is smaller than the number of available blocks
2. Check for free blocks by traversing the FAT, and allocating and linking the 
free blocks in the FAT and writing the data into the corresponding data blocks.
3. Increment the free_blocks

Finding a free entry in the root directory and writing the file parameters into 
the root directory. 

1. In the function fs_delete() we would, 
2. Traverse and mark the blocks used by the file as free blocks
3. Decrement free_blocks
4. Clear the file entry from the root directory

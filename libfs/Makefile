# Target library
lib := libfs.a

all: $(lib)

## TODO
libfs.a: disk.o fs.o
	ar rcs libfs.a disk.o fs.o

disk.o: disk.c disk.h
	gcc -Wall -Werror -c -o disk.o disk.c

fs.o: fs.c fs.h
	gcc -Wall -Werror -c -o fs.o fs.c

clean:
	rm *.o
	rm *.a
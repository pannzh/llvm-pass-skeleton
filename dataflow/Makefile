CC=clang
CFLAGS=-fsanitize=dataflow -g
LDFLAGS=-fsanitize=dataflow

all: a.out

rtlib.o : rtlib.c
	$(CC) $(CFLAGS) -c $< -o $@

example.o: example.c
	$(CC) $(CFLAGS) -Xclang -load -Xclang ../build/dataflow/libLoadStorePass.so -c $< -o $@

a.out: rtlib.o example.o
	$(CC) $(LDFLAGS) $^ -o $@

clean:
	rm -f rtlib.o example.o a.out
.PHONY: clean all

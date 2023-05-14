TARGETS = hello hello-func

all: $(TARGETS)
.PHONY: all

$(TARGETS): %: %.bpf.o 

%.bpf.o: %.bpf.c
	clang \
	    -target bpf \
		-I/usr/include/x86_64-linux-gnu \
		-I/home/martin/dev/WSL2-Linux-Kernel/tools/lib/ \
		-I/home/martin/dev/WSL2-Linux-Kernel/tools/bpf/resolve_btfids/libbpf \
		-g \
	    -O2 -o $@ -c $<

clean: 
	- rm *.bpf.o
	- rm -f /sys/fs/bpf/hello 
	- rm -f /sys/fs/bpf/hello-func


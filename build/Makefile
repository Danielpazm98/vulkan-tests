VULKAN_SDK_PATH = /home/daniel/1.1.126.0/x86_64

CC=g++
CFLAGS = -g -std=c++17 -I$(IDIR) -I$(VULKAN_SDK_PATH)/include -fpermissive

ODIR=../src
IDIR =../include

_OBJ = main.o
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))

LDFLAGS = -L$(VULKAN_SDK_PATH)/lib `pkg-config --static --libs glfw3` -lvulkan

all: VulkanTest


$(ODIR)/main.o: $(ODIR)/main.cpp
	$(CC) -c -o $@ $< $(CFLAGS) $(LDFLAGS)

VulkanTest: $(OBJ)
	$(CC) -o $@ $^ $(CFLAGS) $(LDFLAGS)
 

.PHONY: test clean

test:  main
	rm -f $(ODIR)/*.o
	make
	rm -f $(ODIR)/*.o
	./main	

clean:
	rm -f $(ODIR)/*.o



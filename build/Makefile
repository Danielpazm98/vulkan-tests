VULKAN_SDK_PATH = /home/daniel/1.1.126.0/x86_64
STB_INCLUDE_PATH = ../lib

CC=g++
CFLAGS = -g -std=c++17 -I$(IDIR) -I$(VULKAN_SDK_PATH)/include -I$(STB_INCLUDE_PATH) -fpermissive

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
 

.PHONY: test re ret clean

test: VulkanTest 
	LD_LIBRARY_PATH=$(VULKAN_SDK_PATH)/lib VK_LAYER_PATH=$(VULKAN_SDK_PATH)/etc/vulkan/explicit_layer.d ./VulkanTest

re:
	rm -f $(ODIR)/*.o
	make

ret: VulkanTest
	rm -f $(ODIR)/*.o
	make
	LD_LIBRARY_PATH=$(VULKAN_SDK_PATH)/lib VK_LAYER_PATH=$(VULKAN_SDK_PATH)/etc/vulkan/explicit_layer.d ./VulkanTest

clean:
	rm -f $(ODIR)/*.o



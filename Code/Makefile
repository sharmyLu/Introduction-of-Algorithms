###compile toolchains####
CC=g++

###file dir###
ROOT_DIR=$(shell pwd)
SRC_DIR=$(ROOT_DIR)
SUB_DIR=$(filter-out .,$(shell find . -type d))

###compile flag###
INC_DIR=$(patsubst %,-I%,$(SUB_DIR))
COMMON_INC=$(shell ls Common/*.h 2>/dev/null)
CFLAGS=-ICommon -Wall -std=c++11 -g

###src file###
SRC_FILE=$(foreach dir,$(SUB_DIR),$(shell ls $(dir)/*.cpp 2>/dev/null))

TARGET=$(ROOT_DIR)/algorithms_test
OBJS=$(patsubst %.cpp,%.o,$(SRC_FILE))

.PHONY:all clean

all:$(TARGET)

$(TARGET):$(OBJS) Entry.o
	$(CC) -o $@ $^

Entry.o:Entry.cpp AlgorithmsList.hpp $(OBJS)
	$(CC) $(CFLAGS) $(INC_DIR) -c $< -o $@	

%.o:%.cpp %.h $(COMMON_INC)
	$(CC) $(CFLAGS) -c $< -o $@	

clean:
	find . -name "*.o" -exec rm -rf {} \;
	rm -rf $(OBJ_DIR) $(ROOT_DIR)/algorithms_test




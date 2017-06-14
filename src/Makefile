STAGING_DIR=/home/liuw/workspace/hzspec/Repos/openWrt.git/staging_dir


LIB_PATH=$(STAGING_DIR)/target-mipsel_24kec+dsp_uClibc-0.9.33.2/usr/lib
INC_PATH=$(STAGING_DIR)/target-mipsel_24kec+dsp_uClibc-0.9.33.2/usr/include

CXX=mipsel-openwrt-linux-g++
CC= mipsel-openwrt-linux-gcc
CFLAGS= -g -I./inc -std=c99
CFLAGS += -I$(INC_PATH)
CXXFLAGS= -g -I./inc -std=c++11
CXXFLAGS += -I$(INC_PATH)

LDFLAGS=-L$(LIB_PATH) -lcurl -lpthread -lssl -lcrypto
shepherd: main.cpp routerInterface.cpp cmd.o cparser_tree.o libcli.a 
	$(CXX) $(CXXFLAGS) main.cpp routerInterface.cpp cmd.o cparser_tree.o libcli.a $(LDFLAGS) $(CXXFLAGS) -o shepherd -DDEBUG  
	$(CC) -std=c99 -c cparser_tree.c -I./inc 
cmd.o:  cmd.c	
	$(CC) -std=c99 -c cmd.c -I./inc 

.PHONY: clean distclean
clean:
	rm -f *.o
	rm -f shepherd

distclean:
	rm -f *.o
	rm -f shepherd

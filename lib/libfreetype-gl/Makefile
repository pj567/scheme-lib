##########################################################
# Copyright 2016-2080 evilbinary.
#作者:evilbinary on 12/24/16.
#邮箱:rootdebug@163.com
##########################################################


TARGET = libfreetype-gl.so 
OBJS =  vertex-buffer.o platform.o vertex-attribute.o \
	distance-field.o edtaa3func.o font-manager.o makefont.o \
	text-buffer.o texture-atlas.o texture-font.o utf8-utils.o \
	vector.o 
PLATFORM=
BITS =$(shell getconf LONG_BIT)


LIBS = -L../libgl -lgles -L../3rdparty/lib -lfreetype-gl  -L/opt/local/lib/ -lfreetype 
CFLAGS = -Wall -Wformat  -DGLAD \
	-I../libgl \
	-I../3rdparty/include/freetype-gl -g \
	-I/opt/local/include//freetype2/

CXXFLAGS= -Wall -Wformat

UNAME_S := $(shell uname -s)
ifeq ($(UNAME_S), Linux) #LINUX
	ECHO_MESSAGE = "Linux"
	LIBS += 
	CXXFLAGS += 
	CXXFLAGS += 
	CFLAGS +=  -fPIC
	ifeq ($(BITS), 32)
		PLATFORM=i3le
	else
		PLATFORM=a6le
	endif
endif

ifeq ($(UNAME_S), Darwin) #APPLE
	ECHO_MESSAGE = "Mac OS X"
	LIBS += 
	CXXFLAGS += 
	CXXFLAGS += 
	CFLAGS +=
	ifeq ($(BITS), 32)
		PLATFORM=i3osx
	else
		PLATFORM=a6osx
	endif
#	CXXFLAGS += -D__APPLE__
endif

ifeq ($(UNAME_S), MINGW32_NT-6.1)
   	ECHO_MESSAGE = "Windows"
	LIBS += 
	CXXFLAGS += 
	CXXFLAGS += 
	CFLAGS +=
	PLATFORM=i3nt
	TARGET = libgui.dll
endif

.cpp.o:
	$(CXX) $(CXXFLAGS) -c -o $@ $<
.c.o:
	$(CC) $(CFLAGS) -c -o $@ $<
all: $(TARGET)
	@echo Build complete for $(ECHO_MESSAGE)

$(TARGET): $(OBJS)
	$(CC)  $(CFLAGS) $(OBJS) -shared  -o $(TARGET)   $(LIBS)

boot:
	cp ../libchez/$(PLATFORM)/*.boot .
clean:
	rm -rf $(TARGET) $(OBJS)


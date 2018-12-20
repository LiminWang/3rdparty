
ROOT_PATH = ..
LIB_SRC   = $(ROOT_PATH)/decoder
LIB_PATH  = $(ROOT_PATH)/lib
LIB_INC   = $(ROOT_PATH)/include

CXXFLAGS += -msse
CXXFLAGS += -msse2
CXXFLAGS += -msse3
CXXFLAGS += -msse4
CXXFLAGS += -fno-exceptions -fpermissive -fvisibility=hidden -fPIC -c -O3
CXXFLAGS += -D__CONFIG_LINUX
CXXFLAGS += -I $(LIB_INC)

LIB_SRCS = $(LIB_SRC)/xavs.cpp $(LIB_SRC)/xavs_decoder.cpp \
    	   $(LIB_SRC)/xavs_decoder_aec.cpp  $(LIB_SRC)/xavs_decoder_vlc.cpp  \
           $(LIB_SRC)/xavs_globe.cpp $(LIB_SRC)/xavs_dsp.cpp \
           $(LIB_SRC)/xavs_dsp_mc.cpp $(LIB_SRC)/xavs_dsp_mc_w.cpp \
           $(LIB_SRC)/xavs_dsp_mmx.cpp $(LIB_SRC)/xavs_dsp_mc_mmx.cpp \
           $(LIB_SRC)/xavs_dsp_mc_w_mmx.cpp $(LIB_SRC)/xavs_dsp_mc_w_mmx.cpp \
           $(LIB_SRC)/xavs_dsp_sse2.cpp $(LIB_SRC)/xavs_dsp_mc_sse2.cpp \
           $(LIB_SRC)/xavs_dsp_mc_w_sse2.cpp

LIB_OBJS := $(patsubst %.cpp,%.o,$(LIB_SRCS))

LIB=$(LIB_PATH)/libavsplusdec.a

all: $(LIB) $(PROG)

$(LIB) : $(LIB_OBJS)
	mkdir -p $(LIB_PATH)
	ar rc $@ $(LIB_OBJS)
	ranlib $@

depend:
	$(CC) -MM $(CFLAGS) $(LIB_SRCS) 1>.depend

clean: 
	rm -f $(LIB_OBJS) $(LIB)

distclean: clean
	rm -f Makefile .depend

# include dependency files if they exist
#
ifneq ($(wildcard .depend),)
include .depend
endif

TARGET        = analysis
SRC           = $(TARGET).cc


CXXFLAGS        = -fPIC -O3 -Wall -Wextra -pedantic

OBJ           = $(patsubst %.cc, %.o, $(SRC))
ROOTCFLAGS   := $(shell root-config --cflags)
ROOTLIBS     := $(shell root-config --libs) -lMinuit2 -lSpectrum
CXXFLAGS     += $(ROOTCFLAGS)
LIBS         += $(ROOTLIBS)
LIBS         += -L$(RHICF_TOP) -lRHICfEvent
LIBS         += -L$(BOOST_LIBRARY) -lboost_program_options -lboost_filesystem
LIBS         += -L$(RHICF_LIB) -lRHICfEvent

LDFLAGS       = -O

CXXFLAGS     += -I$(RHICF_LIB)
CXXFLAGS     += -I$(BOOST_INCLUDE)

.PHONY: $(TARGET)
$(TARGET):    $(OBJ)
		g++ -o $@ $(OBJ) $(LDFLAGS) $(LIBS)

%.o : %.cc $(INCS)
	g++ $(CXXFLAGS) -c -g -o $@ $<

clean:	
	-rm -f $(TARGET) $(OBJ) *~
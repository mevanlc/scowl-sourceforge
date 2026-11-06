CXXFLAGS ?= -O

%: %.cc
	$(CXX) $(CPPFLAGS) $(CXXFLAGS) $< -o $@ $(LDFLAGS) $(LDLIBS)

deaccent: deaccent.cc deaccent.hh
find-accented: find-accented.cc deaccent.hh








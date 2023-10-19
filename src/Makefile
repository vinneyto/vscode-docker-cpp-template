CXX = g++
DEBUG_CXXFLAGS = -g -O1 -fsanitize=address -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wall -std=c++17 -ltbb -lpthread
RELEASE_CXXFLAGS = -O2 -std=c++17 -ltbb -lpthread

debug: CXXFLAGS = $(DEBUG_CXXFLAGS)
debug: hello

release: CXXFLAGS = $(RELEASE_CXXFLAGS)
release: hello

SRC = $(wildcard *.cpp)
OBJ = $(SRC:.cpp=.o)

all: hello

hello: $(OBJ)
	$(CXX) $(CXXFLAGS) $^ -o $@

%.o: %.cpp
	$(CXX) $(CXXFLAGS) -c $< -o $@

clean:
	rm -f $(OBJ) hello
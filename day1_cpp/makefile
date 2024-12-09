
CXX ?= g++

ifeq ($(CXX),cl)
	CXXFLAGS = /nologo /W3
	TARGET = day1.exe
else
	CXXFLAGS = -Wall -Wextra -g -std=c++17
	TARGET = day1
endif

OBJDIR = obj
SRCDIR = src

SRC = $(wildcard $(SRCDIR)/*.cpp)
IMGUISRC = imgui\backends\imgui_impl_glfw.cpp imgui\backends\imgui_impl_opengl3.cpp imgui\imgui*.cpp
OBJS = $(SRC:$(SRCDIR)/%.cpp=$(OBJDIR)/%.obj)

INCLUDES =/Iimgui /Iimgui\backends /Iimgui\examples\libs\glfw\include
LIBS = /LIBPATH:imgui\\examples\\libs\\glfw\\lib-vc2010-32 glfw3.lib opengl32.lib gdi32.lib shell32.lib




all: $(TARGET)

$(TARGET): $(OBJS)
	@mkdir -p $(OBJDIR)
	$(CXX) $(CXXFLAGS) $(INCLUDES) $(IMGUISRC) $(OBJS) /Fe:$(TARGET) /link $(LIBS)

$(OBJDIR)/%.obj: $(SRCDIR)/%.cpp
	$(CXX) $(CXXFLAGS) $(INCLUDES)  $< /Fo:$@ /link $(LIBS)



clean: 
	rm -rf $(OBJS) $(TARGET)


.PHONY: all clean

#XOUT = $(notdir $(shell pwd)).out
XOUT = EIS.out
CPPFILES = Employee.cpp Database.cpp UserInterface.cpp
HFILES = Employee.h Database.h
OFILES = $(CPPFILES:.cpp=.o)
CC = g++ -std=c++14

all: $(OFILES)
	@echo -e 'Compiling - $(XOUT)'
	$(CC) -o $(XOUT) $(OFILES)

.cpp.o: $(SRCS) $(HDRS)
	$(CC) -c $*.cpp

EmployeeTest: EmployeeTest.cpp $(filter Employee%.o, $(OFILES))
	$(CC) -c EmployeeTest.cpp && \
	$(CC) -o empTest EmployeeTest.o $(filter Employee%.o, $(OFILES))

DatabaseTest: DatabaseTest.cpp $(filter Employee%.o Database%.o, $(OFILES))
	$(CC) -c DatabaseTest.cpp && \
	$(CC) -o dbTest DatabaseTest.o $(filter Employee%.o Database%.o, $(OFILES))

clean:

ifeq (exist, $(shell [ -e ./empTest ] && echo exist))
	rm -rf empTest EmployeeTest.o
endif

ifeq (exist, $(shell [ -e ./dbTest ] && echo exist))
	rm -rf dbTest DatabaseTest.o
endif

ifeq (exist, $(shell [ -e ./$(XOUT) ] && echo exist))
	rm -rf $(XOUT) $(OFILES)
endif
.PHONY: all clear rebuild
CC=gcc
GCOV= -fprofile-arcs -ftest-coverage
CFLAGS=-lstdc++ -lgtest -std=c++17 -Wall -Werror -Wextra 
BUILD=build/
EXECUTABLE=result_testing
all: test

test:  testing/tests.cpp
	@mkdir $(BUILD)
	@${CC} $<  ${CFLAGS} -o $(BUILD)$(EXECUTABLE)
	@./$(BUILD)$(EXECUTABLE)


gcov_report: testing/tests.cpp
	@lcov -t $(EXECUTABLE) -o $(EXECUTABLE).info -c -d .
	@genhtml -o report $(EXECUTABLE).info
	@open report/index.html
	

clean:
	@/bin/rm -rf *.o *.a build *.gcno *gcda report *.info main *.dSYM *.out gcov_report

leaks:
	leaks --atExit -- ./$(BUILD)$(EXECUTABLE)

rebuild: clean all

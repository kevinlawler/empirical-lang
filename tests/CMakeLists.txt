if(WIN32)
    set(EXECUTABLE empirical.exe)
else(WIN32)
    set(EXECUTABLE empirical)
endif(WIN32)

add_test(NAME test_joins
         COMMAND ${CMAKE_BINARY_DIR}/${EXECUTABLE} --verify-markdown joins.md
         WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})

# TODO need a Windows version of the test script
if(NOT WIN32)
add_test(NAME test_emp
         COMMAND ./test_emp.sh ${CMAKE_BINARY_DIR}/${EXECUTABLE}
         WORKING_DIRECTORY ${CMAKE_CURRENT_SOURCE_DIR})
endif(NOT WIN32)

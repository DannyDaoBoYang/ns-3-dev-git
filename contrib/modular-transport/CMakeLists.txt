check_include_file_cxx(stdint.h HAVE_STDINT_H)
if(HAVE_STDINT_H)
    add_definitions(-DHAVE_STDINT_H)
endif()

set(examples_as_tests_sources)
if(${ENABLE_EXAMPLES})
    set(examples_as_tests_sources
        #test/modular-transport-examples-test-suite.cc
        )
endif()

build_lib(
    LIBNAME modular-transport
    SOURCE_FILES model/modular-transport.cc
                 model/mt-header.cc
                 model/TCP-header.cc
                 helper/modular-transport-helper.cc
    HEADER_FILES model/modular-transport.h
                 model/mt-header.h
                 model/TCP-header.h
                 helper/modular-transport-helper.h
    LIBRARIES_TO_LINK ${libinternet}
    TEST_SOURCES test/modular-transport-test-suite.cc
                 ${examples_as_tests_sources}
)


cmake_minimum_required( VERSION "2.6.4" )

project( search CXX C )

include_directories(
    src
)

set( SEARCH_SOURCES
    src/SentenceTransformer.cc
)

set( SEARCH_LIBS
    torch
)

set( SEARCH_COMPILE_OPTIONS
    -Wall
    -Wextra
    -O3
    -std=c++20
    # -g
)

add_executable( build/search ${SEARCH_SOURCES} src/main.cc )

target_link_libraries( build/search -Wl,-rpath=/usr/local/lib/logport:. ${SEARCH_LIBS} )

set_target_properties( build/search
    PROPERTIES
    COMPILE_OPTIONS  "${SEARCH_COMPILE_OPTIONS}"
)


cmake_minimum_required(VERSION 3.27)
project(m17n)

set(m17n_srcs
    character.c
    charset.c
    chartab.c
    coding.c
    database.c
    input.c
    language.c
    locale.c
    m17n.c
    m17n-core.c
    mtext.c
    mtext-wseg.c
    plist.c
    symbol.c
    textprop.c
)
list(TRANSFORM m17n_srcs PREPEND "m17n-lib/src/")

add_library(m17n ${m17n_srcs})
target_include_directories(m17n PRIVATE ${PROJECT_SOURCE_DIR} m17n-lib/src)

install(FILES
    m17n-lib/src/m17n-core.h
    m17n-lib/src/m17n.h
    DESTINATION "${CMAKE_INSTALL_PREFIX}/include"
)
install(TARGETS m17n DESTINATION "${CMAKE_INSTALL_PREFIX}/lib")

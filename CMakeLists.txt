CMAKE_MINIMUM_REQUIRED(VERSION 3.20)

project(DXFRW VERSION 1.0.1)

add_compile_options(-Wall -Wextra -pedantic -Werror)

set(CMAKE_CXX_STANDARD 17)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

# SOURCE FILES
set(libdxfrw_srcs
        src/intern/drw_dbg.cpp
        src/intern/drw_textcodec.cpp
        src/intern/dwgbuffer.cpp
        src/intern/dwgreader.cpp
        src/intern/dwgreader15.cpp
        src/intern/dwgreader18.cpp
        src/intern/dwgreader21.cpp
        src/intern/dwgreader24.cpp
        src/intern/dwgreader27.cpp
        src/intern/dwgutil.cpp
        src/intern/dxfreader.cpp
        src/intern/dxfwriter.cpp
        src/intern/rscodec.cpp
        src/drw_base.cpp
        src/drw_classes.cpp
        src/drw_entities.cpp
        src/drw_header.cpp
        src/drw_objects.cpp
        src/libdwgr.cpp
        src/libdxfrw.cpp
)

# HEADER FILES
set(libdxfrw_hdrs
        src/intern/drw_cptable932.h
        src/intern/drw_cptable936.h
        src/intern/drw_cptable949.h
        src/intern/drw_cptable950.h
        src/intern/drw_cptables.h
        src/intern/drw_dbg.h
        src/intern/drw_textcodec.h
        src/intern/dwgbuffer.h
        src/intern/dwgreader.h
        src/intern/dwgreader15.h
        src/intern/dwgreader18.h
        src/intern/dwgreader21.h
        src/intern/dwgreader24.h
        src/intern/dwgreader27.h
        src/intern/dwgreader32.h
        src/intern/dwgutil.h
        src/intern/dxfreader.h
        src/intern/dxfwriter.h
        src/intern/rscodec.h
        src/main_doc.h
)

set(installdxfrw_hdrs
        src/drw_base.h
        src/drw_classes.h
        src/drw_entities.h
        src/drw_header.h
        src/drw_interface.h
        src/drw_objects.h
        src/libdwgr.h
        src/libdxfrw.h
)

set(LIBDXFRW_INSTALL_INCLUDEDIR ${CMAKE_INSTALL_INCLUDEDIR}/libdxfrw)

add_library(dxfrw ${libdxfrw_srcs} ${libdxfrw_hdrs})
set_target_properties(dxfrw PROPERTIES
        VERSION "${PROJECT_VERSION}"
        SOVERSION "${PROJECT_VERSION_MAJOR}"
        EXPORT_NAME libdxfrw
)
target_compile_features(dxfrw PUBLIC cxx_std_14)
target_include_directories(dxfrw
        PUBLIC
        $<INSTALL_INTERFACE:${LIBDXFRW_INSTALL_INCLUDEDIR}>
)

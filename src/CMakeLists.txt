# Copyright (c) Glyn Matthews 2012, 2013.
# Distributed under the Boost Software License, Version 1.0.
# (See accompanying file LICENSE_1_0.txt or copy at
# http://www.boost.org/LICENSE_1_0.txt)

set(Uri_SRCS
  ${CMAKE_CURRENT_SOURCE_DIR}/uri.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/uri_builder.cpp
  ${CMAKE_CURRENT_SOURCE_DIR}/detail/uri_parse.cpp)
if(NOT CPP-NETLIB_BUILD_SINGLE_LIB)
  add_library(cppnetlib-uri ${Uri_SRCS})
  target_link_libraries(cppnetlib-uri ${Boost_LIBRARIES})
  install(
    TARGETS
    cppnetlib-uri
    DESTINATION ${CMAKE_INSTALL_PREFIX}/lib
    )

  install(DIRECTORY network
    DESTINATION ${CMAKE_INSTALL_PREFIX}/include
    )
endif()

#propagate sources to parent scope for one-lib-build
set(Uri_SRCS ${Uri_SRCS} PARENT_SCOPE)

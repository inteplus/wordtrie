CMAKE_MINIMUM_REQUIRED(VERSION 3.0.0 FATAL_ERROR)

PROJECT(libwordtrie LANGUAGES CXX)

# Boost dependency
FIND_PACKAGE(Boost 1.55 REQUIRED serialization)

SET(LIBWORDTRIE_SRC_DIR ${CMAKE_CURRENT_LIST_DIR})

FILE(GLOB LIBWORDTRIE_SRC
  "${LIBWORDTRIE_SRC_DIR}/wordtrie*.cpp"
)

ADD_LIBRARY(${PROJECT_NAME} STATIC ${LIBWORDTRIE_SRC})

TARGET_COMPILE_OPTIONS(${PROJECT_NAME} PUBLIC -funsigned-char)

TARGET_INCLUDE_DIRECTORIES(${PROJECT_NAME} INTERFACE ${LIBWORDTRIE_SRC_DIR})

INCLUDE_DIRECTORIES(${Boost_INCLUDE_DIR})

TARGET_LINK_LIBRARIES(${PROJECT_NAME} ${Boost_LIBRARIES})

SET_TARGET_PROPERTIES(${PROJECT_NAME} PROPERTIES OUTPUT_NAME "wordtrie")

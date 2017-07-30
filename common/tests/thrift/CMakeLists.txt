cmake_minimum_required(VERSION 2.8)

# Build thrift file
set(GEN_FILES
"gen-cpp2/DummyService_client.cpp"
"gen-cpp2/dummy_service_constants.h"
"gen-cpp2/DummyService_custom_protocol.h"
"gen-cpp2/dummy_service_data.h"
"gen-cpp2/DummyService_processmap_binary.cpp"
"gen-cpp2/DummyService.tcc"
"gen-cpp2/dummy_service_types_custom_protocol.h"
"gen-cpp2/dummy_service_types.tcc"
"gen-cpp2/dummy_service_constants.cpp"
"gen-cpp2/DummyService.cpp"
"gen-cpp2/dummy_service_data.cpp"
"gen-cpp2/DummyService.h"
"gen-cpp2/DummyService_processmap_compact.cpp"
"gen-cpp2/dummy_service_types.cpp"
"gen-cpp2/dummy_service_types.h"
    )


add_custom_command(
  OUTPUT ${GEN_FILES}
  COMMAND python -mthrift_compiler.main --gen cpp2
          -o ./ ${CMAKE_CURRENT_SOURCE_DIR}/dummy_service.thrift
  DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/dummy_service.thrift)

add_library(dummy_service_thrift ${GEN_FILES})

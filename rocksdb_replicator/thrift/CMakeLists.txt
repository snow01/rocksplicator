cmake_minimum_required(VERSION 3.1)

# Build thrift file
set(GEN_FILES
"gen-cpp2/Replicator_client.cpp"
"gen-cpp2/replicator_constants.h"
"gen-cpp2/Replicator_custom_protocol.h"
"gen-cpp2/replicator_data.h"
"gen-cpp2/Replicator_processmap_binary.cpp"
"gen-cpp2/Replicator.tcc"
"gen-cpp2/replicator_types_custom_protocol.h"
"gen-cpp2/replicator_types.tcc"
"gen-cpp2/replicator_constants.cpp"
"gen-cpp2/Replicator.cpp"
"gen-cpp2/replicator_data.cpp"
"gen-cpp2/Replicator.h"
"gen-cpp2/Replicator_processmap_compact.cpp"
"gen-cpp2/replicator_types.cpp"
"gen-cpp2/replicator_types.h"
)

add_custom_command(
  OUTPUT ${GEN_FILES}
  COMMAND python -mthrift_compiler.main --gen cpp2:process_in_event_base
          -o ./ ${CMAKE_CURRENT_SOURCE_DIR}/replicator.thrift
  DEPENDS ${CMAKE_CURRENT_SOURCE_DIR}/replicator.thrift)

add_library(replicator_thrift ${GEN_FILES})

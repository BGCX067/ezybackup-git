set (ezybackup_TARGET ezybackup)

if (WIN32)
  set (ezybackup_TARGET ${ezybackup_TARGET}.exe)
endif (WIN32)

set (ezybackup_SRCS
  main.cpp
)

include_directories (${CMAKE_CURRENT_BINARY_DIR})
include_directories (${CMAKE_CURRENT_SOURCE_DIR})

add_executable (${ezybackup_TARGET} WIN32
  ${ezybackup_SRCS}
)


# SPDX-License-Identifier: BSD-3-Clause
# Copyright Contributors to the OpenColorIO Project.

set(SOURCES
	main.cpp
)

add_executable(ociolutimage ${SOURCES})

if(NOT BUILD_SHARED_LIBS)
	target_compile_definitions(ociolutimage
		PRIVATE
			OpenColorIO_SKIP_IMPORTS
	)
endif()

set_target_properties(ociolutimage PROPERTIES
	COMPILE_FLAGS "${PLATFORM_COMPILE_FLAGS}")

target_link_libraries(ociolutimage
	PRIVATE
		apputils
		OpenColorIO
		OpenImageIO::OpenImageIO
		utils::strings
)

install(TARGETS ociolutimage
	RUNTIME DESTINATION bin
)

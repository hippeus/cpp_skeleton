set(SRC
	a.cpp
	)

set(LIB	mod_a)

add_library(${LIB} SHARED
	${SRC}
)

target_include_directories( ${LIB} PUBLIC
	${CMAKE_CURRENT_SOURCE_DIR}
)

install(TARGETS ${LIB}
	LIBRARY DESTINATION lib
	)

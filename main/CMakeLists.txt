set(APP skel)

set(SRC
   	main.cpp
)

add_executable(${APP}
	${SRC}
)

target_link_libraries(${APP}
	mod_a
)

install(TARGETS ${APP}
	DESTINATION bin
	)

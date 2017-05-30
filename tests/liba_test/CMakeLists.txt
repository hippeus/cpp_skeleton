file(GLOB SRCS *cpp)

set(TEST_APP mod_a_test)

add_executable(${TEST_APP}
	${SRCS}
)

add_test(ATest ${TEST_APP})

target_link_libraries(${TEST_APP}
	mod_a
	GTest::GTest
	GTest::Main
	${GMOCK_BOTH_LIBRARIES}
)

install(TARGETS ${TEST_APP}
	RUNTIME DESTINATION bin
)

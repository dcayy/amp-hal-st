add_executable(integration_test.flasher)
emil_build_for(integration_test.flasher HOST All)

target_sources(integration_test.flasher PRIVATE
    Main.cpp
)

target_link_libraries(integration_test.flasher PRIVATE
    args
    integration_test.logic
    hal.generic
    services.network_instantiations
)

if (EMIL_BUILD_WIN)
    target_link_libraries(integration_test.flasher PRIVATE hal.windows)
endif()

if (EMIL_BUILD_UNIX OR EMIL_BUILD_DARWIN)
    target_link_libraries(integration_test.flasher PRIVATE hal.unix)
endif()

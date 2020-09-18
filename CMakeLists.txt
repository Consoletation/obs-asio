cmake_minimum_required(VERSION 3.5)

project(obs-asio)

# in cmake gui set the following:
# BASS_ASIO_LIB == path of bassasio.lib
# BASS_ASIO_INCLUDE_DIR == path of bassasio.h
# put also bassasio.dll in obs-plugins/bin folder
# be careful there are two versions of the lib and dll (x86 and x64)

include_directories(
	${BASS_ASIO_INCLUDE_DIR}
)
set(obs-asio-sdk_HEADERS
	)

set(obs-asio_HEADERS
	)

set(obs-asio_SOURCES
	asio-input.cpp
)

add_library(obs-asio MODULE
	${obs-asio_SOURCES}
	${obs-asio_HEADERS}
	${obs-asio-sdk_HEADERS}
)
target_link_libraries(obs-asio
	libobs
	${BASS_ASIO_LIB}
)

set_target_properties(obs-asio PROPERTIES FOLDER "plugins")
install_obs_plugin_with_data(obs-asio data)

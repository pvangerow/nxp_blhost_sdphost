cmake_minimum_required(VERSION 3.24)


# Platform dependent compile definitions (Look at MakeFile)
add_compile_definitions(
	BOOTLOADER_HOST
)

if (WIN32 OR MSVC)
	add_compile_definitions(
		WIN32
	)
endif()
if (UNIX AND NOT APPLE)
	add_compile_definitions(
		LINUX
	)
endif()
if (UNIX AND APPLE)
	add_compile_definitions(
		MACOSX
	)
endif()

# Additional settings
project(nxp_sdp_host)
enable_language(C CXX)

add_executable(blhost
	proj/blhost/src/blhost.cpp
	src/blfwk/src/Bootloader.cpp
	src/blfwk/src/BusPal.cpp
	src/blfwk/src/BusPalPeripheral.cpp
	src/blfwk/src/Command.cpp
	src/blfwk/src/DataSource.cpp
	src/blfwk/src/DataTarget.cpp
	src/blfwk/src/ELFSourceFile.cpp
	src/blfwk/src/GHSSecInfo.cpp
	src/blfwk/src/IntelHexSourceFile.cpp
	src/blfwk/src/Logging.cpp
	src/blfwk/src/SBSourceFile.cpp
	src/blfwk/src/SDPCommand.cpp
	src/blfwk/src/SDPUsbHidPacketizer.cpp
	src/blfwk/src/SRecordSourceFile.cpp
	src/blfwk/src/SearchPath.cpp
	src/blfwk/src/SerialPacketizer.cpp
	src/blfwk/src/SourceFile.cpp
	src/blfwk/src/StELFFile.cpp
	src/blfwk/src/StExecutableImage.cpp
	src/blfwk/src/StIntelHexFile.cpp
	src/blfwk/src/StSRecordFile.cpp
	src/blfwk/src/UartPeripheral.cpp
	src/blfwk/src/UsbHidPacketizer.cpp
	src/blfwk/src/UsbHidPeripheral.cpp
	src/blfwk/src/Value.cpp
	src/blfwk/src/format_string.cpp
	src/blfwk/src/hid-windows.c
	src/blfwk/src/jsoncpp.cpp
	src/blfwk/src/options.cpp
	src/blfwk/src/serial.c
	src/blfwk/src/utils.cpp
	src/crc/src/crc16.c
)

add_executable(sdphost
	sdphost.cpp
	src/blfwk/src/Bootloader.cpp
	src/blfwk/src/BusPal.cpp
	src/blfwk/src/BusPalPeripheral.cpp
	src/blfwk/src/Command.cpp
	src/blfwk/src/DataSource.cpp
	src/blfwk/src/DataTarget.cpp
	src/blfwk/src/ELFSourceFile.cpp
	src/blfwk/src/GHSSecInfo.cpp
	src/blfwk/src/IntelHexSourceFile.cpp
	src/blfwk/src/Logging.cpp
	src/blfwk/src/SBSourceFile.cpp
	src/blfwk/src/SDPCommand.cpp
	src/blfwk/src/SDPUsbHidPacketizer.cpp
	src/blfwk/src/SRecordSourceFile.cpp
	src/blfwk/src/SearchPath.cpp
	src/blfwk/src/SerialPacketizer.cpp
	src/blfwk/src/SourceFile.cpp
	src/blfwk/src/StELFFile.cpp
	src/blfwk/src/StExecutableImage.cpp
	src/blfwk/src/StIntelHexFile.cpp
	src/blfwk/src/StSRecordFile.cpp
	src/blfwk/src/UartPeripheral.cpp
	src/blfwk/src/UsbHidPacketizer.cpp
	src/blfwk/src/UsbHidPeripheral.cpp
	src/blfwk/src/Value.cpp
	src/blfwk/src/format_string.cpp
	src/blfwk/src/hid-windows.c
	src/blfwk/src/jsoncpp.cpp
	src/blfwk/src/options.cpp
	src/blfwk/src/serial.c
	src/blfwk/src/utils.cpp
	src/crc/src/crc16.c
)

target_include_directories(blhost PUBLIC
	src/
	src/include/
	src/blfwk/
)

target_include_directories(sdphost PUBLIC
	src/
	src/include/
	src/blfwk/
)

add_library(openmotion_libcamera INTERFACE)

find_package(PkgConfig REQUIRED)
find_package(OpenCV REQUIRED)

pkg_check_modules(LIBCAMERA REQUIRED libcamera)

target_include_directories(openmotion_libcamera INTERFACE
    ./include
    ${LIBCAMERA_INCLUDE_DIRS}
    ${OPENCV_INCLUDE_DIR})

target_sources(openmotion_libcamera
    INTERFACE
    ./src/openmotion_libcamera.cpp
    ./src/libcamera_app.cpp
    ./src/libcamera_app_options.cpp
)

target_link_libraries(openmotion_libcamera INTERFACE pthread ${LIBCAMERA_LINK_LIBRARIES} ${OpenCV_LIBS})
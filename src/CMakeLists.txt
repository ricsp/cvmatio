# build the project
set(BUILD_EXECUTABLE False)
if(BUILD_EXECUTABLE)
    set(SRC_FILES MatlabIO.cpp main.cpp)
    add_executable(${PROJECT_NAME} ${SRC_FILES})
else()
    set(SRC_FILES MatlabIO.cpp)
    add_library(${PROJECT_NAME} SHARED ${SRC_FILES})
endif()

#link
target_link_libraries(${PROJECT_NAME}   ${Boost_LIBRARIES} 
                                        ${OpenCV_LIBS} 
                                        ${ZLIB_LIBRARIES}
)

# install
install(TARGETS ${PROJECT_NAME} RUNTIME DESTINATION bin
                                LIBRARY DESTINATION lib
)

SET(HS ${CMAKE_SOURCE_DIR}/include/EFStream.hpp  ${CMAKE_SOURCE_DIR}/include/MatlabIOContainer.hpp  ${CMAKE_SOURCE_DIR}/include/MatlabIO.hpp  ${CMAKE_SOURCE_DIR}/include/typetraits.hpp)
INSTALL(FILES ${HS} DESTINATION include/${PROJECT_NAME})

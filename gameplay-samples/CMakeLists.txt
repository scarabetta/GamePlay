include(BuildHelpers.CMakeLists.txt)

include_directories( 
    ${CMAKE_SOURCE_DIR}/gameplay/src
    ${CMAKE_SOURCE_DIR}/external-deps/lua/include
    ${CMAKE_SOURCE_DIR}/external-deps/bullet/include
    ${CMAKE_SOURCE_DIR}/external-deps/libpng/include
    ${CMAKE_SOURCE_DIR}/external-deps/oggvorbis/include
    ${CMAKE_SOURCE_DIR}/external-deps/zlib/include
    ${CMAKE_SOURCE_DIR}/external-deps/openal/include
    ${CMAKE_SOURCE_DIR}/external-deps/glew/include
)

add_definitions(-D__linux__)

#TODO make this section variant per OS
link_directories(
    ${CMAKE_SOURCE_DIR}/external-deps/lua/lib/linux
    ${CMAKE_SOURCE_DIR}/external-deps/zlib/lib/linux
    ${CMAKE_SOURCE_DIR}/external-deps/libpng/lib/linux
    ${CMAKE_SOURCE_DIR}/external-deps/bullet/lib/linux
    ${CMAKE_SOURCE_DIR}/external-deps/oggvorbis/lib/linux
    ${CMAKE_SOURCE_DIR}/external-deps/glew/lib/linux
)

#TODO make this section variant per OS
set(GAMEPLAY_LIBRARIES
    gameplay
    m
    lua
    png
    z
    vorbis
    ogg
    BulletDynamics
    BulletCollision
    LinearMath
    openal
    GLEW
    GL
    rt
    dl
    X11
) 
#TODO: The above should be enough, no?
add_definitions(-lstdc++ -lgameplay -lm -llua -lz -lpng -logg -lvorbis -lBulletCollision -lBulletDynamics -lLinearMath-lopenal -LGLEW -lGL -lrt -ldl -lX11)


add_subdirectory(sample00-mesh)
add_subdirectory(sample01-longboard)
add_subdirectory(sample02-spaceship)
add_subdirectory(sample03-character)
add_subdirectory(sample04-particles)
add_subdirectory(sample05-lua)
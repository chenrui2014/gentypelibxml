cmake_minimum_required(VERSION 2.8)
project(gentypelibxml)
find_package(catkin)
find_package(genmsg)

set(gentypelibxml_INSTALL_DIR CACHE PATH share/typelib FORCE)

generate_generator(typelibxml share/typelibxml "Orocos Typelib XML" .xml)

# add_subdirectory(scripts)
#
catkin_stack()
catkin_project(gentypelibxml
  CFG_EXTRAS gentypelibxml-extras.cmake
)

file(WRITE ${CMAKE_CURRENT_BINARY_DIR}/gentypelibxml "Orocos Typelib XML")
install(FILES ${CMAKE_CURRENT_BINARY_DIR}/gentypelibxml
  DESTINATION etc/langs
)
#
install(FILES stack.yaml DESTINATION share/${PROJECT_NAME})

catkin_export_python()

add_subdirectory(scripts)

cmake_minimum_required(VERSION "3.12")

project("ExerciseCMake")

find_package(Boost REQUIRED COMPONENTS filesystem)

find_package(yaml-cpp REQUIRED CONFIG)

find_package(deal.II 9.1.0 REQUIRED
  HINTS ${DEAL_II_DIR} ../ ../../ $ENV{DEAL_II_DIR}
  )
DEAL_II_INITIALIZE_CACHED_VARIABLES()

add_executable(main main.cpp fem/fem.cpp flatset/flatset.cpp filesystem/filesystem.cpp yamlParser/yamlParser.cpp)

target_link_libraries(main Boost::filesystem)

target_link_libraries(main yaml-cpp)

DEAL_II_SETUP_TARGET(main)

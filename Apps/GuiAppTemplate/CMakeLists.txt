cmake_minimum_required(VERSION 3.12)
project(GuiAppTemplate VERSION 0.0.1)

juce_add_gui_app(${PROJECT_NAME} PRODUCT_NAME "Gui App Example")

juce_generate_juce_header(${PROJECT_NAME})

#automatically grabs all the sources from the "Source" directory
#you can also manually add your source files as shown in the JUCE examples
aux_source_directory("${CMAKE_CURRENT_SOURCE_DIR}/Source" Sources)
target_sources(${PROJECT_NAME} PRIVATE ${Sources})

target_compile_definitions(${PROJECT_NAME} PRIVATE
        JUCE_WEB_BROWSER=0
        JUCE_USE_CURL=0
        JUCE_APPLICATION_NAME_STRING="$<TARGET_PROPERTY:${PROJECT_NAME},JUCE_PROJECT_NAME>"
        JUCE_APPLICATION_VERSION_STRING="$<TARGET_PROPERTY:${PROJECT_NAME},JUCE_VERSION>")

target_link_libraries(${PROJECT_NAME} PRIVATE juce::juce_gui_extra)

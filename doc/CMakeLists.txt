#
# Build the documentation
#
find_package(Doxygen)

if(${CMAKE_VERSION} VERSION_LESS "3.9.0")
    message(WARNING "You need CMake version >= 3.9.0 if you want to support Doxygen")
elseif(DOXYGEN_FOUND)
    set(DOXYGEN_PROJECT_NAME ${APPLICATION_NAME})
    set(DOXYGEN_PROJECT_NUMBER ${APPLICATION_VERSION})
    set(DOXYGEN_PROJECT_BRIEF "Unit testing library with mock support")

    set(DOXYGEN_TAB_SIZE 4)
    set(DOXYGEN_OPTIMIZE_OUTPUT_FOR_C YES)
    set(DOXYGEN_MARKDOWN_SUPPORT YES)

    set(DOXYGEN_PREDEFINED DOXYGEN
                           CMOCKA_PRINTF_ATTRIBUTE(x,y))

    set(DOXYGEN_EXCLUDE ${CMAKE_CURRENT_SOURCE_DIR}/that_style)
    set(DOXYGEN_HTML_HEADER ${CMAKE_CURRENT_SOURCE_DIR}/that_style/header.html)
    set(DOXYGEN_HTML_EXTRA_STYLESHEET ${CMAKE_CURRENT_SOURCE_DIR}/that_style/that_style.css)
    set(DOXYGEN_HTML_EXTRA_FILES ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/nav_edge_left.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/nav_edge_right.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/nav_edge_inter.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/sync_off.png
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/sync_on.png
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/splitbar_handle.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/doc.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/mag_glass.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/folderclosed.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/img/folderopen.svg
                                 ${CMAKE_CURRENT_SOURCE_DIR}/that_style/js/striped_bg.js)

    set(_doxyfile_template "${CMAKE_BINARY_DIR}/CMakeDoxyfile.in")
    set(_target_doxyfile "${CMAKE_CURRENT_BINARY_DIR}/Doxyfile.docs")
    configure_file("${_doxyfile_template}" "${_target_doxyfile}")

    doxygen_add_docs(docs
                     ${cmocka-library_SOURCE_DIR}
                     ${cmocka-headers_SOURCE_DIR}
                     ${CMAKE_CURRENT_SOURCE_DIR})
endif(${CMAKE_VERSION} VERSION_LESS "3.9.0")

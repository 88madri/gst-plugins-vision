set (SOURCES
  gstkayasrc.c
  )
    
set (HEADERS
  gstkayasrc.h)

include_directories (AFTER
  ${GSTREAMER_INCLUDE_DIR}/..
  ${KAYA_INCLUDE_DIR}
  ${PROJECT_SOURCE_DIR}/common
  )

set (libname libgstkaya)

add_library (${libname} MODULE
  ${SOURCES}
  ${HEADERS})

target_link_libraries (${libname}
  ${GLIB2_LIBRARIES}
  ${GOBJECT_LIBRARIES}
  ${GSTREAMER_LIBRARY}
  ${GSTREAMER_BASE_LIBRARY}
  ${GSTREAMER_VIDEO_LIBRARY}
  ${KAYA_LIBRARIES}
  )

set (pdbfile "${CMAKE_CURRENT_BINARY_DIR}/\${CMAKE_INSTALL_CONFIG_NAME}/${libname}.pdb")
install (FILES ${pdbfile} DESTINATION lib/gstreamer-1.0)
install(TARGETS ${libname}
  LIBRARY DESTINATION lib/gstreamer-1.0)

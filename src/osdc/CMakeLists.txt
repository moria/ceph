set(osdc_files
  Objecter.cc
  Filer.cc)
set(osdc_rbd_files
  ObjectCacher.cc
  Striper.cc)
add_library(osdc_rbd_objs OBJECT ${osdc_rbd_files})
add_library(osdc STATIC ${osdc_files} $<TARGET_OBJECTS:osdc_rbd_objs>)
if(WITH_LTTNG AND WITH_EVENTTRACE)
  add_dependencies(osdc eventtrace_tp)
endif()

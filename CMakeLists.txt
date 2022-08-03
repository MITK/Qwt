cmake_minimum_required(VERSION 3.18...3.18 FATAL_ERROR)

project(Qwt VERSION 6.2.0 LANGUAGES CXX)

set(QWT_MOC_HEADERS
  qwt_abstract_legend.h
  qwt_abstract_scale.h
  qwt_abstract_slider.h
  qwt_analog_clock.h
  qwt_compass.h
  qwt_counter.h
  qwt_dial.h
  qwt_dyngrid_layout.h
  qwt_knob.h
  qwt_legend.h
  qwt_legend_label.h
  qwt_magnifier.h
  qwt_panner.h
  qwt_picker.h
  qwt_plot.h
  qwt_plot_canvas.h
  qwt_plot_glcanvas.h
  qwt_plot_magnifier.h
  qwt_plot_opengl_canvas.h
  qwt_plot_panner.h
  qwt_plot_picker.h
  qwt_plot_renderer.h
  qwt_plot_rescaler.h
  qwt_plot_zoomer.h
  qwt_polar_canvas.h
  qwt_polar_magnifier.h
  qwt_polar_panner.h
  qwt_polar_picker.h
  qwt_polar_plot.h
  qwt_polar_renderer.h
  qwt_sampling_thread.h
  qwt_scale_widget.h
  qwt_slider.h
  qwt_text_label.h
  qwt_thermo.h
  qwt_wheel.h
  qwt_widget_overlay.h
)

set(QWT_SOURCES
  qwt.cpp
  qwt_abstract_legend.cpp
  qwt_abstract_scale.cpp
  qwt_abstract_scale_draw.cpp
  qwt_abstract_slider.cpp
  qwt_analog_clock.cpp
  qwt_arrow_button.cpp
  qwt_bezier.cpp
  qwt_clipper.cpp
  qwt_color_map.cpp
  qwt_column_symbol.cpp
  qwt_compass.cpp
  qwt_compass_rose.cpp
  qwt_counter.cpp
  qwt_curve_fitter.cpp
  qwt_date.cpp
  qwt_date_scale_draw.cpp
  qwt_date_scale_engine.cpp
  qwt_dial.cpp
  qwt_dial_needle.cpp
  qwt_dyngrid_layout.cpp
  qwt_event_pattern.cpp
  qwt_graphic.cpp
  qwt_interval.cpp
  qwt_interval_symbol.cpp
  qwt_knob.cpp
  qwt_legend.cpp
  qwt_legend_data.cpp
  qwt_legend_label.cpp
  qwt_magnifier.cpp
  qwt_math.cpp
  qwt_matrix_raster_data.cpp
  qwt_null_paintdevice.cpp
  qwt_painter.cpp
  qwt_painter_command.cpp
  qwt_panner.cpp
  qwt_picker.cpp
  qwt_picker_machine.cpp
  qwt_pixel_matrix.cpp
  qwt_plot.cpp
  qwt_plot_abstract_barchart.cpp
  qwt_plot_abstract_canvas.cpp
  qwt_plot_axis.cpp
  qwt_plot_barchart.cpp
  qwt_plot_canvas.cpp
  qwt_plot_curve.cpp
  qwt_plot_dict.cpp
  qwt_plot_directpainter.cpp
  qwt_plot_glcanvas.cpp
  qwt_plot_graphicitem.cpp
  qwt_plot_grid.cpp
  qwt_plot_histogram.cpp
  qwt_plot_intervalcurve.cpp
  qwt_plot_item.cpp
  qwt_plot_layout.cpp
  qwt_plot_legenditem.cpp
  qwt_plot_magnifier.cpp
  qwt_plot_marker.cpp
  qwt_plot_multi_barchart.cpp
  qwt_plot_opengl_canvas.cpp
  qwt_plot_panner.cpp
  qwt_plot_picker.cpp
  qwt_plot_rasteritem.cpp
  qwt_plot_renderer.cpp
  qwt_plot_rescaler.cpp
  qwt_plot_scaleitem.cpp
  qwt_plot_seriesitem.cpp
  qwt_plot_shapeitem.cpp
  qwt_plot_spectrocurve.cpp
  qwt_plot_spectrogram.cpp
  qwt_plot_svgitem.cpp
  qwt_plot_textlabel.cpp
  qwt_plot_tradingcurve.cpp
  qwt_plot_vectorfield.cpp
  qwt_plot_zoneitem.cpp
  qwt_plot_zoomer.cpp
  qwt_point_3d.cpp
  qwt_point_data.cpp
  qwt_point_mapper.cpp
  qwt_point_polar.cpp
  qwt_polar_canvas.cpp
  qwt_polar_curve.cpp
  qwt_polar_fitter.cpp
  qwt_polar_grid.cpp
  qwt_polar_item.cpp
  qwt_polar_itemdict.cpp
  qwt_polar_layout.cpp
  qwt_polar_magnifier.cpp
  qwt_polar_marker.cpp
  qwt_polar_panner.cpp
  qwt_polar_picker.cpp
  qwt_polar_plot.cpp
  qwt_polar_renderer.cpp
  qwt_polar_spectrogram.cpp
  qwt_raster_data.cpp
  qwt_round_scale_draw.cpp
  qwt_sampling_thread.cpp
  qwt_scale_div.cpp
  qwt_scale_draw.cpp
  qwt_scale_engine.cpp
  qwt_scale_map.cpp
  qwt_scale_widget.cpp
  qwt_series_data.cpp
  qwt_slider.cpp
  qwt_spline.cpp
  qwt_spline_basis.cpp
  qwt_spline_cubic.cpp
  qwt_spline_curve_fitter.cpp
  qwt_spline_local.cpp
  qwt_spline_parametrization.cpp
  qwt_spline_pleasing.cpp
  qwt_spline_polynomial.cpp
  qwt_symbol.cpp
  qwt_system_clock.cpp
  qwt_text.cpp
  qwt_text_engine.cpp
  qwt_text_label.cpp
  qwt_thermo.cpp
  qwt_transform.cpp
  qwt_vectorfield_symbol.cpp
  qwt_weeding_curve_fitter.cpp
  qwt_wheel.cpp
  qwt_widget_overlay.cpp
)

set(_qwt_moc_headers )
foreach(_header ${QWT_MOC_HEADERS})
  list(APPEND _qwt_moc_headers src/${_header})
endforeach()

set(_qwt_sources )
foreach(_source ${QWT_SOURCES})
  list(APPEND _qwt_sources src/${_source})
endforeach()

find_package(Qt5Svg REQUIRED)
find_package(Qt5OpenGL REQUIRED)
find_package(Qt5PrintSupport REQUIRED)
find_package(Qt5Concurrent REQUIRED)

qt5_wrap_cpp(_qwt_sources ${_qwt_moc_headers})

add_library(qwt SHARED ${_qwt_sources})

target_link_libraries(qwt PUBLIC Qt5::Svg Qt5::OpenGL Qt5::PrintSupport Qt5::Concurrent)

target_compile_definitions(qwt PUBLIC QWT_DLL PRIVATE QWT_MAKEDLL)

set_target_properties(qwt PROPERTIES
  DEBUG_POSTFIX d
  SOVERSION ${PROJECT_VERSION_MAJOR}
  VERSION ${PROJECT_VERSION}
)

option(QWT_BUILD_DESIGNER_PLUGIN "Build the Qt Designer plugin" ON)
  if (QWT_BUILD_DESIGNER_PLUGIN)

  include_directories(${CMAKE_CURRENT_SOURCE_DIR}/src)

  set(_qwt_designer_sources designer/qwt_designer_plugin.cpp)

  qt5_wrap_cpp(_qwt_designer_sources
    designer/qwt_designer_plugin.cpp
  )

  set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/plugins/designer)
  set(CMAKE_LIBRARY_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/plugins/designer)
  set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_CURRENT_BINARY_DIR}/plugins/designer)

  find_package(Qt5Designer REQUIRED)

  include_directories(${Qt5Designer_INCLUDE_DIRS})

  qt5_add_resources(_qwt_designer_sources designer/qwt_designer_plugin.qrc)

  add_library(qwt_designer_plugin SHARED ${_qwt_designer_sources})

  target_link_libraries(qwt_designer_plugin qwt Qt5::Designer)

  set_target_properties(qwt_designer_plugin PROPERTIES
    COMPILE_DEFINITIONS QWT_DLL
    DEBUG_POSTFIX d
    SOVERSION ${PROJECT_VERSION_MAJOR}
    VERSION ${PROJECT_VERSION}
  )
endif()

set(${PROJECT_NAME}_LIBRARIES qwt)

if (QWT_BUILD_DESIGNER_PLUGIN)
  install(TARGETS qwt_designer_plugin
    RUNTIME DESTINATION plugins/designer
    LIBRARY DESTINATION plugins/designer
  )
endif()

install(TARGETS ${${PROJECT_NAME}_LIBRARIES} EXPORT ${PROJECT_NAME}_TARGETS
  LIBRARY DESTINATION lib
  ARCHIVE DESTINATION lib
  RUNTIME DESTINATION bin
  INCLUDES DESTINATION include/${PROJECT_NAME}
)

install(DIRECTORY src/
  DESTINATION include/${PROJECT_NAME}
  FILES_MATCHING PATTERN "*.h"
)

configure_file(
  ${PROJECT_NAME}Config.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}Config.cmake
  @ONLY
)

configure_file(
  ${CMAKE_CURRENT_SOURCE_DIR}/${PROJECT_NAME}ConfigVersion.cmake.in
  ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}ConfigVersion.cmake
  @ONLY
)

export(EXPORT ${PROJECT_NAME}_TARGETS
  FILE ${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}Targets.cmake
)

set(config_package_location lib/cmake/${PROJECT_NAME})

install(EXPORT ${PROJECT_NAME}_TARGETS
  FILE ${PROJECT_NAME}Targets.cmake
  DESTINATION ${config_package_location}
)

install(FILES
    "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}Config.cmake"
    "${CMAKE_CURRENT_BINARY_DIR}/${PROJECT_NAME}ConfigVersion.cmake"
  DESTINATION ${config_package_location}
)

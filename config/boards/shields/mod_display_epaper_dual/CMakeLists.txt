# Copyright (c) 2026
# SPDX-License-Identifier: MIT

if(CONFIG_ZMK_DISPLAY AND CONFIG_HALCYON_EPAPER_WIDGET_DUAL)
  zephyr_library_include_directories(${CMAKE_SOURCE_DIR}/include)
  zephyr_library_sources(custom_status_screen.c)
  zephyr_library_sources(widgets/bolt.c)
  zephyr_library_sources(widgets/util.c)
  zephyr_library_sources(widgets/art.c)

  if(NOT CONFIG_ZMK_SPLIT OR CONFIG_ZMK_SPLIT_ROLE_CENTRAL)
    zephyr_library_sources(widgets/status.c)
  else()
    zephyr_library_sources(widgets/peripheral_status.c)
  endif()
endif()

set(KIT ${PROJECT_NAME}Plugins)
project(${KIT})

#
# See CTK/CMake/ctkMacroBuildQtPlugin.cmake for details
#

# The header '${KIT}Export.h' will be automatically configured.
set(${KIT}_EXPORT "Q_SLICER_BASE_QTGUI_PLUGINS_EXPORT")

# Source files
set(${KIT}_SRCS
  qSlicerQTGUIAbstractPlugin.cxx
  qSlicerQTGUIAbstractPlugin.h
  qSlicerQTGUIPlugins.cxx
  qSlicerQTGUIPlugins.h

  qSlicerModulePanelPlugin.cxx
  qSlicerModulePanelPlugin.h
  qSlicerModulesListViewPlugin.cxx
  qSlicerModulesListViewPlugin.h
  qSlicerMouseModeToolBarPlugin.cxx
  qSlicerMouseModeToolBarPlugin.h
  qSlicerWidgetPlugin.cxx
  qSlicerWidgetPlugin.h
  )

# Headers that should run through moc
set(${KIT}_MOC_SRCS
  qSlicerQTGUIPlugins.h

  qSlicerQTGUIAbstractPlugin.h
  qSlicerModulePanelPlugin.h
  qSlicerModulesListViewPlugin.h
  qSlicerMouseModeToolBarPlugin.h
  qSlicerWidgetPlugin.h
  )

set(${KIT}_TARGET_LIBRARIES
  qSlicerBaseQTGUI
  )
if(Slicer_BUILD_CLI_SUPPORT)
  list(APPEND ${KIT}_TARGET_LIBRARIES
    qSlicerBaseQTCLI
    )
endif()

ctkMacroBuildQtDesignerPlugin(
  NAME ${PROJECT_NAME}
  EXPORT_DIRECTIVE ${${KIT}_EXPORT}
  SRCS ${${KIT}_SRCS}
  MOC_SRCS ${${KIT}_MOC_SRCS}
  TARGET_LIBRARIES ${${KIT}_TARGET_LIBRARIES}
  )

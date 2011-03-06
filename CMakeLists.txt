cmake_minimum_required(VERSION 2.6)

project(ImageCompleter)

find_package(wxWidgets COMPONENTS core base REQUIRED)
include( ${wxWidgets_USE_FILE} )

set(cmdsrc src/image-completer-cmd)
set(prioritybp src/priority-bp/impl)

include_directories(lib/tacus/ src/image-completer-cmd src/priority-bp src/priority-bp/api src/priority-bp/impl src/priority-bp/impl/compositors src/priority-bp/impl/energy-calculators src/tech/tech src/tech)

add_executable(ImageCompleter
${cmdsrc}/CommandLineOptions.cpp
${cmdsrc}/Main.cpp
${cmdsrc}/Pch.cpp
${cmdsrc}/SettingsUi.cpp

${prioritybp}/Compositor.cpp
${prioritybp}/ConstNodeLabels.cpp
${prioritybp}/EnergyCalculatorContainer.cpp
${prioritybp}/HostImageLocal.cpp
${prioritybp}/Image.cpp
${prioritybp}/Label.cpp
${prioritybp}/Mask.cpp
${prioritybp}/MaskWritable.cpp
${prioritybp}/NeighborEdge.cpp
${prioritybp}/Node.cpp
${prioritybp}/NodeSet.cpp
${prioritybp}/Pch.cpp
${prioritybp}/PriorityBp.cpp
${prioritybp}/PriorityBpRunner.cpp
${prioritybp}/ScalableDebugging.cpp
${prioritybp}/Settings.cpp

${prioritybp}/compositors/CompositorRoot.cpp
${prioritybp}/compositors/CompositorUtils.cpp
${prioritybp}/compositors/ImageFloat.cpp
${prioritybp}/compositors/OutputBlenderDebugSoftMaskIntensity.cpp
${prioritybp}/compositors/OutputBlenderSoftMask.cpp
${prioritybp}/compositors/PatchBlenderNone.cpp
${prioritybp}/compositors/PatchBlenderPriority.cpp
${prioritybp}/compositors/PatchTypeDebugPatchOrder.cpp
${prioritybp}/compositors/PatchTypeNormal.cpp
${prioritybp}/compositors/PatchTypePoisson.cpp
${prioritybp}/compositors/PoissonSolver.cpp
${prioritybp}/compositors/TaucsMatrix.cpp

${prioritybp}/energy-calculators/EnergyCalculatorFft.cpp
${prioritybp}/energy-calculators/EnergyCalculatorFftUtils.cpp
${prioritybp}/energy-calculators/EnergyCalculatorPerPixel.cpp

src/tech/Pch.cpp
src/tech/tech/ImageUtils.cpp
src/tech/tech/Profile.cpp
src/tech/tech/Time.cpp
)

target_link_libraries(ImageCompleter ${wxWidgets_LIBRARIES})
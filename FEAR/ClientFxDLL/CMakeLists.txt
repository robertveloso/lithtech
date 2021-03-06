project( FEAR_ClientFXDLL )

set(SOURCES
  BaseCreateFX.cpp
  BaseFx.cpp
  BaseSpriteFX.cpp
  CameraShakeFX.cpp
  clientfx.cpp
  ClientFXVertexDeclMgr.cpp
  CreateFX.cpp
  CreateRayFX.cpp
  DebrisSystemFX.cpp
  DebrisSystemProps.cpp
  ../Shared/DebugNew.cpp
  DecalFX.cpp
  dynalightfx.cpp
  FlareSpriteFX.cpp
  LensFlareFX.cpp
  lightningfx.cpp
  LightningProps.cpp
  ltbmodelfx.cpp
  ../../runtime/kernel/mem/src/ltmemory.cpp # currently not found in the source tree
  ../../sdk/inc/ltmodule.cpp
  ../../sdk/inc/ltobjref.cpp
  MemoryPageMgr.cpp
  OverlayFX.cpp
  ParticleSimulation.cpp
  ParticleSystemFX.cpp
  ParticleSystemGroup.cpp
  ParticleSystemProps.cpp
#  ../../sdk/inc/performancemonitorhook.cpp # currently not found in the source tree
  PolyTrailFX.cpp
  PolyTrailProps.cpp
  RumbleFX.cpp
  Soundfx.cpp
  spritefx.cpp
  stdafx.cpp
  TracerFX.cpp
  VideoControllerFX.cpp
)

include_directories(
  ../../sdk/inc
  ../../libs/lith
  ../../libs/stdlith
  ../Shared
)

add_definitions(
  -DMEMTRACK_CLIENTFX
  -D_DEBUG
)
if(WIN32)
add_definitions(
  -DWIN32
  -D_WINDOWS
)
else(WIN32)
add_definitions(
  -D_LINUX
  -D__LINUX
)
endif(WIN32)

add_library( ${PROJECT_NAME} SHARED ${SOURCES} )

target_link_libraries( ${PROJECT_NAME} shared_assert )

if(CMAKE_COMPILER_IS_GNUCXX)
  set_target_properties(${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "-fpermissive")
endif(CMAKE_COMPILER_IS_GNUCXX)

cmake_minimum_required(VERSION 3.4.3)
include("../../../../cmake/modules/StandaloneOverlay.cmake")

add_swift_target_library(swiftDispatch ${SWIFT_SDK_OVERLAY_LIBRARY_BUILD_TYPES} IS_SDK_OVERLAY
  Dispatch.swift
  Dispatch.mm
  Block.swift

  Data.swift
  IO.swift
  Private.swift
  Queue.swift
  Source.swift
  Schedulers+DispatchQueue.swift
  Time.swift

  "${SWIFT_SOURCE_DIR}/stdlib/linker-support/magic-symbols-for-install-name.c"

  SWIFT_COMPILE_FLAGS ${SWIFT_RUNTIME_SWIFT_COMPILE_FLAGS} ${SWIFT_STANDARD_LIBRARY_SWIFT_FLAGS}
  LINK_FLAGS "${SWIFT_RUNTIME_SWIFT_LINK_FLAGS}"
  SWIFT_MODULE_DEPENDS_OSX Darwin ObjectiveC # auto-updated
  SWIFT_MODULE_DEPENDS_IOS Darwin ObjectiveC # auto-updated
  SWIFT_MODULE_DEPENDS_TVOS Darwin ObjectiveC # auto-updated
  SWIFT_MODULE_DEPENDS_WATCHOS Darwin ObjectiveC # auto-updated
  FRAMEWORK_DEPENDS_WEAK Combine

  DEPLOYMENT_VERSION_OSX ${SWIFTLIB_DEPLOYMENT_VERSION_DISPATCH_OSX}
  DEPLOYMENT_VERSION_IOS ${SWIFTLIB_DEPLOYMENT_VERSION_DISPATCH_IOS}
  DEPLOYMENT_VERSION_TVOS ${SWIFTLIB_DEPLOYMENT_VERSION_DISPATCH_TVOS}
  DEPLOYMENT_VERSION_WATCHOS ${SWIFTLIB_DEPLOYMENT_VERSION_DISPATCH_WATCHOS}
  INSTALL_IN_COMPONENT sdk-overlay
)

#START-FILE-LIST
# File List auto generated by waf2cmake.py, do not modify manually.

start_sources()
sources_platform(ALL)
add_sources("NoUberFile"
	SOURCE_GROUP "AlembicCompiler"
		"AlembicCompiler.cpp"
		"AlembicConverter.cpp"
		"GeomCacheBlockCompressor.cpp"
		"GeomCacheEncoder.cpp"
		"GeomCacheWriter.cpp"
		"AlembicCompiler.h"
		"AlembicConverter.h"
		"GeomCache.h"
		"GeomCacheBlockCompressor.h"
		"GeomCacheEncoder.h"
		"GeomCacheWriter.h"
	SOURCE_GROUP "CryCommonTools"
		"../../CryCommonTools/FileUtil.h"
		"../../CryCommonTools/PathHelpers.cpp"
		"../../CryCommonTools/StringHelpers.cpp"
		"../../CryCommonTools/PathHelpers.h"
		"../../CryCommonTools/StringHelpers.h"
	SOURCE_GROUP "MeshCompiler (Cry3DEngine)"
		"../../../CryEngine/Cry3DEngine/MeshCompiler/ForsythFaceReorderer.cpp"
		"../../../CryEngine/Cry3DEngine/MeshCompiler/ForsythFaceReorderer.h"
		"../../../CryEngine/Cry3DEngine/MeshCompiler/MeshCompiler.cpp"
		"../../../CryEngine/Cry3DEngine/MeshCompiler/MeshCompiler.h"
		"../../../CryEngine/Cry3DEngine/MeshCompiler/TangentSpaceCalculation.cpp"
		"../../../CryEngine/Cry3DEngine/MeshCompiler/TangentSpaceCalculation.h"
		"${SDK_DIR}/TangentBasisComputation/mikkelsen/mikktspace.cpp"
		"${SDK_DIR}/TangentBasisComputation/mikkelsen/mikktspace.h"
	SOURCE_GROUP "Source Files"
		"ResourceCompilerABC.cpp"
		"../ResourceCompiler/IConfig.cpp"
		"ResourceCompilerPlugin.def"
		"stdafx.h"
		"stdafx.cpp"
	SOURCE_GROUP "Utils"
		"../../CryCommonTools/StealingThreadPool.cpp"
		"../../CryCommonTools/StealingThreadPool.h"
)
sources_platform(WIN32)
add_sources("NoUberFile"
	SOURCE_GROUP "CryCommonTools"
		"../../CryCommonTools/FileUtil_windows.cpp"
)
sources_platform(LINUX)
add_sources("NoUberFile"
	SOURCE_GROUP "CryCommonTools"
		"../../CryCommonTools/FileUtil_posix.cpp"
)
end_sources()
#END-FILE-LIST

CryResourceCompilerModule(ResourceCompilerABC PCH "stdafx.cpp" SOLUTION_FOLDER "RC")
target_include_directories(${THIS_PROJECT} PRIVATE 
	"${CMAKE_SOURCE_DIR}/ResourceCompiler"
	"${CRYENGINE_SOURCE_DIR}/Code/Tools" 
	"${CRYENGINE_SOURCE_DIR}/Code/Tools/CryCommonTools"
	"${SDK_DIR}/TangentBasisComputation"
	)

target_compile_definitions(${THIS_PROJECT} PRIVATE _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING)
target_link_libraries(${THIS_PROJECT} PRIVATE zlib lz4 alembic ilmbase)
target_compile_options(${THIS_PROJECT} PRIVATE /EHsc /GR)
set_target_properties(${THIS_PROJECT} PROPERTIES LINK_FLAGS "/DEF:ResourceCompilerPlugin.def")

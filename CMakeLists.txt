cmake_minimum_required(VERSION 3.17)
project(XingDBG)

set(CMAKE_CXX_STANDARD 20)
set(CMAKE_AUTOMOC ON)
set(CMAKE_AUTORCC ON)
set(CMAKE_AUTOUIC ON)

set(QT_VERSION 6)
set(REQUIRED_LIBS Core Gui Widgets)
set(REQUIRED_LIBS_QUALIFIED Qt6::Core Qt6::Gui Qt6::Widgets)
find_package(Qt${QT_VERSION} COMPONENTS ${REQUIRED_LIBS} REQUIRED)

find_package(LLVM REQUIRED CONFIG)
include_directories(${LLVM_INCLUDE_DIRS})
link_directories(${LLVM_LIBRARY_DIRS})

set(KDDockWidgets_QT6 ON)
set(build_for_qt6 ON)
set(build_examples OFF)
set(KDDockWidgets_STATIC ON)
set(build_static ON)
add_subdirectory(3rdparty/KDDockWidgets)

include_directories(3rdparty/KDDockWidgets/src/fwd_headers)
include_directories(${CMAKE_CURRENT_SOURCE_DIR})

if(WIN32)
	message(STATUS "Build for windows")
    set(EXECUTABLE_EXTRA WIN32 ${CMAKE_CURRENT_SOURCE_DIR}/Resources/resource.rc)
    set(LIBS_EXTRA
            LLVMOption.lib
            LLVMSupport.lib
            lldbInitialization.lib
            lldbPluginABIAArch64.lib
            lldbPluginABIARM.lib
            lldbPluginABIHexagon.lib
            lldbPluginABIMips.lib
            lldbPluginABIPowerPC.lib
            lldbPluginABISystemZ.lib
            lldbPluginABIX86.lib
            lldbPluginArchitectureArm.lib
            lldbPluginArchitectureMips.lib
            lldbPluginArchitecturePPC64.lib
            lldbPluginArchitectureAArch64.lib
            lldbPluginDisassemblerLLVMC.lib
            LLVMAArch64CodeGen.lib
            LLVMAArch64AsmParser.lib
            LLVMAArch64Disassembler.lib
            LLVMAArch64Desc.lib
            LLVMAArch64Info.lib
            LLVMAArch64Utils.lib
            LLVMAMDGPUCodeGen.lib
            LLVMMIRParser.lib
            LLVMAMDGPUAsmParser.lib
            LLVMAMDGPUDisassembler.lib
            LLVMAMDGPUDesc.lib
            LLVMAMDGPUInfo.lib
            LLVMAMDGPUUtils.lib
            LLVMARMCodeGen.lib
            LLVMARMAsmParser.lib
            LLVMARMDisassembler.lib
            LLVMARMDesc.lib
            LLVMARMInfo.lib
            LLVMARMUtils.lib
            LLVMAVRCodeGen.lib
            LLVMAVRAsmParser.lib
            LLVMAVRDesc.lib
            LLVMAVRDisassembler.lib
            LLVMAVRInfo.lib
            LLVMBPFCodeGen.lib
            LLVMBPFAsmParser.lib
            LLVMBPFDesc.lib
            LLVMBPFDisassembler.lib
            LLVMBPFInfo.lib
            LLVMHexagonCodeGen.lib
            LLVMHexagonAsmParser.lib
            LLVMHexagonDisassembler.lib
            LLVMHexagonDesc.lib
            LLVMHexagonInfo.lib
            LLVMLanaiCodeGen.lib
            LLVMLanaiAsmParser.lib
            LLVMLanaiDisassembler.lib
            LLVMLanaiDesc.lib
            LLVMLanaiInfo.lib
            LLVMMSP430CodeGen.lib
            LLVMMSP430AsmParser.lib
            LLVMMSP430Desc.lib
            LLVMMSP430Disassembler.lib
            LLVMMSP430Info.lib
            LLVMNVPTXCodeGen.lib
            LLVMNVPTXDesc.lib
            LLVMNVPTXInfo.lib
            LLVMPowerPCCodeGen.lib
            LLVMPowerPCAsmParser.lib
            LLVMPowerPCDesc.lib
            LLVMPowerPCDisassembler.lib
            LLVMPowerPCInfo.lib
            LLVMRISCVCodeGen.lib
            LLVMRISCVAsmParser.lib
            LLVMRISCVDisassembler.lib
            LLVMRISCVDesc.lib
            LLVMRISCVInfo.lib
            LLVMSparcCodeGen.lib
            LLVMSparcAsmParser.lib
            LLVMSparcDesc.lib
            LLVMSparcDisassembler.lib
            LLVMSparcInfo.lib
            LLVMSystemZCodeGen.lib
            LLVMSystemZAsmParser.lib
            LLVMSystemZDisassembler.lib
            LLVMSystemZDesc.lib
            LLVMSystemZInfo.lib
            LLVMVECodeGen.lib
            LLVMVEAsmParser.lib
            LLVMVEDesc.lib
            LLVMVEDisassembler.lib
            LLVMVEInfo.lib
            LLVMWebAssemblyCodeGen.lib
            LLVMWebAssemblyAsmParser.lib
            LLVMWebAssemblyDisassembler.lib
            LLVMWebAssemblyDesc.lib
            LLVMWebAssemblyInfo.lib
            LLVMWebAssemblyUtils.lib
            LLVMX86CodeGen.lib
            LLVMCFGuard.lib
            LLVMX86AsmParser.lib
            LLVMX86Desc.lib
            LLVMX86Disassembler.lib
            LLVMX86Info.lib
            LLVMXCoreCodeGen.lib
            LLVMXCoreDesc.lib
            LLVMXCoreDisassembler.lib
            LLVMXCoreInfo.lib
            lldbPluginDynamicLoaderStatic.lib
            lldbPluginDynamicLoaderHexagonDYLD.lib
            lldbPluginDynamicLoaderWasmDYLD.lib
            lldbPluginInstructionARM.lib
            lldbPluginInstructionARM64.lib
            lldbPluginInstructionMIPS.lib
            lldbPluginInstructionMIPS64.lib
            LLVMMipsCodeGen.lib
            LLVMAsmPrinter.lib
            LLVMGlobalISel.lib
            LLVMSelectionDAG.lib
            LLVMMipsAsmParser.lib
            LLVMMipsDesc.lib
            LLVMMipsDisassembler.lib
            LLVMMipsInfo.lib
            lldbPluginInstructionPPC64.lib
            lldbPluginInstrumentationRuntimeASan.lib
            lldbPluginInstrumentationRuntimeMainThreadChecker.lib
            lldbPluginInstrumentationRuntimeTSan.lib
            lldbPluginInstrumentationRuntimeUBSan.lib
            lldbPluginJITLoaderGDB.lib
            lldbPluginObjCPlusPlusLanguage.lib
            lldbPluginCXXItaniumABI.lib
            lldbPluginMemoryHistoryASan.lib
            lldbPluginObjectContainerBSDArchive.lib
            lldbPluginObjectContainerMachOArchive.lib
            lldbPluginObjectFileMinidump.lib
            lldbPluginPlatformAndroid.lib
            lldbPluginPlatformFreeBSD.lib
            lldbPluginPlatformLinux.lib
            lldbPluginPlatformNetBSD.lib
            lldbPluginPlatformOpenBSD.lib
            lldbPluginPlatformQemuUser.lib
            lldbPluginPlatformWindows.lib
            lldbPluginProcessWindowsCommon.lib
            lldbPluginDynamicLoaderWindowsDYLD.lib
            lldbPluginScriptedProcess.lib
            lldbPluginProcessMachCore.lib
            lldbPluginDynamicLoaderDarwinKernel.lib
            lldbPluginPlatformMacOSX.lib
            lldbPluginPlatformPOSIX.lib
            lldbPluginPlatformGDB.lib
            lldbPluginProcessGDBRemote.lib
            lldbPluginDynamicLoaderMacOSXDYLD.lib
            lldbPluginObjectFileMachO.lib
            lldbPluginProcessMinidump.lib
            lldbPluginDynamicLoaderPosixDYLD.lib
            lldbPluginProcessElfCore.lib
            lldbPluginDynamicLoaderPosixDYLD.lib
            lldbPluginProcessElfCore.lib
            lldbPluginClangREPL.lib
            lldbPluginScriptInterpreterNone.lib
            lldbPluginStructuredDataDarwinLog.lib
            lldbPluginSymbolFileBreakpad.lib
            lldbPluginObjectFileBreakpad.lib
            lldbPluginSymbolFileSymtab.lib
            lldbPluginSystemRuntimeMacOSX.lib
            lldbPluginSymbolVendorELF.lib
            lldbPluginObjectFileELF.lib
            lldbPluginSymbolVendorPECOFF.lib
            lldbPluginObjectFilePECOFF.lib
            lldbPluginSymbolVendorWasm.lib
            lldbPluginObjectFileWasm.lib
            lldbPluginTraceExporterCTF.lib
            lldbPluginTraceExporterCommon.lib
            lldbPluginUnwindAssemblyInstEmulation.lib
            lldbPluginUnwindAssemblyX86.lib
            lldbBreakpoint.lib
            lldbCore.lib
            lldbDataFormatters.lib
            lldbExpression.lib
            lldbInterpreter.lib
            lldbSymbol.lib
            lldbTarget.lib
            lldbPluginCPlusPlusLanguage.lib
            lldbPluginObjCLanguage.lib
            lldbPluginAppleObjCRuntime.lib
            lldbPluginRenderScriptRuntime.lib
            lldbPluginObjectFileJIT.lib
            lldbPluginObjectFilePDB.lib
            lldbPluginSymbolFileDWARF.lib
            lldbPluginSymbolFilePDB.lib
            lldbPluginTypeSystemClang.lib
            lldbCommands.lib
            lldbPluginProcessUtility.lib
            lldbPluginClangCommon.lib
            lldbPluginCPPRuntime.lib
            lldbPluginExpressionParserClang.lib
            lldbPluginSymbolFileNativePDB.lib
            lldbPluginObjCRuntime.lib
            lldbBreakpoint.lib
            lldbCore.lib
            lldbDataFormatters.lib
            lldbExpression.lib
            lldbInterpreter.lib
            lldbSymbol.lib
            lldbTarget.lib
            lldbPluginCPlusPlusLanguage.lib
            lldbPluginObjCLanguage.lib
            lldbPluginAppleObjCRuntime.lib
            lldbPluginRenderScriptRuntime.lib
            lldbPluginObjectFileJIT.lib
            lldbPluginObjectFilePDB.lib
            lldbPluginSymbolFileDWARF.lib
            lldbPluginSymbolFilePDB.lib
            lldbPluginTypeSystemClang.lib
            lldbCommands.lib
            lldbPluginProcessUtility.lib
            lldbPluginClangCommon.lib
            lldbPluginCPPRuntime.lib
            lldbPluginExpressionParserClang.lib
            lldbPluginSymbolFileNativePDB.lib
            lldbPluginObjCRuntime.lib
            lldbBreakpoint.lib
            lldbCore.lib
            lldbDataFormatters.lib
            lldbExpression.lib
            lldbInterpreter.lib
            lldbSymbol.lib
            lldbTarget.lib
            lldbPluginCPlusPlusLanguage.lib
            lldbPluginObjCLanguage.lib
            lldbPluginAppleObjCRuntime.lib
            lldbPluginRenderScriptRuntime.lib
            lldbPluginObjectFileJIT.lib
            lldbPluginObjectFilePDB.lib
            lldbPluginSymbolFileDWARF.lib
            lldbPluginSymbolFilePDB.lib
            lldbPluginTypeSystemClang.lib
            lldbCommands.lib
            lldbPluginProcessUtility.lib
            lldbPluginClangCommon.lib
            lldbPluginCPPRuntime.lib
            lldbPluginExpressionParserClang.lib
            lldbPluginSymbolFileNativePDB.lib
            lldbPluginObjCRuntime.lib
            lldbBreakpoint.lib
            lldbCore.lib
            lldbDataFormatters.lib
            lldbExpression.lib
            lldbInterpreter.lib
            lldbSymbol.lib
            lldbTarget.lib
            lldbPluginCPlusPlusLanguage.lib
            lldbPluginObjCLanguage.lib
            lldbPluginAppleObjCRuntime.lib
            lldbPluginRenderScriptRuntime.lib
            lldbPluginObjectFileJIT.lib
            lldbPluginObjectFilePDB.lib
            lldbPluginSymbolFileDWARF.lib
            lldbPluginSymbolFilePDB.lib
            lldbPluginTypeSystemClang.lib
            lldbCommands.lib
            lldbPluginProcessUtility.lib
            lldbPluginClangCommon.lib
            lldbPluginCPPRuntime.lib
            lldbPluginExpressionParserClang.lib
            lldbPluginSymbolFileNativePDB.lib
            lldbPluginObjCRuntime.lib
            lldbBreakpoint.lib
            lldbCore.lib
            lldbDataFormatters.lib
            lldbExpression.lib
            lldbInterpreter.lib
            lldbSymbol.lib
            lldbTarget.lib
            lldbPluginCPlusPlusLanguage.lib
            lldbPluginObjCLanguage.lib
            lldbPluginAppleObjCRuntime.lib
            lldbPluginRenderScriptRuntime.lib
            lldbPluginObjectFileJIT.lib
            lldbPluginObjectFilePDB.lib
            lldbPluginSymbolFileDWARF.lib
            lldbPluginSymbolFilePDB.lib
            lldbPluginTypeSystemClang.lib
            lldbCommands.lib
            lldbPluginProcessUtility.lib
            lldbPluginClangCommon.lib
            lldbPluginCPPRuntime.lib
            lldbPluginExpressionParserClang.lib
            lldbPluginSymbolFileNativePDB.lib
            lldbPluginObjCRuntime.lib
            lldbVersion.lib
            lldbHost.lib
            LLVMMCJIT.lib
            LLVMExecutionEngine.lib
            LLVMOrcTargetProcess.lib
            LLVMOrcShared.lib
            LLVMRuntimeDyld.lib
            clangCodeGen.lib
            LLVMCoverage.lib
            LLVMLTO.lib
            LLVMCodeGen.lib
            LLVMPasses.lib
            LLVMTarget.lib
            LLVMCoroutines.lib
            LLVMipo.lib
            LLVMIRReader.lib
            LLVMAsmParser.lib
            LLVMVectorize.lib
            LLVMInstrumentation.lib
            LLVMBitWriter.lib
            LLVMLinker.lib
            LLVMObjCARCOpts.lib
            LLVMExtensions.lib
            clangRewriteFrontend.lib
            clangFrontend.lib
            clangDriver.lib
            LLVMWindowsDriver.lib
            LLVMOption.lib
            clangParse.lib
            clangRewrite.lib
            clangSerialization.lib
            clangSema.lib
            clangEdit.lib
            clangAnalysis.lib
            clangASTMatchers.lib
            clangSupport.lib
            clangAST.lib
            LLVMFrontendOpenMP.lib
            LLVMScalarOpts.lib
            LLVMAggressiveInstCombine.lib
            LLVMInstCombine.lib
            LLVMTransformUtils.lib
            LLVMAnalysis.lib
            LLVMProfileData.lib
            LLVMSymbolize.lib
            LLVMDebugInfoDWARF.lib
            LLVMDebugInfoPDB.lib
            LLVMObject.lib
            LLVMBitReader.lib
            LLVMCore.lib
            LLVMRemarks.lib
            LLVMBitstreamReader.lib
            LLVMMCParser.lib
            LLVMTextAPI.lib
            LLVMDebugInfoMSF.lib
            clangLex.lib
            clangBasic.lib
            lldbUtility.lib
            LLVMMCDisassembler.lib
            LLVMMC.lib
            LLVMBinaryFormat.lib
            LLVMDebugInfoCodeView.lib
            LLVMSupport.lib
            LLVMDemangle.lib
            psapi.lib
            shell32.lib
            ole32.lib
            uuid.lib
            advapi32.lib
            delayimp.lib
            ws2_32.lib
            rpcrt4.lib
            version.lib
            dbghelp.lib
            diaguids.lib
    )
elseif(APPLE)
	message(STATUS "Now is Apple systens.")
elseif(UNIX)
	message(STATUS "Now is UNIX-like OS's.")
else()
    message(FATAL_ERROR "Unknown platform." )
endif()



add_executable(${PROJECT_NAME}
        ${EXECUTABLE_EXTRA}
        Resources/resource.qrc
        main.cpp
        MainWindow.cpp
        MainWindow.h
        LLDBCore.cpp
        LLDBCore.h
        App.cpp
        App.h
        Utils.h
        Dialogs/SelectPlatformDlg.h
        Dialogs/SelectPlatformDlg.cpp
        Dialogs/OpenExeDlg.h
        Dialogs/OpenExeDlg.cpp
        Dialogs/AttachDlg.h
        Dialogs/AttachDlg.cpp
        Dialogs/AboutDlg.h
        Dialogs/AboutDlg.cpp
        Views/SymbolView.h
        Views/SymbolView.cpp
        Views/SourceView.h
        Views/SourceView.cpp
        Views/SourceListView.h
        Views/SourceListView.cpp
        Views/BreakpointView.h
        Views/BreakpointView.cpp
        Views/DisassemblyView.cpp
        Views/DisassemblyView.h
        Views/RegisterView.cpp
        Views/RegisterView.h
        Views/ThreadView.cpp
        Views/ThreadView.h
        Views/CallStackView.cpp
        Views/CallStackView.h
        Views/OutputView.cpp
        Views/OutputView.h
        Views/HexView.cpp
        Views/HexView.h
        Views/MemoryView.cpp
        Views/MemoryView.h
        Views/AbstractTableView.cpp
        Views/AbstractTableView.h
)

set(LIBLLDB_MODULE_NAME lldb)

if(MSVC)
    set_property(TARGET ${PROJECT_NAME} PROPERTY
            MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    set_property(TARGET kddockwidgets PROPERTY
            MSVC_RUNTIME_LIBRARY "MultiThreaded$<$<CONFIG:Debug>:Debug>")
    set(LIBLLDB_MODULE_NAME liblldb)
endif()

target_link_libraries(${PROJECT_NAME}
        ${REQUIRED_LIBS_QUALIFIED}
        KDAB::kddockwidgets
        ${LIBLLDB_MODULE_NAME}
        ${LIBS_EXTRA}
        )

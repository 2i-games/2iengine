# compile shaders

set(OUTPUT_DIR spirv)

set(SHADERS_CS
        "hairparticle_simulateCS.hlsl"
        "emittedparticle_simulateCS.hlsl"
        "generateMIPChainCubeCS_float4.hlsl"
        "generateMIPChainCubeCS_unorm4.hlsl"
        "generateMIPChainCubeArrayCS_float4.hlsl"
        "generateMIPChainCubeArrayCS_unorm4.hlsl"
        "generateMIPChain3DCS_float4.hlsl"
        "generateMIPChain3DCS_unorm4.hlsl"
        "generateMIPChain2DCS_float4.hlsl"
        "generateMIPChain2DCS_unorm4.hlsl"
        "blur_gaussian_float4CS.hlsl"
        "bloomseparateCS.hlsl"
        "depthoffield_mainCS.hlsl"
        "depthoffield_neighborhoodMaxCOCCS.hlsl"
        "depthoffield_prepassCS.hlsl"
        "depthoffield_upsampleCS.hlsl"
        "depthoffield_tileMaxCOC_verticalCS.hlsl"
        "depthoffield_tileMaxCOC_horizontalCS.hlsl"
        "voxelRadianceSecondaryBounceCS.hlsl"
        "voxelSceneCopyClearCS.hlsl"
        "voxelClearOnlyNormalCS.hlsl"
        "upsample_bilateral_float1CS.hlsl"
        "upsample_bilateral_float4CS.hlsl"
        "upsample_bilateral_unorm1CS.hlsl"
        "upsample_bilateral_unorm4CS.hlsl"
        "temporalaaCS.hlsl"
        "tileFrustumsCS.hlsl"
        "tonemapCS.hlsl"
        "ssr_resolveCS.hlsl"
        "ssr_temporalCS.hlsl"
        "ssaoCS.hlsl"
        "ssr_medianCS.hlsl"
        "ssr_raytraceCS.hlsl"
        "sharpenCS.hlsl"
        "skinningCS.hlsl"
        "skinningCS_LDS.hlsl"
        "resolveMSAADepthStencilCS.hlsl"
        "raytrace_shadeCS.hlsl"
        "raytrace_tilesortCS.hlsl"
        "raytrace_kickjobsCS.hlsl"
        "raytrace_launchCS.hlsl"
        "paint_textureCS.hlsl"
        "raytrace_closesthitCS.hlsl"
        "oceanUpdateDisplacementMapCS.hlsl"
        "oceanUpdateGradientFoldingCS.hlsl"
        "oceanSimulatorCS.hlsl"
        "msao_interleaveCS.hlsl"
        "msao_preparedepthbuffers1CS.hlsl"
        "msao_preparedepthbuffers2CS.hlsl"
        "msao_blurupsampleCS.hlsl"
        "msao_blurupsampleCS_blendout.hlsl"
        "msao_blurupsampleCS_premin.hlsl"
        "msao_blurupsampleCS_premin_blendout.hlsl"
        "msaoCS.hlsl"
        "motionblur_neighborhoodMaxVelocityCS.hlsl"
        "motionblur_tileMaxVelocity_horizontalCS.hlsl"
        "motionblur_tileMaxVelocity_verticalCS.hlsl"
        "luminancePass2CS.hlsl"
        "motionblur_kickjobsCS.hlsl"
        "motionblurCS.hlsl"
        "motionblurCS_cheap.hlsl"
        "motionblurCS_earlyexit.hlsl"
        "lineardepthCS.hlsl"
        "luminancePass1CS.hlsl"
        "lightCullingCS_DEFERRED_ADVANCED_DEBUG.hlsl"
        "lightCullingCS_DEFERRED_DEBUG.hlsl"
        "lightShaftsCS.hlsl"
        "lightCullingCS_ADVANCED_DEBUG.hlsl"
        "lightCullingCS_DEBUG.hlsl"
        "lightCullingCS_DEFERRED.hlsl"
        "lightCullingCS_DEFERRED_ADVANCED.hlsl"
        "lightCullingCS.hlsl"
        "lightCullingCS_ADVANCED.hlsl"
        "hbaoCS.hlsl"
        "gpusortlib_sortInnerCS.hlsl"
        "gpusortlib_sortStepCS.hlsl"
        "gpusortlib_kickoffSortCS.hlsl"
        "gpusortlib_sortCS.hlsl"
        "fxaaCS.hlsl"
        "filterEnvMapCS.hlsl"
        "fft_512x512_c2c_CS.hlsl"
        "fft_512x512_c2c_v2_CS.hlsl"
        "emittedparticle_sphpartitionCS.hlsl"
        "emittedparticle_sphpartitionoffsetsCS.hlsl"
        "emittedparticle_sphpartitionoffsetsresetCS.hlsl"
        "emittedparticle_simulateCS_SORTING.hlsl"
        "emittedparticle_simulateCS_SORTING_DEPTHCOLLISIONS.hlsl"
        "emittedparticle_sphdensityCS.hlsl"
        "emittedparticle_sphforceCS.hlsl"
        "emittedparticle_kickoffUpdateCS.hlsl"
        "emittedparticle_simulateCS_DEPTHCOLLISIONS.hlsl"
        "emittedparticle_emitCS.hlsl"
        "emittedparticle_emitCS_FROMMESH.hlsl"
        "emittedparticle_emitCS_volume.hlsl"
        "emittedparticle_finishUpdateCS.hlsl"
        "downsample4xCS.hlsl"
        "depthoffield_prepassCS_earlyexit.hlsl"
        "depthoffield_mainCS_cheap.hlsl"
        "depthoffield_mainCS_earlyexit.hlsl"
        "depthoffield_postfilterCS.hlsl"
        "depthoffield_kickjobsCS.hlsl"
        "copytexture2D_float4_borderexpandCS.hlsl"
        "copytexture2D_unorm4_borderexpandCS.hlsl"
        "copytexture2D_unorm4CS.hlsl"
        "copytexture2D_float4CS.hlsl"
        "chromatic_aberrationCS.hlsl"
        "bvh_hierarchyCS.hlsl"
        "bvh_primitivesCS.hlsl"
        "bvh_propagateaabbCS.hlsl"
        "blur_gaussian_wide_unorm1CS.hlsl"
        "blur_gaussian_wide_unorm4CS.hlsl"
        "blur_gaussian_unorm1CS.hlsl"
        "blur_gaussian_unorm4CS.hlsl"
        "blur_gaussian_wide_float1CS.hlsl"
        "blur_gaussian_wide_float3CS.hlsl"
        "blur_gaussian_wide_float4CS.hlsl"
        "blur_bilateral_wide_unorm4CS.hlsl"
        "blur_gaussian_float1CS.hlsl"
        "blur_gaussian_float3CS.hlsl"
        "blur_bilateral_unorm4CS.hlsl"
        "blur_bilateral_wide_float1CS.hlsl"
        "blur_bilateral_wide_float3CS.hlsl"
        "blur_bilateral_wide_float4CS.hlsl"
        "blur_bilateral_wide_unorm1CS.hlsl"
        "blur_bilateral_float1CS.hlsl"
        "blur_bilateral_float3CS.hlsl"
        "blur_bilateral_float4CS.hlsl"
        "blur_bilateral_unorm1CS.hlsl"
        "bloomcombineCS.hlsl"
        "voxelSceneCopyClearCS_TemporalSmoothing.hlsl"
)

set(SHADERS_DS
        "objectDS.hlsl"
)

set(SHADERS_PS
        "emittedparticlePS_soft.hlsl"
        "screenPS.hlsl"
        "imagePS_separatenormalmap.hlsl"
        "imagePS_separatenormalmap_bicubic.hlsl"
        "imagePS_backgroundblur_masked.hlsl"
        "imagePS_masked.hlsl"
        "imagePS_backgroundblur.hlsl"
        "imagePS.hlsl"
        "emittedparticlePS_soft_lighting.hlsl"
        "oceanSurfacePS.hlsl"
        "deferredPS.hlsl"
        "hairparticlePS_forward.hlsl"
        "hairparticlePS_tiledforward.hlsl"
        "impostorPS_forward.hlsl"
        "impostorPS_tiledforward.hlsl"
        "volumetricLight_SpotPS.hlsl"
        "volumetricLight_PointPS.hlsl"
        "volumetricLight_DirectionalPS.hlsl"
        "voxelPS.hlsl"
        "vertexcolorPS.hlsl"
        "trailPS.hlsl"
        "tubeLightPS.hlsl"
        "upsample_bilateralPS.hlsl"
        "sunPS.hlsl"
        "sssPS.hlsl"
        "sphereLightPS.hlsl"
        "spotLightPS.hlsl"
        "skyPS_dynamic.hlsl"
        "skyPS_static.hlsl"
        "shadowPS_transparent.hlsl"
        "shadowPS_water.hlsl"
        "shadowPS_alphatest.hlsl"
        "rectangleLightPS.hlsl"
        "renderlightmapPS.hlsl"
        "raytrace_debugbvhPS.hlsl"
        "pointLightPS.hlsl"
        "outlinePS.hlsl"
        "oceanSurfaceSimplePS.hlsl"
        "objectPS_tiledforward_transparent_pom.hlsl"
        "objectPS_tiledforward_water.hlsl"
        "objectPS_voxelizer.hlsl"
        "objectPS_voxelizer_terrain.hlsl"
        "objectPS_tiledforward_transparent.hlsl"
        "objectPS_tiledforward_transparent_normalmap.hlsl"
        "objectPS_tiledforward_transparent_normalmap_planarreflection.hlsl"
        "objectPS_tiledforward_transparent_normalmap_pom.hlsl"
        "objectPS_tiledforward_transparent_planarreflection.hlsl"
        "objectPS_tiledforward_normalmap_pom.hlsl"
        "objectPS_tiledforward_planarreflection.hlsl"
        "objectPS_tiledforward_pom.hlsl"
        "objectPS_tiledforward_terrain.hlsl"
        "objectPS_textureonly.hlsl"
        "objectPS_tiledforward.hlsl"
        "objectPS_tiledforward_normalmap.hlsl"
        "objectPS_tiledforward_normalmap_planarreflection.hlsl"
        "objectPS_forward_transparent_pom.hlsl"
        "objectPS_forward_water.hlsl"
        "objectPS_hologram.hlsl"
        "objectPS_paintradius.hlsl"
        "objectPS_simplest.hlsl"
        "objectPS_forward_transparent_normalmap_planarreflection.hlsl"
        "objectPS_forward_transparent_normalmap_pom.hlsl"
        "objectPS_forward_transparent_planarreflection.hlsl"
        "objectPS_forward_pom.hlsl"
        "objectPS_forward_terrain.hlsl"
        "objectPS_forward_transparent.hlsl"
        "objectPS_forward_transparent_normalmap.hlsl"
        "objectPS_forward.hlsl"
        "objectPS_forward_normalmap.hlsl"
        "objectPS_forward_normalmap_planarreflection.hlsl"
        "objectPS_forward_normalmap_pom.hlsl"
        "objectPS_forward_planarreflection.hlsl"
        "objectPS_deferred_normalmap_pom.hlsl"
        "objectPS_deferred_planarreflection.hlsl"
        "objectPS_deferred_pom.hlsl"
        "objectPS_deferred_terrain.hlsl"
        "objectPS_blackout.hlsl"
        "objectPS_debug.hlsl"
        "objectPS_deferred.hlsl"
        "objectPS_deferred_normalmap.hlsl"
        "objectPS_deferred_normalmap_planarreflection.hlsl"
        "objectPS_alphatestonly.hlsl"
        "lightVisualizerPS.hlsl"
        "lensFlarePS.hlsl"
        "impostorPS_wire.hlsl"
        "impostorPS_deferred.hlsl"
        "impostorPS_simple.hlsl"
        "impostorPS_alphatestonly.hlsl"
        "hairparticlePS_tiledforward_transparent.hlsl"
        "hairparticlePS_deferred.hlsl"
        "hairparticlePS_forward_transparent.hlsl"
        "hairparticlePS_simplest.hlsl"
        "hairparticlePS_alphatestonly.hlsl"
        "forceFieldVisualizerPS.hlsl"
        "fontPS.hlsl"
        "environmentalLightPS.hlsl"
        "envMap_skyPS_static.hlsl"
        "envMap_skyPS_dynamic.hlsl"
        "envMapPS.hlsl"
        "envMapPS_terrain.hlsl"
        "emittedparticlePS_soft_distortion.hlsl"
        "downsampleDepthBuffer4xPS.hlsl"
        "emittedparticlePS_simplest.hlsl"
        "dirLightPS.hlsl"
        "discLightPS.hlsl"
        "decalPS.hlsl"
        "cubeMapPS.hlsl"
        "circlePS.hlsl"
        "captureImpostorPS_normal.hlsl"
        "captureImpostorPS_surface.hlsl"
        "captureImpostorPS_albedo.hlsl"
)

set(SHADERS_VS
        "hairparticleVS.hlsl"
        "emittedparticleVS.hlsl"
        "imageVS.hlsl"
        "fontVS.hlsl"
        "voxelVS.hlsl" #ray tracing required
        "vertexcolorVS.hlsl"
        "vSpotLightVS.hlsl"
        "vTubeLightVS.hlsl"
        "vDiscLightVS.hlsl"
        "vPointLightVS.hlsl"
        "vRectangleLightVS.hlsl"
        "vSphereLightVS.hlsl"
        "trailVS.hlsl"
        "sphereVS.hlsl"
        "spotLightVS.hlsl"
        "skyVS.hlsl"
        "shadowVS_transparent.hlsl"
        "shadowVS.hlsl"
        "shadowVS_alphatest.hlsl"
        "screenVS.hlsl"
        "renderlightmapVS.hlsl"
        "raytrace_screenVS.hlsl"
        "pointLightVS.hlsl"
        "oceanSurfaceVS.hlsl"
        "objectVS_simple.hlsl"
        "objectVS_simple_tessellation.hlsl"
        "objectVS_voxelizer.hlsl"
        "objectVS_common.hlsl"
        "objectVS_common_tessellation.hlsl"
        "objectVS_debug.hlsl"
        "objectVS_positionstream.hlsl"
        "lensFlareVS.hlsl"
        "impostorVS.hlsl"
        "forceFieldPointVisualizerVS.hlsl"
        "forceFieldPlaneVisualizerVS.hlsl"
        "envMap_skyVS.hlsl"
        "envMapVS.hlsl"
        "dirLightVS.hlsl"
        "decalVS.hlsl"
        "cubeShadowVS.hlsl"
        "cubeShadowVS_alphatest.hlsl"
        "cubeVS.hlsl"
)

set(SHADERS_GS
        "voxelGS.hlsl"
        "objectGS_voxelizer.hlsl"
        "lensFlareGS.hlsl"
)

set(SHADERS_HS
        "objectHS.hlsl"
)

set(SHADERS_LIB
)


SET(SPIRV_BINARY_FILES)


#TODO find dxc

function(Generate_Shaders SHADERS_SRC_LIST SHADER_TYPE)
    foreach (Shader IN LISTS ${SHADERS_SRC_LIST})
        get_filename_component(FILE_NAME ${Shader} NAME_WLE)
        message(STATUS "SHADER ${SHADER_TYPE} ${FILE_NAME}")
        if (${SHADER_TYPE} STREQUAL vs OR ${SHADER_TYPE} STREQUAL ds OR ${SHADER_TYPE} STREQUAL gs)
            set(INVERT_Y TRUE)
        endif()
        set(SPIRV_OUTPUT "${CMAKE_CURRENT_SOURCE_DIR}/${OUTPUT_DIR}/${FILE_NAME}.cso")
        set(SPIRV_SOURCE "${CMAKE_CURRENT_SOURCE_DIR}/../${Shader}")
        add_custom_command(
                OUTPUT ${SPIRV_OUTPUT}
                COMMAND ${CMAKE_COMMAND} -E make_directory "${CMAKE_CURRENT_SOURCE_DIR}/spirv/"
                COMMAND "/opt/directx-shader-compiler/bin/dxc"
                "${SPIRV_SOURCE}"
                -T "${SHADER_TYPE}_6_4"
                -I "${CMAKE_CURRENT_SOURCE_DIR}/../"
                -D SPIRV
                -D
                $<$<STREQUAL:${SHADER_TYPE},vs>:SPIRV_SHADERSTAGE=0> # VS
                $<$<STREQUAL:${SHADER_TYPE},hs>:SPIRV_SHADERSTAGE=1> # HS
                $<$<STREQUAL:${SHADER_TYPE},ds>:SPIRV_SHADERSTAGE=2> # DS
                $<$<STREQUAL:${SHADER_TYPE},gs>:SPIRV_SHADERSTAGE=3> # GS
                $<$<STREQUAL:${SHADER_TYPE},ps>:SPIRV_SHADERSTAGE=4> # PS
                $<$<STREQUAL:${SHADER_TYPE},cs>:SPIRV_SHADERSTAGE=5> # CS or LIB
                $<$<STREQUAL:${SHADER_TYPE},lib>:SPIRV_SHADERSTAGE=5> # CS or LIB
                $<$<BOOL:${INVERT_Y}>:-fvk-invert-y>
                -spirv
#                -O1
                -fvk-use-dx-layout
                -flegacy-macro-expansion
                -Fo ${SPIRV_OUTPUT}
                -fspv-target-env=vulkan1.2
#                -fspv-extension=KHR
                DEPENDS ${SPIRV_SOURCE}
        )
        list(APPEND SPIRV_BINARY_FILES ${SPIRV_OUTPUT})
    endforeach()
    set(SPIRV_BINARY_FILES ${SPIRV_BINARY_FILES} PARENT_SCOPE)
endfunction()


Generate_Shaders(SHADERS_VS vs)
Generate_Shaders(SHADERS_HS hs)
Generate_Shaders(SHADERS_DS ds)
Generate_Shaders(SHADERS_GS gs)
Generate_Shaders(SHADERS_PS ps)
Generate_Shaders(SHADERS_CS cs)
Generate_Shaders(SHADERS_LIB lib)

add_custom_target(
        Shaders_SPIRV
        DEPENDS ${SPIRV_BINARY_FILES}
)
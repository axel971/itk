IF( NOT ITK_DISABLE_CXX_TESTING )
IF(ITK_BINARY_DIR)
  IF(TCL_TCLSH)
    ADD_TEST(PrintSelf-SpatialObject ${TCL_TCLSH}
             ${ITK_SOURCE_DIR}/Utilities/Dart/PrintSelfCheck.tcl  
             ${ITK_SOURCE_DIR}/Code/SpatialObject)
  ENDIF(TCL_TCLSH)
ENDIF(ITK_BINARY_DIR)


SET(SPATIAL_OBJECT_TESTS        ${CXX_TEST_PATH}/itkSpatialObjectTests)
SET(SPATIAL_OBJECT_TESTS2       ${CXX_TEST_PATH}/itkSpatialObjectTests2)
SET(SPATIAL_OBJECT_TESTS3       ${CXX_TEST_PATH}/itkSpatialObjectTests3)
SET(SPATIAL_OBJECT_TESTS4       ${CXX_TEST_PATH}/itkSpatialObjectTests4)
SET(SPATIAL_OBJECT_TESTS5       ${CXX_TEST_PATH}/itkSpatialObjectTests5)
SET(SPATIAL_OBJECT_HEADER_TEST  ${CXX_TEST_PATH}/itkSpatialObjectHeaderTest)

ADD_TEST( itkAffineGeometryFrameTest ${SPATIAL_OBJECT_TESTS} itkAffineGeometryFrameTest )
ADD_TEST( itkArrowSpatialObjectTest ${SPATIAL_OBJECT_TESTS} itkArrowSpatialObjectTest )

ADD_TEST( itkBoxSpatialObjectTest ${SPATIAL_OBJECT_TESTS3} 
  --compare ${ITK_DATA_ROOT}/Baseline/SpatialObjects/BoxSpatialObjectTest.png
            ${ITK_TEST_OUTPUT_DIR}/BoxSpatialObjectTest.png
  itkBoxSpatialObjectTest 
            ${ITK_TEST_OUTPUT_DIR}/BoxSpatialObjectTest.png)

ADD_TEST( itkBlobSpatialObjectTest ${SPATIAL_OBJECT_TESTS} itkBlobSpatialObjectTest )
ADD_TEST( itkCylinderSpatialObjectTest ${SPATIAL_OBJECT_TESTS5} itkCylinderSpatialObjectTest )
ADD_TEST( itkEllipseSpatialObjectTest ${SPATIAL_OBJECT_TESTS5} itkEllipseSpatialObjectTest)
ADD_TEST( itkGaussianSpatialObjectTest ${SPATIAL_OBJECT_TESTS5} itkGaussianSpatialObjectTest)
ADD_TEST( itkImageMaskSpatialObjectTest ${SPATIAL_OBJECT_TESTS4} itkImageMaskSpatialObjectTest )
ADD_TEST( itkImageMaskSpatialObjectTest2 ${SPATIAL_OBJECT_TESTS4} itkImageMaskSpatialObjectTest2 )
ADD_TEST( itkImageSpatialObjectTest ${SPATIAL_OBJECT_TESTS4} itkImageSpatialObjectTest )

ADD_TEST( itkMeshSpatialObjectTest ${SPATIAL_OBJECT_TESTS3} itkMeshSpatialObjectTest )
ADD_TEST( itkPlaneSpatialObjectTest ${SPATIAL_OBJECT_TESTS2} itkPlaneSpatialObjectTest )
ADD_TEST( itkPolygonGroupSpatialObjectTest ${SPATIAL_OBJECT_TESTS2} itkPolygonGroupSpatialObjectTest )
ADD_TEST( itkPolygonSpatialObjectTest ${SPATIAL_OBJECT_TESTS2} itkPolygonSpatialObjectTest )
ADD_TEST( itkSceneSpatialObjectTest ${SPATIAL_OBJECT_TESTS2} itkSceneSpatialObjectTest )
ADD_TEST( itkSpatialObjectTreeContainerTest ${SPATIAL_OBJECT_TESTS2} itkSpatialObjectTreeContainerTest )
ADD_TEST( itkSurfaceSpatialObjectTest ${SPATIAL_OBJECT_TESTS2} itkSurfaceSpatialObjectTest )
ADD_TEST( itkTubeSpatialObjectTest ${SPATIAL_OBJECT_TESTS2} itkTubeSpatialObjectTest )

ADD_TEST( itkLandmarkSpatialObjectTest ${SPATIAL_OBJECT_TESTS3} itkLandmarkSpatialObjectTest )
ADD_TEST( itkLineSpatialObjectTest ${SPATIAL_OBJECT_TESTS3} itkLineSpatialObjectTest )
ADD_TEST( itkSpatialObjectDuplicatorTest ${SPATIAL_OBJECT_TESTS3} itkSpatialObjectDuplicatorTest )
ADD_TEST( itkSpatialObjectPrintTest ${SPATIAL_OBJECT_TESTS3} itkSpatialObjectPrintTest)
ADD_TEST( itkSpatialObjectHeaderTest ${SPATIAL_OBJECT_HEADER_TEST})

ADD_TEST( itkMetaArrowConverterTest ${SPATIAL_OBJECT_TESTS5} itkMetaArrowConverterTest 
  ${ITK_TEST_OUTPUT_DIR}/MetaArrowConverterTestFile.mha)
ADD_TEST( itkContourSpatialObjectTest ${SPATIAL_OBJECT_TESTS5} itkContourSpatialObjectTest)

SET(SpatialObject_SRCS
  itkAffineGeometryFrameTest.cxx
  itkArrowSpatialObjectTest.cxx
  itkBlobSpatialObjectTest.cxx
)

SET(SpatialObject_SRCS5
  itkCylinderSpatialObjectTest.cxx
  itkEllipseSpatialObjectTest.cxx
  itkGaussianSpatialObjectTest.cxx
  itkMetaArrowConverterTest.cxx
  itkContourSpatialObjectTest.cxx
)

SET(SpatialObject_SRCS4
  itkImageMaskSpatialObjectTest.cxx
  itkImageMaskSpatialObjectTest2.cxx
  itkImageSpatialObjectTest.cxx
)

SET(SpatialObject_SRCS2
  itkPlaneSpatialObjectTest.cxx
  itkPolygonGroupSpatialObjectTest.cxx
  itkPolygonSpatialObjectTest.cxx
  itkSceneSpatialObjectTest.cxx
  itkSpatialObjectTreeContainerTest.cxx
  itkSurfaceSpatialObjectTest.cxx
  itkTubeSpatialObjectTest.cxx
)

SET(SpatialObject_SRCS3
  itkBoxSpatialObjectTest.cxx
  itkLandmarkSpatialObjectTest.cxx
  itkLineSpatialObjectTest.cxx
  itkMeshSpatialObjectTest.cxx
  itkSpatialObjectPrintTest.cxx
  itkSpatialObjectDuplicatorTest.cxx
)

ADD_EXECUTABLE(itkSpatialObjectTests itkSpatialObjectTests.cxx ${SpatialObject_SRCS})
TARGET_LINK_LIBRARIES(itkSpatialObjectTests ITKIO ITKSpatialObject)

ADD_EXECUTABLE(itkSpatialObjectTests2 itkSpatialObjectTests2.cxx ${SpatialObject_SRCS2})
TARGET_LINK_LIBRARIES(itkSpatialObjectTests2 ITKIO)

ADD_EXECUTABLE(itkSpatialObjectTests3 itkSpatialObjectTests3.cxx ${SpatialObject_SRCS3})
TARGET_LINK_LIBRARIES(itkSpatialObjectTests3 ITKIO ITKSpatialObject)

ADD_EXECUTABLE(itkSpatialObjectTests4 itkSpatialObjectTests4.cxx ${SpatialObject_SRCS4})
TARGET_LINK_LIBRARIES(itkSpatialObjectTests4 ITKIO ITKSpatialObject)

ADD_EXECUTABLE(itkSpatialObjectTests5 itkSpatialObjectTests5.cxx ${SpatialObject_SRCS5})
TARGET_LINK_LIBRARIES(itkSpatialObjectTests5 ITKIO ITKSpatialObject)

ADD_EXECUTABLE(itkSpatialObjectHeaderTest itkSpatialObjectHeaderTest.cxx)
TARGET_LINK_LIBRARIES(itkSpatialObjectHeaderTest ITKCommon)

IF(ITK_OBJCXX_COMPILER_WORKS)
  SET(SPATIALOBJECT_OBJCXX_TEST ${CXX_TEST_PATH}/itkSpatialObjectHeaderObjCxxTest)
  ADD_TEST(itkSpatialObjectHeaderObjCxxTest ${SPATIALOBJECT_OBJCXX_TEST})
  ADD_EXECUTABLE(itkSpatialObjectHeaderObjCxxTest itkSpatialObjectHeaderObjCxxTest.mm)
  TARGET_LINK_LIBRARIES(itkSpatialObjectHeaderObjCxxTest ITKCommon)
ENDIF(ITK_OBJCXX_COMPILER_WORKS)

ENDIF( NOT ITK_DISABLE_CXX_TESTING )


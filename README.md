# Limelightlib (WPILIB Java)
https://github.com/LimelightVision/limelightlib-wpijava/releases
## Usage
https://docs.limelightvision.io/docs/docs-limelight/apis/limelight-lib

## LimelightHelpers Static Methods

### Target Data
```java
public static boolean getTV(String limelightName)
public static double getTX(String limelightName)
public static double getTY(String limelightName)
public static double getTXNC(String limelightName)
public static double getTYNC(String limelightName)
public static double getTA(String limelightName)
public static double[] getT2DArray(String limelightName)
public static int getTargetCount(String limelightName)
public static RawFiducial[] getRawFiducials(String limelightName)
public static RawDetection[] getRawDetections(String limelightName)
```

### Neural Network Results
```java
public static int getClassifierClassIndex(String limelightName)  
public static int getDetectorClassIndex(String limelightName)
public static String getClassifierClass(String limelightName)
public static String getDetectorClass(String limelightName)
```

### Pose Estimation
```java
public static PoseEstimate getBotPoseEstimate_wpiBlue(String limelightName)
public static PoseEstimate getBotPoseEstimate_wpiRed(String limelightName)
public static PoseEstimate getBotPoseEstimate_wpiBlue_MegaTag2(String limelightName)
public static PoseEstimate getBotPoseEstimate_wpiRed_MegaTag2(String limelightName)

public static Pose3d getBotPose3d(String limelightName)
public static Pose3d getBotPose3d_wpiRed(String limelightName)
public static Pose3d getBotPose3d_wpiBlue(String limelightName)
public static Pose3d getBotPose3d_TargetSpace(String limelightName)
public static Pose3d getCameraPose3d_TargetSpace(String limelightName)
public static Pose3d getTargetPose3d_CameraSpace(String limelightName)
public static Pose3d getTargetPose3d_RobotSpace(String limelightName)
public static Pose3d getCameraPose3d_RobotSpace(String limelightName)

public static Pose2d getBotPose2d(String limelightName)
public static Pose2d getBotPose2d_wpiBlue(String limelightName)
public static Pose2d getBotPose2d_wpiRed(String limelightName)

public static double[] getBotPose(String limelightName)
public static double[] getBotPose_wpiRed(String limelightName)
public static double[] getBotPose_wpiBlue(String limelightName)
public static double[] getBotPose_TargetSpace(String limelightName)
public static double[] getCameraPose_TargetSpace(String limelightName)
public static double[] getTargetPose_CameraSpace(String limelightName)
public static double[] getTargetPose_RobotSpace(String limelightName)
```

### Camera/Pipeline Configuration
```java
public static void setPipelineIndex(String limelightName, int pipelineIndex)
public static void setPriorityTagID(String limelightName, int ID)
public static double getCurrentPipelineIndex(String limelightName)
public static String getCurrentPipelineType(String limelightName)

public static void setLEDMode_PipelineControl(String limelightName)
public static void setLEDMode_ForceOff(String limelightName)
public static void setLEDMode_ForceBlink(String limelightName)
public static void setLEDMode_ForceOn(String limelightName)

public static void setStreamMode_Standard(String limelightName)
public static void setStreamMode_PiPMain(String limelightName)
public static void setStreamMode_PiPSecondary(String limelightName)

public static void setCropWindow(String limelightName, double cropXMin, double cropXMax, double cropYMin, double cropYMax)
public static void setCameraPose_RobotSpace(String limelightName, double forward, double side, double up, double roll, double pitch, double yaw)
```

### Advanced AprilTag/Fiducial Settings
```java
public static void setFiducial3DOffset(String limelightName, double offsetX, double offsetY, double offsetZ)
public static void SetRobotOrientation(String limelightName, double yaw, double yawRate, double pitch, double pitchRate, double roll, double rollRate)
public static void SetFiducialIDFiltersOverride(String limelightName, int[] validIDs)
public static void SetFiducialDownscalingOverride(String limelightName, float downscale)
```

### Results and Data Access
```java
public static double getLatency_Pipeline(String limelightName)
public static double getLatency_Capture(String limelightName)
public static double[] getTargetColor(String limelightName)
public static double getFiducialID(String limelightName)
public static String getNeuralClassID(String limelightName)
public static String[] getRawBarcodeData(String limelightName)
public static String getJSONDump(String limelightName)
public static LimelightResults getLatestResults(String limelightName)
```

### Python Script Interface
```java
public static void setPythonScriptData(String limelightName, double[] outgoingPythonData)
public static double[] getPythonScriptData(String limelightName)
```

### Utility Methods
```java
public static CompletableFuture<Boolean> takeSnapshot(String tableName, String snapshotName)
public static NetworkTable getLimelightNTTable(String tableName)
public static NetworkTableEntry getLimelightNTTableEntry(String tableName, String entryName)
public static double getLimelightNTDouble(String tableName, String entryName)
public static void setLimelightNTDouble(String tableName, String entryName, double val)
public static void setLimelightNTDoubleArray(String tableName, String entryName, double[] val)
public static double[] getLimelightNTDoubleArray(String tableName, String entryName)
public static String getLimelightNTString(String tableName, String entryName)
public static URL getLimelightURLString(String tableName, String request)
```

## Core Classes

### PoseEstimate
Represents a 3D Pose Estimate with metadata

**Public Properties:**
- `Pose2d pose` - The estimated pose
- `double timestampSeconds` - Timestamp of the estimate
- `double latency` - Processing latency
- `int tagCount` - Number of tags used
- `double tagSpan` - Span between detected tags
- `double avgTagDist` - Average distance to tags
- `double avgTagArea` - Average area of tags
- `RawFiducial[] rawFiducials` - Raw fiducial detections
- `boolean isMegaTag2` - Whether this is a MegaTag2 result


### (NetworkTables-derived) RawFiducial
Represents raw AprilTag/Fiducial detection data

**Public Properties:**
- `int id` - AprilTag ID number
- `double txnc` - Horizontal offset from camera center in degrees
- `double tync` - Vertical offset from camera center in degrees
- `double ta` - Target area (0-100% of image)
- `double distToCamera` - Distance from camera to target in meters
- `double distToRobot` - Distance from robot to target in meters
- `double ambiguity` - AprilTag pose ambiguity score

### (NetworkTables-derived)  RawDetection
Represents raw neural network detection data

**Public Properties:**
- `int classId` - Neural network class ID
- `double txnc` - Horizontal offset from camera center in degrees
- `double tync` - Vertical offset from camera center in degrees
- `double ta` - Target area (0-100% of image)
- `double corner0_X` - First corner X coordinate
- `double corner0_Y` - First corner Y coordinate
- `double corner1_X` - Second corner X coordinate
- `double corner1_Y` - Second corner Y coordinate
- `double corner2_X` - Third corner X coordinate
- `double corner2_Y` - Third corner Y coordinate
- `double corner3_X` - Fourth corner X coordinate
- `double corner3_Y` - Fourth corner Y coordinate

### (JSON-derived) LimelightResults
Contains all results from a Limelight's JSON output

**Public Properties:**
- `String error` - Error message if any
- `double pipelineID` - Current pipeline index
- `double latency_pipeline` - Pipeline processing latency (ms)
- `double latency_capture` - Image capture latency (ms)
- `double latency_jsonParse` - JSON parsing latency (ms)
- `double timestamp_LIMELIGHT_publish` - Timestamp when data was published
- `double timestamp_RIOFPGA_capture` - Timestamp when RoboRIO FPGA captured the data
- `boolean valid` - Whether the target is valid
- `double[] botpose` - Robot pose in field space
- `double[] botpose_wpired` - Robot pose in WPILib Red alliance space
- `double[] botpose_wpiblue` - Robot pose in WPILib Blue alliance space
- `double botpose_tagcount` - Number of tags used for pose estimation
- `double botpose_span` - Span between detected tags
- `double botpose_avgdist` - Average distance to detected tags
- `double botpose_avgarea` - Average area of detected tags
- `double[] camerapose_robotspace` - Camera pose relative to robot
- `LimelightTarget_Retro[] targets_Retro` - Array of retroreflective targets
- `LimelightTarget_Fiducial[] targets_Fiducials` - Array of AprilTag targets
- `LimelightTarget_Classifier[] targets_Classifier` - Array of classifier results
- `LimelightTarget_Detector[] targets_Detector` - Array of detector results
- `LimelightTarget_Barcode[] targets_Barcode` - Array of barcode results

**Public Methods:**
- `Pose3d getBotPose3d()`
- `Pose3d getBotPose3d_wpiRed()`
- `Pose3d getBotPose3d_wpiBlue()`
- `Pose2d getBotPose2d()`
- `Pose2d getBotPose2d_wpiRed()`
- `Pose2d getBotPose2d_wpiBlue()`


### (JSON-derived) LimelightTarget_Retro
Represents a Color/Retroreflective Target Result

**Public Properties:**
- `double ta` - Target area (0-100% of image)
- `double tx` - Horizontal offset from crosshair to target (-29.8 to 29.8 degrees)
- `double ty` - Vertical offset from crosshair to target (-24.85 to 24.85 degrees)
- `double tx_pixels` - Horizontal offset in pixels
- `double ty_pixels` - Vertical offset in pixels
- `double tx_nocrosshair` - Horizontal offset from camera center
- `double ty_nocrosshair` - Vertical offset from camera center
- `double ts` - Target skew or rotation (-90 to 0 degrees)

**Public Methods:**
- `Pose3d getCameraPose_TargetSpace()`
- `Pose3d getRobotPose_FieldSpace()`
- `Pose3d getRobotPose_TargetSpace()`
- `Pose3d getTargetPose_CameraSpace()`
- `Pose3d getTargetPose_RobotSpace()`
- `Pose2d getCameraPose_TargetSpace2D()`
- `Pose2d getRobotPose_FieldSpace2D()`
- `Pose2d getRobotPose_TargetSpace2D()`
- `Pose2d getTargetPose_CameraSpace2D()`
- `Pose2d getTargetPose_RobotSpace2D()`

### (JSON-derived) LimelightTarget_Fiducial
Represents an AprilTag/Fiducial Target Result

**Public Properties:**
- `double fiducialID` - AprilTag ID number
- `String fiducialFamily` - AprilTag family type
- All properties from LimelightTarget_Retro

**Public Methods:**
- All methods from LimelightTarget_Retro

### (JSON-derived) LimelightTarget_Barcode
Represents a Barcode Target Result

**Public Properties:**
- `String family` - Barcode family type (e.g. "QR", "DataMatrix")
- `String data` - Decoded barcode data content
- `double tx_pixels` - Horizontal offset in pixels
- `double ty_pixels` - Vertical offset in pixels
- `double tx` - Horizontal offset from crosshair
- `double ty` - Vertical offset from crosshair
- `double tx_nocrosshair` - Horizontal offset from camera center
- `double ty_nocrosshair` - Vertical offset from camera center
- `double ta` - Target area
- `double[][] corners` - Corner coordinates

**Public Methods:**
- `String getFamily()`

### (JSON-derived) LimelightTarget_Classifier
Represents a Neural Classifier Pipeline Result

**Public Properties:**
- `String className` - Detected class name
- `double classID` - Detected class ID number
- `double confidence` - Detection confidence (0-100%)
- `double zone` - Detection zone
- `double tx` - Horizontal offset from crosshair
- `double ty` - Vertical offset from crosshair
- `double txp` - Horizontal offset in pixels
- `double typ` - Vertical offset in pixels

### (JSON-derived) LimelightTarget_Detector
Represents a Neural Detector Pipeline Result

**Public Properties:**
- `String className` - Detected class name
- `double classID` - Detected class ID number
- `double confidence` - Detection confidence (0-100%)
- `double ta` - Target area
- `double tx` - Horizontal offset from crosshair
- `double ty` - Vertical offset from crosshair
- `double txp` - Horizontal offset in pixels
- `double typ` - Vertical offset in pixels
- `double tx_nocrosshair` - Horizontal offset from camera center
- `double ty_nocrosshair` - Vertical offset from camera center

# Object Correspondence in Digital-Twin Terrain Using PX4 Autopilot

## 📌 Project Aim
Simulated and analyzed object correspondence in a custom terrain using a PX4-based UAV.  
The drone detects, localizes, and tracks specific rocks across multiple environments to study displacement caused by hypothetical events (e.g., natural calamities).

---

## 🎯 Motivation
This work mimics challenges faced in planetary exploration:
- Monitoring remote sites  
- Detecting environmental changes  
- Automating data logging and analysis  

---

## 🛠️ Methodology

### Terrain Modeling
- Captured real-world images → processed in **Meshroom** for 3D reconstruction  
- Cleaned and scaled models in **Blender**  
- Exported terrain into **Gazebo** for UAV simulation  

### System Architecture
- **Drone Launch Pipeline**: PX4 x500_depth + Gazebo integration  
- **YOLOv8 Detection Node**: Custom-trained on rock dataset, real-time bounding box detection  
- **Coordinate Conversion**: Mapped pixel detections to 3D world coordinates using depth + TF2 transforms  
- **Odometry TF Broadcaster**: Maintained world ↔ drone localization  
- **Teleoperation**: Keyboard control for testing and validation  

### Data Workflow
`Spawn drone & environment → Detect rocks → Log coordinates → Compare across terrains`

---

## 🚀 Highlights
- ✅ >90% detection accuracy with YOLOv8 on test images  
- ✅ Localization precision: error ~0.1–0.2m  
- ✅ Efficient simulation: Gazebo loads optimized terrain in <15s  
- ✅ Change detection: Successfully tracked ~0.4m rock displacement  

---

## ⚠️ Limitations
- No SLAM → odometry drift remains  
- Manual rock correspondence across environments  
- Assumes static camera-drone calibration  

---

## 🔮 Future Directions
- Integrate **ORB-SLAM3/Cartographer** for drift correction  
- Automate rock matching with nearest-neighbor algorithms  
- Deploy **ArUco markers** for calibration  
- Extend to real drone platforms & onboard computation  
- Use **point cloud analysis** for scene-level correspondence  

---

## 📖 Takeaway
This project demonstrates a full end-to-end pipeline bridging **AI vision models with robotics simulation**.  
It lays the groundwork for **autonomous planetary exploration** and **long-term environmental monitoring** using UAVs.

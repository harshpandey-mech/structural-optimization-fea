# Structural Component Analysis & Optimization
### SOLIDWORKS Simulation | FEA | Topology Optimization | Al 6061-T6

---

## 📌 Project Overview

This project performs **static Finite Element Analysis (FEA) and iterative mass optimization** of a suspension upright for a Formula Student–class race car using SOLIDWORKS Simulation. The upright is subjected to combined real-world load cases and redesigned iteratively to minimize mass while maintaining a Factor of Safety ≥ 2.5 across all loading conditions.

The suspension upright is one of the most structurally critical components on a race car — it connects the wheel hub to the suspension wishbones and must withstand simultaneous braking, cornering, and bump forces.

---

## 🎯 Objectives

- Perform multi-load-case static FEA on the suspension upright
- Apply von Mises yield criterion for failure assessment
- Conduct iterative topology-inspired design optimization
- Achieve target mass reduction while maintaining structural safety

---

## ⚙️ Methodology

### Material
- **Aluminium 6061-T6**
- Yield strength (σ_y): 276 MPa
- Ultimate tensile strength: 310 MPa
- Density: 2700 kg/m³
- Young's Modulus: 68.9 GPa

### Load Cases Applied
Three simultaneous load cases based on standard vehicle dynamics analysis:

| Load Case | Acceleration | Force at Hub (approx.) |
|---|---|---|
| Braking | 1.5g longitudinal | 2120 N forward |
| Cornering | 2.0g lateral | 2830 N lateral |
| Bump | 3.0g vertical | 4240 N vertical |

Load combinations applied as worst-case superposition. Loads derived from vehicle mass of 320 kg with driver, tyre contact patch as force application point.

### FEA Setup — SOLIDWORKS Simulation
| Setting | Value |
|---|---|
| Element type | Solid tetrahedral (second-order) |
| Mesh quality | High (curvature-based) |
| Min element size | 1.5 mm (at fillets and stress concentrations) |
| Fixture | Fixed geometry at wishbone mounting holes |
| Load application | Split face at hub bearing bore |
| Failure criterion | von Mises stress vs. yield strength |

### Design Optimization Process
4 design iterations performed:
1. **Baseline:** Solid block geometry — FEA run to identify load paths
2. **Iteration 1:** Remove clearly unloaded material — visual topology guide
3. **Iteration 2:** Add gussets at high-stress zones, remove bulk from low-stress web
4. **Iteration 3:** Pocket and rib structure refined based on stress contour maps
5. **Final:** Full FEA verification on optimized geometry

Target FoS ≥ 2.5 (σ_allowable = 276 / 2.5 = **110.4 MPa**) maintained throughout.

---

## 📊 Results

| Iteration | Mass (kg) | Peak von Mises Stress (MPa) | FoS | Status |
|---|---|---|---|---|
| Baseline | 1.86 | 61 | 4.5 | Over-designed |
| Iteration 1 | 1.71 | 79 | 3.5 | Pass |
| Iteration 2 | 1.58 | 95 | 2.9 | Pass |
| Iteration 3 | 1.48 | 103 | 2.7 | Pass |
| **Final** | **1.43** | **108** | **2.55** | ✅ **Pass** |

**Key Results:**
- **Mass reduction: 23%** (1.86 kg → 1.43 kg)
- Peak stress of 108 MPa — **61% below yield limit** of 276 MPa
- FoS = 2.55 — exceeds minimum design target of 2.5
- Maximum deformation under worst-case combined load: 0.31 mm

**Key Finding:** The majority of reducible mass was located in the central web section of the original block geometry, which carried < 30% of the load path. By converting this to a ribbed pocket structure, significant weight was saved with minimal stiffness penalty.

---

## 📁 Repository Structure

```
structural-optimization-fea/
│
├── README.md
│
├── cad/
│   ├── upright_baseline.SLDPRT        # Original solid geometry
│   ├── upright_iteration1.SLDPRT
│   ├── upright_iteration2.SLDPRT
│   ├── upright_iteration3.SLDPRT
│   ├── upright_final.SLDPRT           # Optimized final design
│   └── upright_drawing.pdf            # 2D engineering drawing with dimensions
│
├── fea_setup/
│   ├── load_cases.md                  # Exact load values and application points
│   ├── mesh_settings.md               # Mesh parameters for reproducibility
│   └── material_properties.md        # Full Al 6061-T6 property table
│
├── results/
│   ├── stress_contour_baseline.png
│   ├── stress_contour_final.png
│   ├── deformation_plot.png
│   ├── mass_vs_iteration.png
│   └── fos_vs_iteration.png
│
└── data/
    └── iteration_summary.xlsx         # Mass, stress, FoS for all iterations
```

> **Note:** SOLIDWORKS `.SLDPRT` files require SOLIDWORKS 2021 or later to open. Screenshots of all geometry and FEA results are available in `results/`.

---

## 🔧 Software Required

- SOLIDWORKS 2021 or later
- SOLIDWORKS Simulation add-in (included in most educational licences)

---

## 📚 References

- Shigley's Mechanical Engineering Design, 10th Ed. — McGraw Hill
- SOLIDWORKS Simulation Help Documentation
- Formula Student Rules 2024 — Structural component design requirements
- Aluminum Association — Al 6061-T6 material data sheet

---

## 👤 Author

**Harsh Pandey**  
B.Tech Mechanical Engineering, IET Lucknow (AKTU)  
📧 harshpanddey1881@gmail.com 

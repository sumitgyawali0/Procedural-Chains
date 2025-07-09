# Procedural Chain Simulation with Rigid Body Dynamics

A comprehensive Houdini-based procedural chain simulation system featuring dual-approach workflows for different shot requirements, optimized for Unreal Engine integration.

## 🎯 Project Overview

This project demonstrates two complementary approaches to procedural chain simulation:
- **Vellum Hair Simulation**: Optimized for wide shots and multiple chain strands
- **Bullet Solver System**: Designed for close-up shots requiring detailed ring interactions

## 🚀 Features

- **Procedural Chain Generation**: Automated chain creation between any two surfaces
- **Dual Simulation Approach**: Performance-optimized workflows for different shot scales
- **Unreal Engine Ready**: Optimized mesh export pipeline
- **Flexible Configuration**: Easily adjustable chain count, length, and physics parameters
- **Realistic Physics**: Proper chain dynamics with bending and stretching controls

## 📋 Requirements

- **Houdini 19.5+** (tested on 19.5 and 20.0)
- **Unreal Engine 5.0+** (for final integration)
- Basic knowledge of Houdini VEX and simulation workflows

## 🔧 Installation

1. Clone this repository:
```bash
git clone https://github.com/yourusername/procedural-chain-simulation.git
```

2. Open Houdini and navigate to the project directory

3. Load the main scene file


## 🎮 Usage

### Quick Start

1. **Load the Master Scene**: Open the provided project file
2. **Set Source Objects**: Assign your geometry to the "source" and "target" object parameters
3. **Configure Chain Count**: Adjust the chain strand count in the interface
4. **Choose Simulation Type**: Select between Vellum or Bullet approach based on your needs
5. **Run Simulation**: Execute the simulation and iterate on parameters

### Vellum Hair Approach (Recommended for Wide Shots)

```python
# Key VEX expression for point ID assignment
i@id = @ptnum;
```

**Best for:**
- Wide shots with multiple chain strands
- Scenes requiring efficient performance
- Long chain sequences
- Multiple simultaneous simulations

### Bullet Solver Approach (Recommended for Close-ups)

```python
# Active point control for static elements
i@active = 0;
```

**Best for:**
- Close-up shots requiring detailed interactions
- Ring-to-ring collision dynamics
- Hero chain sequences
- Detailed physics simulation

## ⚙️ Parameters

### Global Settings
- `Chain Count`: Number of chain strands (1-100)
- `Chain Length`: Length of each chain strand
- `Ring Scale`: Size of individual chain rings
- `Simulation Type`: Choose between Vellum and Bullet approaches

### Vellum Parameters
- `Bend Stiffness`: Controls chain flexibility (0.0 - 1.0)
- `Stretch Stiffness`: Prevents chain stretching (0.8 - 1.0)
- `Damping`: Overall simulation damping (0.0 - 1.0)

### Bullet Parameters
- `Mass`: Chain ring mass (0.1 - 10.0)
- `Bounce`: Collision bounce factor (0.0 - 1.0)
- `Friction`: Surface friction (0.0 - 1.0)

## 🎯 Unreal Engine Integration

### Export Pipeline

The project includes optimized export settings for Unreal Engine:

1. **Mesh Triangulation**: All geometry is triangulated for UE compatibility
2. **Attribute Cleanup**: Only normals and UV attributes are retained
3. **Group Cleanup**: Unnecessary Houdini groups are removed
4. **Degenerate Cleanup**: Clean operation removes problematic geometry

### Export Process

1. Navigate to the "Export" tab in the master scene
2. Select your target simulation cache
3. Run the "Optimize for Unreal" process
4. Export as FBX or Alembic based on your pipeline needs

## 🔧 Troubleshooting

### Common Issues

**Chains not connecting properly:**
- Check that source and target objects have sufficient point density
- Verify ID assignments are unique for each chain strand

**Performance issues:**
- Use Vellum approach for scenes with high chain counts
- Reduce simulation substeps for faster iteration
- Consider using proxy geometry during development

**Unreal Engine compatibility:**
- Ensure all meshes are triangulated before export
- Check that UV coordinates are properly assigned
- Verify normal vectors are consistent

## 📚 Technical Details

### Vellum Implementation
The vellum approach uses Houdini's hair simulation system with custom constraints to mimic chain behavior. Key components:
- Point scattering system for chain attachment
- ID-based connection system
- Resampling for consistent chain segment length
- Custom bending/stretching parameters

### Bullet Implementation
The bullet solver provides detailed rigid body dynamics:
- Individual chain ring physics
- Collision detection between rings
- Active/passive point control
- Constraint-based connections

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature-name`
3. Commit your changes: `git commit -m 'Add feature description'`
4. Push to the branch: `git push origin feature-name`
5. Submit a pull request



## 🙏 Acknowledgments

- Houdini community for simulation techniques and workflows
- Client project team for real-world testing and feedback
- Unreal Engine documentation for integration guidelines

---

*This project was developed as part of a production pipeline R&D initiative, combining procedural techniques with practical performance considerations for real-world applications.*

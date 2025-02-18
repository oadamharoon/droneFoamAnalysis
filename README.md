# droneFoamAnalysis
OpenFOAM CFD analysis for drones.

# 1. Create a new case directory

mkdir -p $FOAM_RUN/droneAnalysis

cd $FOAM_RUN/droneAnalysis

# 2. Create the basic OpenFOAM directory structure

mkdir -p constant/triSurface

mkdir -p system

mkdir -p 0

# Copy your drone STL file

cp "/mnt/c/Users/oadam/Downloads/Transforming UAV Final Overall With Open Wings.STL" constant/triSurface/drone.stl

# 3. Create and fill blockMeshDict

cd $FOAM_RUN/droneAnalysis/system

nano blockMeshDict

Copy everything from the code between "// system/blockMeshDict" and the next section marker

# 4. Create and fill initial conditions for velocity

cd ../0

nano U

Copy everything from the code between "// 0/U" and the next section marker

# 5. Create and fill pressure conditions

nano p

Copy everything from the code between "// 0/p" and the next section marker

# 6. Back to system directory for controlDict

cd ../system

nano controlDict

Copy everything from the code between "// system/controlDict" and the next section marker

# 7. Create and fill snappyHexMeshDict

nano snappyHexMeshDict

Copy everything from the code between "// system/snappyHexMeshDict" to the end

# 8. Generate the basic mesh

cd ..

blockMesh

# 9. Create the mesh around your drone

snappyHexMesh -overwrite

# 10. Run the simulation

simpleFoam

# 11. View the results

paraFoam

# Social Force Model (SFM) Pedestrian Simulation

## Objective
Simulate pedestrian dynamics using the **Social Force Model (SFM)** and 
analyze how macroscopic contact properties emerge from microscopic interactions
with an obstacle.

## Methodology
- Social Force Model (SFM) for pedestrian movement
- 5th-order Gear predictor-corrector integration
- Contact forces (normal and tangential) based on linear spring-damper model
- Driving force toward a random desired direction for each pedestrian
- Periodic boundary conditions with a central fixed obstacle

## Results
- System reaches a stationary regime with constant contact rates
- Unique accumulated contacts grow linearly with time after a transient period
- Contact slope ($Q$) analyzed as a function of the area fraction ($\phi$)
- Identification of collision patterns and pedestrian-obstacle interaction dynamics

## Conclusion
The simulator produces **stable and physically consistent results** using the
Social Force Model integrated with a high-order predictor-corrector method.  
Macroscopic observables, such as the contact rate, naturally emerge from the
microscopic force definitions, validating the modeling approach for
pedestrian-obstacle interactions.

---

## Additional Material

- **Presentation**: Full methodology, equations, plots, and error analysis are
  documented in the slides used for the oral defense:  
  `/analysis/SdS-TP5-2025Q2G02_Presentación.pdf`

- **Simulation Visualizations (Videos)**:
    - **Pedestrian dynamics and obstacle interaction**  
      https://youtu.be/3yjdBzG9-yQ

- **Local Visualization**:
    - Example animations can be generated using the provided Python scripts in `output-parsing/`.
    - Raw animation data and rendered outputs are stored in the `animations/` directory.

---

## Execution (Reproducibility)

### Compile
```bash
javac PedestrianDynamic/src/*.java -d out/production/SDS-TP5
````

### Generate Initial Conditions

```bash
# Usage: java ParticlesGenerator <N> <L> <speed> <rMin> <rMax> <iterations> <mass>
java -cp out/production/SDS-TP5 ParticlesGenerator 100 6.0 2.0 0.15 0.24 5 80.0
```

### Run Simulation

```bash
# Usage: java Simulator <N> <L> <iterations> <inputDir> <outputDir> <maxT> <deltaT> <writeInterval>
java -cp out/production/SDS-TP5 Simulator 100 6.0 1 ./inputs ./outputs 50 0.0001 0.1
```

### Optional Visualization

```bash
# Usage: python3 output-parsing/animation.py <file_path> --maxT <maxT> [--L <L>] [--save]
python3 output-parsing/animation.py outputs/N_100_L6.000/output_*.csv --maxT 50 --L 6.0
```

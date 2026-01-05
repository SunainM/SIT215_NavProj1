# Wheelchair Navigation System

This project implements a wheelchair-friendly navigation solution as part of the SIT215 Computational Intelligence assignment. The system is designed to find accessible routes through environments such as campuses or neighbourhoods by considering factors like kerb ramps, slopes, and indoor lifts.

## Project Overview

The goal of this project is to:

- Build an environment map annotated with accessible path segments.
- Implement the A\* algorithm for computing optimal routes based on wheelchair accessibility.
- Expand and enhance the initial navigation solution by adding extra environmental constraints.
- Compare multiple heuristics and explore an alternative pathfinding algorithm for performance analysis.
- _(Bonus Task)_ Develop a Graphical User Interface (GUI) for inputting start/end points and visualizing routes.

This README provides instructions on how to run the code, the project structure, and any necessary dependencies.

## File Structure

```
├── Project.ipynb                # Main Jupyter Notebook with the complete implementation.
├── Tiled                        # Directory for Map
    ├── Map.tmx                  # Map file containing the annotated environment.
    ├── sample_tiles.png         # Tile image file used for map visualization.
├── README.md                    # This file.
├── [S224089221]_assign1problemsolving_report.pdf  # Assignment report (separate from the code).
├── gui_video_demo.mp4           # Video Demonstration for GUI
```

### Notes:

- The first code block in `Project.ipynb` contains code that generates the map. You can save the output as `Map.tmx`. It is preferable to store this file in a folder named `Tiled` inside the project directory.
- If using the GUI, make sure `sample_tiles.png` is also located inside the `Tiled` folder.

## Dependencies

Ensure you have the following software and libraries installed:

- **Python 3.7+**
- **Jupyter Notebook / JupyterLab** – for running the notebook files.
- **numpy**
- **matplotlib**
- **pandas**
- **IPython**
- **pygame**
- **pytmx**

You can install the Python libraries using pip:

```bash
pip install numpy matplotlib ipython jupyter pygame pytmx pandas
```

If additional open-source libraries are used within the project, please refer to the code comments or additional documentation provided.

## How to Run the Code

### Step 1: Initialize the Game Code

Run the first code block in the notebook to define the game and load all necessary functions and classes.

### Option 1: Run With GUI

1. Initialize the game instance with GUI:

```python
problem_instance = Problem(map_path, gui=True)
```

2. Run the instance:

```python
problem_instance.run()
```

3. **Navigation in the UI:**
   - Starts with a **Start Screen** — press `Enter` to proceed.
   - A map is displayed with a **Toggle Button** on the top-left to switch between layers.
   - Select a **starting point** by clicking on any non-red tile, press `Enter` to confirm.
   - Then, select a **destination**, confirm with `Enter` again.
   - The screen shows **best paths** for both **A\*** (blue) and **Dijkstra** (yellow). Press `Visualize` to view them.
   - Use `Esc` to restart with different points or toggle layers to explore the path perspectives.
   - **Exit** the window to end the process.
   - To make code-level changes:
     - Interrupt the `problem_instance.run()` block.
     - Modify parameters or functions in a new code cell.
     - Re-run the instance.

### Option 2: Run Without GUI

1. Initialize the instance:

```python
problem = Problem(map_path, gui=False)
```

2. Set source and destination points as tuples of 3 integers:

```python
problem.source = (1, 2, 1)
problem.destination = (3, 4, 0)
```

- Valid range:
  - For z = 0: x, y ∈ [0, 49]
  - For z = 1: x ∈ [0, 49], y ∈ [16, 49]
  - z ∈ [0, 1]
- Using invalid coordinates will result in an error.

3. Run analysis:

```python
problem.analyze()
```

4. Get results:

```python
problem.get_results()
```

## Methods and Properties

- `problem.source = (int, int, int)`
- `problem.destination = (int, int, int)`
- `problem.set_agent_speed(value)`
- `problem.set_heuristic_multiplier(value)`
- `problem.set_use_friction_for_dijkstra(True/False)`
- `problem.analyze()`
- `problem.get_agent_speed()`
- `problem.get_heuristic_multiplier()`
- `problem.get_results()`
- `problem.top_resul`ts()

## Code Overview

The code is structured into different sections:

- **Environment Representation:** Defines the map, nodes, and adjacency matrix representing the location connectivity and costs.
- **Pathfinding Implementation:** Utilizes the A\* algorithm to find the best wheelchair-accessible route between two points.
- **Enhanced Features & Alternative Algorithm:** Contains methods to incorporate additional constraints (e.g., kerb ramps, obstacles) and compares a new heuristic against the basic A\* solution.
- **GUI (Bonus Task):** Provides an interactive interface for users to input start/end points and visualize the computed route.

For a detailed explanation of each module and function, please refer to the inline code comments in `Project.ipynb`.

## Testing and Evaluation

- The implementation has been tested with multiple start and end points to ensure the validity and optimality of the computed routes.
- Comparative performance evaluation between the basic A\* heuristic and the enhanced heuristic (and an alternative algorithm, if implemented) is presented in the report ([S224089221]\_assign1problemsolving_report.pdf).

## Author

_Sunain Mushtaq_\
_S224089221_

## Acknowledgements

The project was developed as an assignment for SIT215 Computational Intelligence. Special thanks to the teaching team and peers for their guidance and support.

---

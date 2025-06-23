# ImolaProject - Pitlane Protocol Simulation

This project simulates a Vehicle-to-Infrastructure protocol inspired by the "Box Box" command used in Formula 1 racing. It enables an RSU (Road Side Unit) to selectively reroute autonomous vehicles into a Pitlane using periodic broadcast messages. The simulation runs over a digital version of the Imola circuit using **SUMO**, **OMNeT++**, and **Veins**.

## 🧹 Project Structure

The repository contains the full simulation setup:

```
imola/
├── antenna.xml
├── config.xml
├── imola                  # Executable scenario file
├── imola.launchd.xml      # Launch configuration
├── imola.rou.xml          # Route file with vehicle definitions
├── ImolaScenario.ned      # OMNeT++ network description
├── Makefile               # Build config
├── omnetpp.ini            # Simulation parameters
├── rerouter.add.xml       # Rerouting logic
├── osm.*                  # SUMO network, poly and config files
├── .oppbuildspec, .cproject, etc.
```

## 🚀 Getting Started

### 1. Install Dependencies

Ensure the following tools are properly installed:

* [OMNeT++ 6.x](https://omnetpp.org/)
* [SUMO 1.16+](https://sumo.dlr.de/)
* [Veins (matching OMNeT++ version)](https://veins.car2x.org/)

> We recommend placing this folder inside your OMNeT++ workspace, for example at:
> `~/omnetpp_workspace/imola/`

### 2. Build the Project

In OMNeT++ IDE:

* Import the project via:
  **File > Import > Existing Project into Workspace**
* Clean and build using **Project > Clean...** and then **Build All**

Or from terminal:

```bash
cd imola
make
```

### 3. Run the Simulation

In OMNeT++:

* Right-click `imola.launchd.xml` > **Run As > OMNeT++ Simulation**
* Choose the configuration from `omnetpp.ini`
* Ensure SUMO GUI launches — the vehicles will begin circling the Imola circuit.

### 4. Expected Behavior

* Every 5 seconds, the RSU emits a **"Box Box"** message to a specific vehicle ID.
* If the vehicle matches the ID, it will:

  * Reroute to the Pitlane.
  * Change color from **yellow** to **turquoise**.
  * Reduce speed to **80 km/h** in the Pitlane (from \~300 km/h).

The `omnetpp.ini` and FSM logic fully define the selective behavior of this command protocol.

## 📂 Output & Results

Simulation logs and animation data are stored in the `/results` folder.

For more detail, consult the [Technical Report PDF](./Imola_Project_Marc_Guitart.pdf) included in the repository.

---

## 📌 License

This work is licensed under the Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License.
See [LICENSE](https://creativecommons.org/licenses/by-nc-sa/4.0/legalcode).

---

## 🧠 Authors

Marc Guitart Frescó
MSc in Computer Science
University of Brescia (Italy)

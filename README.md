# Simple simulation of the fear mechanism


TLDR: Pasting this in terminal should run the fear simulation
conda create --name fear_sim python=3.10
conda activate fear_sim
pip install neuron bmtk uflash
cd components/mechanisms
nrnivmodl .
cd ../..
rm -f config.json circuit_config.json simulation_config.json
python build_network.py
python update_configs.py
python run_bionet.py config.json
python check_output.py output


🧠 Fear Circuit Simulation (Mini-Project-1A)

This project simulates oscillatory activity in a simplified brain “fear circuit” using:

NEURON 9.x

BMTK (Brain Modeling Toolkit)

Python 3.10

Optional: micro:bit flashing via uflash

The simulation allows you to inject different levels of current and observe the resulting oscillation frequency of the network.

📦 Requirements

Install:

Python 3.10 (recommended via Anaconda)

NEURON 9.x

BMTK

Optional: uflash (for micro:bit flashing)

🛠️ Setup Instructions
1️⃣ Create and Activate a Conda Environment
conda create --name fear_sim python=3.10
conda activate fear_sim
2️⃣ Install Required Libraries
Mac / Linux:
pip install neuron
pip install bmtk
pip install uflash   # optional (for micro:bit)
Windows:

Install NEURON from:
https://www.neuron.yale.edu/neuron/download

Then run:

pip install bmtk
pip install uflash

If NEURON is not recognized, follow the instructions in neuron9_installation.txt.

3️⃣ Compile the Mechanism (.mod) Files

Navigate to the mechanisms folder and compile:

cd fear_simulation/components/mechanisms
nrnivmodl .
cd ../..

You should see:

Successfully created x86_64/special

This step is required before running the simulation.

▶️ Running the Simulation
Step 1 — Set the Current Injection

Open parameters.py and modify:

I_E = 0.2

or

I_E = 1.0

These values represent injected current in nanoamps (nA).

Step 2 — Remove Old Configuration Files

Each time you change parameters, delete old config files:

rm -f config.json circuit_config.json simulation_config.json
Step 3 — Build and Update the Network
python build_network.py
python update_configs.py
Step 4 — Run the Simulation
python run_bionet.py config.json

You should see output similar to:

Running simulation for 1000.000 ms...
Simulation completed in X seconds
Step 5 — Compute Oscillation Frequency
python check_output.py output

Example outputs:

The network is oscillating around 3.91 Hz.

or

The network is oscillating around 19.53 Hz.
🔬 Assignment Tasks

Apply a 0.2 nA current

Record oscillation frequency

Interpret emotional state (e.g., calm / low arousal)

Apply a 1.0 nA current

Record oscillation frequency

Interpret emotional state (e.g., high arousal / fear state)

💾 Output Files

Simulation results are stored in:

output/

Including:

spikes.h5

v_report.h5

log.txt

📲 Micro:bit Flashing (Optional)

To flash results to a micro:bit:

Install:

pip install uflash

Connect micro:bit via USB.

Run:

python check_output.py output

⚠️ If running on a remote system (e.g., FABRIC), transfer the output files to your local machine before flashing.

🗂 Project Structure
fear_simulation/
│
├── build_network.py
├── run_bionet.py
├── update_configs.py
├── check_output.py
├── parameters.py
├── network/
├── components/
└── output/



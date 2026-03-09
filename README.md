# Creating env and installing dependencies

1. Create project and environment
python3.12 -m venv .venv
source .venv/bin/activate

Deactivate --> source deactivate lub samo deactivate

Upgrade pip:
pip install --upgrade pip

Install pip-tools:
pip install pip-tools

2. Create requirements.in

This file contains only top-level packages.

pandas
scikit-learn
torch
xgboost

If you want to enforce Python version:

pandas
scikit-learn
torch
xgboost


3. Compile dependencies
Generate the fully resolved dependency file:

pip-compile requirements.in

This produces:
requirements.txt

Example (simplified):
numpy==2.0.1
pandas==2.2.2
scikit-learn==1.5.1
scipy==1.14.0
torch==2.3.1
xgboost==2.1.0
joblib==1.4.2
threadpoolctl==3.5.0
...

All codependencies are pinned automatically.

4. Install the locked environment
pip-sync requirements.txt

pip-sync guarantees the environment matches exactly the lock file.

5. Add new dependency later

Edit requirements.in:

pandas
scikit-learn
torch
xgboost
matplotlib

Then recompile:

pip-compile
pip-sync

6. Upgrade packages
Upgrade everything:

pip-compile --upgrade
pip-sync

Upgrade one package only:
pip-compile --upgrade-package pandas
pip-sync
# gym-longicontrol

This repository is a fork of the gym_longicontrol repository (https://github.com/dynamik1703/gym_longicontrol). The original repository contains a simulation environment for longitudinal car control with specified speed restrictions, along with code for training reinforcement learning models and evaluating their performance.

This fork includes updated code and files to ensure compatibility with Google Colaboratory. The updates focus on the main part of the repository: the training process and visualization, which now allow saving example results as mp4 videos. Additionally, the repository has been extended with a file containing car model data and a new pickle file.

To facilitate smooth operation on Google Colab, several modifications have been implemented. A new Jupyter notebook, **main.ipynb**, has been added. This notebook acts as a guide with pre-written commands to run model training and visualization, ensuring that the workflow operates correctly with the updated code and files. The notebook should be executed on Google Colab after uploading the entire repository to Google Drive.

If you use this repository for academic purposes, please cite the original authors as follows:

```
@conference{icaart21,
  author={Dohmen, Jan and Liessner, Roman and Friebel, Christoph and Bäker, Bernard},
  title={LongiControl: A Reinforcement Learning Environment for Longitudinal Vehicle Control},
  booktitle={Proceedings of the 13th International Conference on Agents and Artificial Intelligence - Volume 2: ICAART,},
  year={2021},
  pages={1030-1037},
  publisher={SciTePress},
  organization={INSTICC},
  doi={10.5220/0010305210301037},
  isbn={978-989-758-484-8},
}

```

## Usage
Instances of the environment can be created and handled similar to other Gym environments:
- `gym.make('gym_longicontrol:DeterministicTrack-v0')`
- `gym.make('gym_longicontrol:StochasticTrack-v0')`


## Example with built-in RL agent

### Training
We can train the model by run main.py and specify save_id argument (if we want to train new model) or load_id argument (if we want to continue train existing model).
```
cd gym-longicontrol/rl/pytorch
python main.py --save_id 9
```
```
cd gym-longicontrol/rl/pytorch
python main.py --load_id 9
```
If we want to save videos from steps of training we can pass -rec argument. We can specify parameters of ... by sending aditional arguments that are presented in gym-longicontrol/rl/pytorch/arguments.py.

A trained agent is given in `gym-longicontrol/rl/pytorch/out`:
- .tar ... model and weights
- .out ... quick overview of the training results
- .npy ... more detailed information about the course of training (can be used within the jupyter notebook `gym-longicontrol/rl/pytorch/monitor.ipynb`)


### Visualize
If we want to load the trained model and visualize an example track that will be saved as mp4 video we need to specify load_id and pass -vis and -rec arguments:
```
cd gym-longicontrol/rl/pytorch
python main.py --load_id 9 --env_id StochasticTrack-v0 -vis -rec
```

#### Examples
<details>
  <summary>Agent right after initialisation</summary>
  
  <p align="center">
  <img src="img/after_init.gif" width=600 height=270>
  </p>
</details>

<details>
  <summary>Early stage agent has learned to complete the track</summary>
  
  <p align="center">
  <img src="img/early_stage_agent.gif" width=600 height=270>
  </p>
</details>

<details open>
  <summary>Well trained agent</summary>
  
  <p align="center">
  <img src="img/trained_agent.gif" width=600 height=270>
  </p>
</details>



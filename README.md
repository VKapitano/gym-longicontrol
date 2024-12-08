# gym-longicontrol
This repository is a fork of the gym_longicontrol repository (https://github.com/dynamik1703/gym_longicontrol). That repository contains the simulation environment of longitudinal car control with given speed restrictions and the codes that train the model with the help of reinforcement learning and do the evaluation. This fork contains upadated codes and files so that can work properly on Google Colaboratory at the moment. Updates concerns the main part of the repository in which we train model and visualize the results on example by mp4 video. File with car model data were added to the repository and new pickle file is created. Training and visualization process is controled by main.ipynb.

In order for the codes to work correctly in the present time on Google Colab, several modifications have been made. A main.ipynb file has been added, which should be run on Google Colab after the entire repository is uploaded to Drive. This Python notebook serves as a guide with pre-written commands for model training and visualization, ensuring that the entire process works with the new modifications.

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



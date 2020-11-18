# social_navigation2_WAF
# Work in Progress
Repository of the paper published in WAF2020 (Wokshop de Agentes Fisicos):
## Defining Adaptive Proxemic Zones for Activity-aware Navigation:
## Abstract
 Many of the tasks that a service robot can perform at home involve navigation skills. In a real world scenario, the navigation system should consider individuals beyond just objects, theses days it is necessary to offer particular and dynamic representation in the scenario in order to enhance the HRI experience. In this paper, we use the proxemic theory to do this representation. The proxemic zones are not static. The culture or the context influences them and, if we have this influence into account, we can increase humans' comfort. Moreover, there are collaborative tasks in which these zones take different shapes to allow the task's best performance. This research develops a layer, the social layer, to represent and distribute the proxemics zones' information in a standard way, through a cost map and using it to perform a social navigate task. We have evaluated these components in a simulated scenario, performing different collaborative and human-robot interaction tasks and reducing the personal area invasion in a 32%. The material developed during this research can be found in a public repository, as well as instructions to facilitate the reproducibility of the results. 

## How to reproduce our research? 
### With an all-in-one LXD container.
- [Download the container image](https://urjc-my.sharepoint.com/:u:/g/personal/jonatan_gines_urjc_es/EbC5H1MRlLRHp0eV8n5wFdsBhNAkfsAhqvppP4dUdMe5ew?e=QBUvin)
- Import the image and launch the container, [link1](https://serverfault.com/a/796586), [link2 (Spanish)](https://superadmin.es/blog/devops/backup-contenedores-lxd/)
- [Create a set a LXD GUI Profile](https://blog.simos.info/how-to-easily-run-graphics-accelerated-gui-apps-in-lxd-containers-on-your-ubuntu-desktop/)

### Compiling the software.
#### 1. Install and configure ROS2 eloquent 
#### 2. Importing repos:
  ```bash
    cd [ros2_ws]/src
    wget https://raw.githubusercontent.com/IntelligentRoboticsLabs/social_navigation2_WAF/master/social_navigation2.repos
    vcs import < social_navigation2.repos
  ```
#### 3. Check the dependencies and compile.
  ```bash
    cd ..
    rosdep install -y -r -q --from-paths src --ignore-src --rosdistro eloquent
    colcon build --symlink-install
  ```
## Running the system.
```bash
  ros2 launch social_navigation_bringup demo_launch.py
```
Gazebo simulator and the RVIz2 window is open. It shows the proxemics of the agents and our robot. We can navigate using the RVIz tool Navigation2 Goal. Agent_1 is performing an escorting action and agent_2 is performing a following action.

## Testing different configurations.
File `social_navigation2/social_navigation_bringup/params/nav2_params.yaml` contains the navigation2 configuration. We can play with `var_h`,`var_s` and `var_r` action params and see how the proxemics change. It is neccesary restart the system launched in the previous step to see the results.

## Reproducing our experiments.
### Approaching
A robot has to get close to a human to interact.
```bash
  ros2 launch social_navigation_exp_bringup approach_exp_bringup.py.py
```
Gazebo simulator is running in background and RVIz2 is open. It shows an agent on the right side of the scene and the robot has to approach her/him.

### Escorting
A robot has to walk side-to-side with a human without disturbing and respecting his/her proxemic zone.
#### Escorting using proxemic zones of concentric circles
```bash
  ros2 launch social_navigation_exp_bringup escort_lu_exp_bringup.py
```
Gazebo simulator is running in background and RVIz2 is open. It shows an agent close to the robot and the agent's proxemic zone. The agent start to walk and the robot tries to walk side-to-side. Since the robot cannot walk on the right side of the person, it is placed behind them.
#### Escorting using our proposal
```bash
  ros2 launch social_navigation_exp_bringup escort_exp_bringup.py
```
Gazebo simulator is running in background and RVIz2 is open. It shows an agent close to the robot and the agent's proxemic zone. The proxemic zone include 2 cooperation zones. The agent start to walk and the robot tries to walk side-to-side. The robot walks on the agent's right while it can.

## Related links
- [Social_navigation2 (social_layer)](https://github.com/jginesclavero/social_navigation2)
- [social_navigation2_actions](https://github.com/jginesclavero/social_navigation2_actions)
- [social_navigation2_experiments](https://github.com/jginesclavero/social_navigation2_experiments)

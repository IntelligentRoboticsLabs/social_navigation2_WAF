# social_navigation2_WAF
# Work in Progress
Repository of the paper published in WAF2020 (Wokshop de Agentes Fisicos):
## Defining Adaptive Proxemic Zones for Activity-aware Navigation:
## Abstract:
 Many of the tasks that a service robot can perform at home involve navigation skills. In a real world scenario, the navigation system should consider individuals beyond just objects, theses days it is necessary to offer particular and dynamic representation in the scenario in order to enhance the HRI experience. In this paper, we use the proxemic theory to do this representation. The proxemic zones are not static. The culture or the context influences them and, if we have this influence into account, we can increase humans' comfort. Moreover, there are collaborative tasks in which these zones take different shapes to allow the task's best performance. This research develops a layer, the social layer, to represent and distribute the proxemics zones' information in a standard way, through a cost map and using it to perform a social navigate task. We have evaluated these components in a simulated scenario, performing different collaborative and human-robot interaction tasks and reducing the personal area invasion in a 32%. The material developed during this research can be found in a public repository, as well as instructions to facilitate the reproducibility of the results. 

## How to reproduce our research? 
### With an all-in-one LXD container.
- LXC containter steps.

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
#### 4. Running the system.
```bash
    ros2 launch social_navigation_bringup demo_launch.py
  ```
   - Gazebo simulator and the RVIz2 window is open. It shows the proxemics of the agents and our robot. We can navigate using the RVIz tool Navigation2 Goal. Agent_1 is performing an escorting action and agent_2 is performing a following action.

#### 5. Testing different configurations.
- File `social_navigation2/social_navigation_bringup/params/nav2_params.yaml` contains the navigation2 configuration. We can play with `var_h`,`var_s` and `var_r` action params and see how the proxemics change. It is neccesary restart the system launched in the previous step to see the results.

## Related links
- [Social_navigation2 (social_layer)](https://github.com/jginesclavero/social_navigation2)
- [social_navigation2_actions](https://github.com/jginesclavero/social_navigation2_actions)
- [social_navigation2_experiments](https://github.com/jginesclavero/social_navigation2_experiments)



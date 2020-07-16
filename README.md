# social_navigation2_WAF
# Work in Progress
Repository of the paper published in WAF2020 (Wokshop de Agentes Fisicos):
## Defining Adaptive Proxemic Zones for Activity-aware Navigation:
## Abstract:

## How to reproduce our research? 
### With an all-in-one LXD container.
- LXC containter steps.

### Compiling the software.
1. Install and configure ROS2 eloquent 
2. Importing repos:
  ```bash
    cd [ros2_ws]/src
    wget https://raw.githubusercontent.com/IntelligentRoboticsLabs/social_navigation2_WAF/master/social_navigation2.repos
    vcs import < social_navigation2.repos
  ```
3. Check the dependencies and compile.
  ```bash
    cd ..
    rosdep install -y -r -q --from-paths src --ignore-src --rosdistro eloquent
    colcon build --symlink-install
  ```
4. Launch steps.
5. Pasos para cambiar de forma sencilla y rápida algo del experimento.

## Related links
- [Social_navigation2 (social_layer)](https://github.com/jginesclavero/social_navigation2)
- [social_navigation2_actions](https://github.com/jginesclavero/social_navigation2_actions)
- [social_navigation2_experiments](https://github.com/jginesclavero/social_navigation2_experiments)



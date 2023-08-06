## ucsd_kitchens Dataset Description

The **ucsd_kitchens** dataset is a real-world dataset consisting of human-collected interactions in three distinct kitchen environments. Each kitchen scene contains five different tasks, and each task is further divided into ten demonstrations, resulting in a total of 150 demonstrations. The dataset offers a comprehensive set of real-world robotic interactions, involving natural language instructions and complex manipulations with kitchen objects.


### Dataset Details

- **Version:** 1.0.0
- **Release Notes:**
  - 1.0.0: Initial release.

- **Author:** Ge Yan, Kris Wu, and Xiaolong Wang
- **Title:** ucsd kitchens Dataset
- **Year:** 2023
- **Month:** August


### Features

The dataset consists of two main parts:

1. **Steps**: This part contains the primary data for each step of the robot's behavior in the kitchen. Each step is associated with the following information:

   - `observation`:
     - `image`: The RGB observation from the main camera, represented as an image with a shape of (480, 640, 3) and a PNG encoding format.
     - `state`: A 21-dimensional tensor representing the robot's joint states, including robot joint angles, joint velocity, and joint torque.

   - `action`: An 8-dimensional tensor representing the robot's action, which includes end-effector position and orientation, gripper open/close, and an episode termination action.

   - `discount`: A scalar value representing the discount for the given step, defaulting to 1 if not provided.

   - `reward`: A scalar value representing the reward for the given step. It is set to 1 for the final step in a demonstration.

   - `is_first`: A boolean scalar indicating whether it is the first step of the episode.

   - `is_last`: A boolean scalar indicating whether it is the last step of the episode.

   - `is_terminal`: A boolean scalar indicating whether the step is a terminal step in the episode. It is set to True for demos.

   - `language_instruction`: The language instruction provided to the robot at that step.

   - `language_embedding`: A 512-dimensional tensor representing the Kona language embedding computed using the Universal Sentence Encoder Large version 5 from TF-Hub.

2. **Episode Metadata**: This part contains metadata for each episode in the dataset. It includes:

   - `file_path`: The path to the original data file associated with the episode.

### Dataset Construction
For the collection of real robot demonstrations, we utilize the HTC VIVE controller and basestation to track the 6-DOF poses of human hand movements. We then use triad-openvr package to employ SteamVR and accurately map human operations onto the xArm robot, enabling it to interact with objects in the real kitchen.

The dataset is built using the `ucsd_kitchens` class, which extends the `GeneratorBasedBuilder` class from TensorFlow Datasets. The data is parsed and processed using a generator function `_generate_examples`, which loads raw data, assembles episodes, and computes language embeddings for each step. The episodes are then structured as dictionary samples, containing the steps and episode metadata.

### Usage

The **ucsd_kitchens** dataset, with its authentic real-world scenarios and accurately mapped human operations, provides an invaluable resource for researchers and developers in the field of robotics and artificial intelligence. The dataset enables the development and evaluation of robotic systems that can understand natural language instructions and seamlessly perform complex tasks in practical kitchen environments.

As a real-world dataset, it reflects the complexities and variabilities of actual kitchen scenarios, making it an ideal choice for training and testing robotic behavior in practical applications. Researchers can utilize this dataset to create advanced robot models capable of achieving a wide range of tasks in real-world settings.

### contact: g3yan@ucsd.edu

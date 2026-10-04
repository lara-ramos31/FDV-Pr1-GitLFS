# FDV-PR1: Git, Git LFS

*Fundamentos del Desarrollo de Videojuegos*' first assignment: setting up a Git (and LFS) repository for a Unity project.

![A GIF showing the Unity project's execution](Media/demo.gif)

## Proposed tasks
1. Create a Unity project that includes two 3D objects. Create a Git repository for the project. Add materials to both objects.
2. Create a Git LFS repository for the previous activity's Unity project. Configure the .gitattributes file. Include a large file (at least 100 MB) in a Media/ folder. Add a Script that prints "Script tarea 1.1" to the console. Add screenshots of the entire process.

## Part 1

A simple 3D scene was created in Unity, including a plane and a prism. Each object was assigned a custom material (gold for the prism, and green for the plane).

![A screenshot of the Unity editor showing the described scene](Media/scene.png)

A [GitHub repository](https://github.com/lara-ramos31/FDV-Pr1-GitLFS) was setup for the project. It includes only the [Assets/](Assets/), [Media/](Media/) and [Packages/](Packages/) folders. The [.gitignore](.gitignore) corresponds to the [standard GitHub template](https://github.com/github/gitignore/blob/main/Unity.gitignore) for Unity projects.

![A screenshot of the GitHub repository](Media/github_repo.png)
## Part 2

Git LFS was installed using `git lfs install`. Some typical file extensions were marked for Git LFS to track using `git lfs track *.png *.jpg *.mp4 *.mkv *.fbx *.gif`:

![A screenshot of the Git LFS setup process](Media/git_lfs_setup.png)

Aside from Git LFS' output, the [.gitattributes](.gitattributes) file was updated to add some lines taken from the class slides:

```
# Collapse Unity-generated files on GitHub 
*.asset linguist-generated 
*.mat linguist-generated 
*.meta linguist-generated 
*.prefab linguist-generated 
*.unity linguist-generated

*.png filter=lfs diff=lfs merge=lfs -text
*.jpg filter=lfs diff=lfs merge=lfs -text
*.mp4 filter=lfs diff=lfs merge=lfs -text
*.mkv filter=lfs diff=lfs merge=lfs -text
*.fbx filter=lfs diff=lfs merge=lfs -text
*.gif filter=lfs diff=lfs merge=lfs -text

*.md text
*.json linguist-generated=true
```

I opted to include a [public domain video](Media/steamboat_willie.mp4) 
(from the [Internet Archive](https://archive.org/details/steamboat-willie_1928)) as the large file for Git LFS to track and include in the repository. It was committed and pushed just like a normal file tracked by Git.

![A screenshot of the video file from inside the GitHub repository, showing the Git LFS mark](Media/git_lfs_file.png)

The script that prints `"Script tarea 1.1"` was assigned to the camera. The following code snippet corresponds to it:

```c#
using UnityEngine;
using System;

public class Script1_1 : MonoBehaviour
{
    // Start is called once before the first execution of Update after the MonoBehaviour is created
    void Start()
    {
        Debug.Log("Script tarea 1.1");
    }
}
```
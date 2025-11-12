

# Ex.No: 10 Mini Project

### 3D Maze Game using Unity

### Date: 21.10.2025

### AIM:

To design and develop a simple 3D Maze Game using Unity where the player navigates through a maze to find the exit using WASD controls and complete the maze.

***

### SOFTWARE REQUIREMENTS:

- Unity 2020.3 or later
- C\# Scripting using Visual Studio

***

### HARDWARE REQUIREMENTS:

- Windows / macOS system with minimum 8 GB RAM
- GPU recommended for smooth gameplay

***

### ALGORITHM:

1. Start a new 3D Unity project and create a plane as the maze base.
2. Add cube walls and design the maze layout.
3. Create a Player capsule and attach **PlayerController.cs** for movement.
4. Position the **Main Camera** and attach **CameraFollow.cs** to smoothly track the player.
5. Create a Goal object with a **WinTrigger.cs** script to detect when the player reaches it.
6. Add lights, textures, and build for testing.

***

### PROGRAM:
```
### Name: MOHAMED HAMEEM SAJITH J
### Reg No: 212223240090
```
#### 1. PlayerController.cs

```csharp
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float speed = 5f;

    void Update()
    {
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");

        Vector3 movement = new Vector3(moveHorizontal, 0.0f, moveVertical);
        transform.Translate(movement * speed * Time.deltaTime, Space.World);
    }
}
```


***

#### 2. CameraFollow.cs

```csharp
using UnityEngine;

public class CameraFollow : MonoBehaviour
{
    [SerializeField] Transform player;  // Assign player object in Inspector
    [SerializeField] float distance = 5f;
    [SerializeField] float height = 3f;
    [SerializeField] float smoothSpeed = 0.125f;

    void LateUpdate()
    {
        Vector3 desiredPosition = player.position - player.forward * distance + Vector3.up * height;
        Vector3 smoothedPosition = Vector3.Lerp(transform.position, desiredPosition, smoothSpeed);
        transform.position = smoothedPosition;
        transform.LookAt(player);
    }
}
```

*(This script makes the camera softly follow the player with a smooth transition)*.[^1][^2]

***

#### 3. WinTrigger.cs

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class WinTrigger : MonoBehaviour
{
    public GameObject player;

    private void OnTriggerEnter(Collider other)
    {
        if (other.gameObject == player)
        {
            Debug.Log("Maze Completed!");
            // You can load a success screen or restart
            SceneManager.LoadScene(SceneManager.GetActiveScene().name);
        }
    }
}
```

*(Attach this to the “Goal” object with a collider marked as **Trigger**)*.[^3][^4]

***

### OUTPUT:

The scene displays a 3D maze environment viewed from a third-person camera.
The player uses **W, A, S, D** to move smoothly through the maze while the camera tracks them.
When the player collides with the Goal object, a victory message appears, and the level resets.

<img width="1919" height="1079" alt="image" src="https://github.com/user-attachments/assets/35c78ccc-b285-49b9-96e7-c54cca6d4c44" />
<img width="1915" height="1079" alt="image" src="https://github.com/user-attachments/assets/ac51d61b-123e-46bc-a43c-d9cdff08c400" />


***

### RESULT:

Hence a functional 3D Maze Game was successfully created using Unity and C\# with player movement, camera tracking, and game-end trigger events.



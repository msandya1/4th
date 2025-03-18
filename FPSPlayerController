using UnityEngine;

public class FPSPlayerController : MonoBehaviour
{
    public float speed = 5f; // Movement speed
    public float rotationSpeed = 100f; // Rotation speed
    public float jumpHeight = 2f; // Jump height
    public float gravity = -9.81f; // Gravity force

    private CharacterController controller;
    private Vector3 velocity;
    private bool isGrounded;
    
    void Start()
    {
        controller = GetComponent<CharacterController>(); // Get the Character Controller
    }

    void Update()
    {
        // Check if the player is on the ground
        isGrounded = controller.isGrounded;
        if (isGrounded && velocity.y < 0)
        {
            velocity.y = -2f; // Reset velocity when grounded
        }

        // Get movement input (Forward/Backward & Left/Right)
        float moveZ = Input.GetAxis("Vertical");  // W & S for forward/backward
        float moveX = Input.GetAxis("Horizontal"); // A & D for left/right

        // Move the player based on input
        Vector3 move = transform.forward * moveZ + transform.right * moveX;
        controller.Move(move * speed * Time.deltaTime);

        // Rotate Left/Right using Mouse X
        float rotation = Input.GetAxis("Mouse X") * rotationSpeed * Time.deltaTime;
        transform.Rotate(0, rotation, 0);

        // Jumping logic
        if (Input.GetButtonDown("Jump") && isGrounded)
        {
            velocity.y = Mathf.Sqrt(jumpHeight * -2f * gravity);
        }

        // Apply gravity
        velocity.y += gravity * Time.deltaTime;
        controller.Move(velocity * Time.deltaTime);
    }
}

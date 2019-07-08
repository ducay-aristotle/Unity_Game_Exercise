## Unity_Game_Exercise
An attempt at recreating the mechanics and level 1-1 of Super Mario Bros.(SNES) at the basic level.

## Project Description(Detailed)
  This Project was made as a three man group with Aristotle Ducay as the lead for the group and gameplay engineering. The goal of the project aims to recreate world 1-1 of Super Mario Bros to gain fundametal knowledge of pipeline workflow, level design, software development and Asset manipulation from within the Unity Engine.   
	
## Skills aquired/learned
- Proper usage of Private and Public variables,
- Proper usage of Private/public int and float variables
- Code consistancy and readability
- Construction of UI elements within C#
- Construction of player movement within C#
- Making Asset prefabs within the Unity editor
- Using Unity's 2D sprite editor and tielmaps to construct world 1-1
- Constructing events such as level finish, player death, player respawn etc...
- Creating functions to use in combination with one another.
	
## Code Snippets	
Source code for player movement in C#:

	using System.Collections;
	using System.Collections.Generic;
	using UnityEngine;
	using UnityEngine.UI;
	using UnityEngine.SceneManagement;

	public class Mario: MonoBehaviour
	{
    [SerializeField]
    public bool isDeath = false;
    public bool isCoin = false;
    public bool isJumping = false;

    Rigidbody2D rb;
    
    public Vector2 velocity;
    public Vector2 originalPos;
    private Vector2 playerpos;

    public float jumpHeight;
    private float Score;
    private float timeLeft = 375f;

    private int Lives;
    private int Coins;
    private float coinMax = 50f;
    public int World;
    public int Level;

    public Text livesText;
    public Text ScoreText;
    public Text CoinsText;
    public Text WorldText;
    public Text TimeText;

    
    // Use this for initialization
    void Start ()
    {
        Debug.Log("Debug here");
        rb = GetComponent<Rigidbody2D>();
        Lives = 3;
        UI();

        
    }
	
	// Update is called once per frame
	void Update ()
    {
        //Ticks down the level timer each second
        LevelTimer();

        
        var moveRight = Input.GetKey(KeyCode.D);
        var moveLeft = Input.GetKey(KeyCode.A);
        var Jumping = Input.GetKey(KeyCode.Space);
        var moveR = Input.GetAxis("Right");
        var moveL = Input.GetAxis("Left");
        var poseR = velocity.x;
        var poseL = velocity.x;
	}
Source Code for player jump in C#:

    void Start()
    {
        //sets the jumpCounter to whatever the jumpTime is set to in the editor
        jumpTimeCounter = jumpTime;
    }

    void Awake()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    void Update()
    {


            //when the player is falling adjust gravity of object
            if (rb.velocity.y < 0)
            {
                rb.velocity += Vector2.up * Physics2D.gravity.y * (fallAcceleration - 1) * Time.deltaTime;

            }

            if (rb.velocity.y > 0 && !Input.GetKey(KeyCode.Space))
            {
                rb.velocity += Vector2.up * Physics2D.gravity.y * (fallAcceleration - 1) * Time.deltaTime;
            }

            

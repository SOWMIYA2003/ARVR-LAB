# ARVR-LAB
### RotateObjects
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Program : MonoBehaviour
{
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        transform.RotateAround(Vector3.up, Vector3.left, 40 * Time.deltaTime);
    }
}
```
![al1](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/bff55c40-899b-4a4c-ad7f-e5f3513c13ca)
![al2](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/2f785842-c330-499f-bea8-da6aabd3d1fb)
### RollaBall
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NewBehaviourScript : MonoBehaviour
{
    public float xforce = 5.0f;
    public float yforce = 20.0f;
    public float zforce = 5.0f;
    // Start is called before the first frame update
    void Start()
    {
        
    }

    // Update is called once per frame
    void Update()
    {
        float x = 0.0f;
        float y = 0.0f;
        float z = 0.0f;
        if(Input.GetKey(KeyCode.A))
        {
            x = x - xforce;
        }
        if (Input.GetKey(KeyCode.D))
        {
            x = x + xforce;
        }
        if (Input.GetKey(KeyCode.W))
        {
            z = z + zforce;
        }
        if (Input.GetKey(KeyCode.S))
        {
            z = z - zforce;
        }
        if (Input.GetKeyDown(KeyCode.Space))
        {
            y =yforce;
        }
        GetComponent<Rigidbody>().AddForce(x, y, z);
    }
}
```
![al3](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/2449e29b-19f0-42ba-8d57-13ee8a6ab771)
![al4](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/5c1a51bc-8eb5-4855-92cf-f89086457bf4)
### PIngPong
![al5](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/3e734460-6fab-4aa6-846c-8481032965c7)
![al6](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/ee6a0e10-d54f-4bbf-8d49-2f54b98e30e4)
### Animator
```
DEVELOPED BY : SOWMIYA N
REGISTER NO : 212221230106

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class IdletoCrouch : MonoBehaviour
{
    public Animator animator;
    public float InputX;
    public float InputY;
    
    void Start()
    {
        animator = this.gameObject.GetComponent<Animator>();
    }


    void Update()
    {
        InputX = Input.GetAxis("Vertical");
        InputY = Input.GetAxis("Horizontal");
        animator.SetFloat("InputX", InputX);
        animator.SetFloat("InputY", InputY);
    }
}
```
![aq1](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/d2a65889-a998-4a8e-8de0-ab7df1f1d556)
![aq2](https://github.com/SOWMIYA2003/ARVR-LAB/assets/93427443/a1f449ca-6105-4f89-9c9e-1230cb7cc4fe)

### RedirectingaScene
```
Developed By : Sowmiya N
Register No : 212221230106

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class Prog : MonoBehaviour
{
    Rigidbody rb;
    public GameObject WinText;
 
    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

 
    void Update()
    {
        if (Input.GetKeyDown(KeyCode.R))
        {
            SceneManager.LoadScene("Level2");
        }
    }
    public void OnMouseDown()
    {
        Destroy(gameObject);
    }
    private void OnCollisionEnter(Collision collision)
    {
        if (collision.gameObject.tag == "cube")
        {
            Destroy(collision.gameObject);
            WinText.SetActive(true);
        }
    }
}

```
### PingPong
### GameManager
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GameManager : MonoBehaviour
{
   public Ball ball;
   public Paddle paddle;
   public static Vector2 bottomLeft;  
   public static Vector2 topRight; 
   void Start()
   {
       bottomLeft = Camera.main.ScreenToWorldPoint(new Vector2(0, 0));
       topRight = Camera.main.ScreenToWorldPoint(new Vector2(Screen.width, Screen.height));

       Instantiate(ball);
       Paddle paddle1 = Instantiate(paddle) as Paddle;
       Paddle paddle2 = Instantiate(paddle) as Paddle;
       paddle1.Init(true); 
       paddle2.Init(false); 
   }

   // Update is called once per frame
   void Update()
   {
       
   }
}
```
### Ball
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Ball : MonoBehaviour
{
  [SerializeField]
   float speed;
   float radius;
   Vector2 direction;

   // Start is called before the first frame update
   void Start()
   {
       direction = Vector2.one.normalized;
       radius = transform.localScale.x / 2; // takes diameter of the ball
   }

   // Update is called once per frame
   void Update()
   {
       transform.Translate(direction * speed * Time.deltaTime);
       
       if(transform.position.y<GameManager.bottomLeft.y+radius && direction.y<0)
       {
           direction.y = -direction.y;
       }
       if (transform.position.y > GameManager.topRight.y - radius && direction.y > 0)
       {
           direction.y = -direction.y;
       }
       
       if (transform.position.x < GameManager.bottomLeft.x + radius && direction.x < 0)
       {
           Debug.Log("Right Player Wins");
           Time.timeScale = 0;
       }
       if (transform.position.x > GameManager.topRight.x - radius && direction.x > 0)
       {
           Debug.Log("Left Player Wins");
           Time.timeScale = 0;
       }

   }
   void OnTriggerEnter2D(Collider2D other)
   {
       if(other.tag=="Paddle")
       {
           bool isRight = other.GetComponent<Paddle>().isRight;
           if(isRight==true && direction.x>0)
           {
               direction.x = -direction.x;
           }
           if (isRight == false && direction.x <0)
           {
               direction.x = -direction.x;
           }
       }
   }
}

```
### Paddle
```
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Paddle : MonoBehaviour
{
   [SerializeField]
    float speed;
    float height;
    string input;
    public bool isRight;
    // Start is called before the first frame update
    void Start() 
    {
        height = transform.localScale.y;
        speed = 6f;
    }
    public void Init(bool isRightPaddle)
    {
        isRight = isRightPaddle;
        Vector2 pos = Vector2.zero;
        if(isRightPaddle)
        {
            pos = new Vector2(GameManager.topRight.x, 0); 
            pos -= Vector2.right * transform.localScale.x;
            input = "PaddleRight";
        }
        else
        {
            pos = new Vector2(GameManager.bottomLeft.x, 0); 
            pos += Vector2.right * transform.localScale.x;
            input = "PaddleLeft";
        }
        transform.position = pos;
        transform.name = input;
    }
    // Update is called once per frame
    void Update() 
    {
        float move = Input.GetAxis(input) * Time.deltaTime * speed;
        if(transform.position.y<GameManager.bottomLeft.y+height/2 && move<0) 
        {
            move = 0;
        }
        if(transform.position.y>GameManager.topRight.y-height/2 && move>0)
        {
            move = 0;
        }
        transform.Translate(move * Vector2.up);
    }
}

```

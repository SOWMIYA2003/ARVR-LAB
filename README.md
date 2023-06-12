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
    // Start is called before the first frame update
    void Start()
    {
        animator = this.gameObject.GetComponent<Animator>();
    }

    // Update is called once per frame
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
    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    // Update is called once per frame
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

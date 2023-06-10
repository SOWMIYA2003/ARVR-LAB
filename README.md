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

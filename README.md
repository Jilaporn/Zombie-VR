# Zombie-VR
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.AI;

public class scr : MonoBehaviour
{
    private Animator animspider;
    private CharacterController controller;
    public float speed = 1.0f;
    public Rigidbody rb;
    private Vector3 moveDirect = Vector3.zero;
    public float gogo;
    
    // Start is called before the first frame update

    private void Awake()
    {
        animspider = GetComponent<Animator>();
    }
    void Start()
    {
        rb = GetComponent<Rigidbody>();
        controller = GetComponent<CharacterController>();
    }

    // Update is called once per frame
    void Update()
    {
        rb.AddForce(new Vector3(50f, 0f, 0f));
        // float h = Input.GetAxisRaw("Horizontal");

        if (Input.GetKey("up"))
        {
            animspider.SetInteger("anis", 1);
        }
        else
        {
            animspider.SetInteger("anis", 0);
        }
        if(controller.isGrounded)
            { moveDirect = transform.forward * Input.GetAxis("vertical") * speed;
        }
       float turn = Input.GetAxis("Horizontal");
        controller.Move(moveDirect * Time.deltaTime);
        
    }

}

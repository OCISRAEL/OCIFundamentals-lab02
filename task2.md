<h2><ins>TASK 2 – Enabling OKE Cluster Autoscaler</ins></h2>

1. Choose your cluster

2. Under **Resources**, Go to **Node Pools** & Choose Your **Pool**

3. Copy the **Node Pool OCID** for later reference

    ![drawing](./img/nodepoolocid.png)

4. Under **Cluster Details**, Go to **Resources** ->  **Adds-ons** in the left panel menu

5. Click on Manage Add-On

    ![drawing](./img/addon.png)

6. Choose **Cluser Autoscaler** from the Adds-ons list

7. Tik the '**Enable Cluster Autoscaler**' box

8.	Choose **Automatic Updates**

9.	Follow the insructions and pay attention to the format. min=1, max=3 (single nodepool. OCID value from step 3)
    ![drawing](./img/autoscaler.png) & 
    
    **Save Changes**

10.	Accept and close the window

11.	Access your **Cluster** again via cloudshell

12.	Run the command: 
        
        kubectl get pods -n kube-system

13.	Validate cluster autoscaler pod in **Running** state
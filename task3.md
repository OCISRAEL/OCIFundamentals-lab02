<h2><ins>TASK 3 – Showcase Autoscaler Functionality </ins></h2>

1. Setting Up an Instance Principal  to Enable the Cluster Autoscaler Add-ons to access to **Node Pools** Require using Dynamic Group 

    1. Navigate to Identity -> Policies

    2. Create a new policy and name it: autoscaler-policy (in your compartment)

    3. Paste the following statements:

            Allow dynamic-group <dynamic-group-name> to manage cluster-node-pools in compartment <YOUR_COMPARTMENT_NAME>
            Allow dynamic-group <dynamic-group-name> to manage instance-family in compartment <YOUR_COMPARTMENT_NAME>
            Allow dynamic-group <dynamic-group-name> to use subnets in compartment <YOUR_COMPARTMENT_NAME>
            Allow dynamic-group <dynamic-group-name> to read virtual-network-family in compartment <YOUR_COMPARTMENT_NAME>
            Allow dynamic-group <dynamic-group-name> to use vnics in compartment <YOUR_COMPARTMENT_NAME>
            Allow dynamic-group <dynamic-group-name> to inspect compartments in compartment <YOUR_COMPARTMENT_NAME>
    
        **Important:** Use the same Dynamic Group & Compartment names (Case Sensetive) that have been created in Day 1 !!

    4. Save Changes

2. Access your **Cluster** via Cloud Shell

3. Run the following command to create multiple replicas of the nginx deployment:

        kubectl scale --replicas=30 deployment/oci-fund-nginx

4. Navigate to  your **Node Pool** and select the **Nodes** tab .Wait and observe how the node pool updates in the console

    ![drawing](./img/nodepoolcreation.png)

5. Move back to **Cloud Shell**

6. Verify new **Nodes** are under creation: 

        kubectl get nodes

7.  Verify all podes are in **Running** State: 
        
        kubectl get pods

Congratulations! You have created a Kubernetes Autoscaler capable of handling high traffic load for your application.

8. Surf to your app with the external IP Address: 

        http://<EXTERNAL_IP_ADDRESS>

9. Scale down your application to a single **Pod**:

        kubectl scale --replicas=1 deployment/oci-fund-nginx

10. Check that only a single pod is running:
        
        kubectl get pods

11. Wait and observe how the **Nodes** are scaled to minimum (default notion '--scale-down-unneeded-time' is 10m), run:

        kubectl get nodes

<br>

<h3>CONGRATULATIONS!! YOU HAVE COMPLETED THE OKE LAB!</h3>
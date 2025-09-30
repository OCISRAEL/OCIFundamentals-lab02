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
    
        **Important:** Use the same Dynamic Group & Compartment names that have been created in Day 1 !!

    4. Save Changes

2. Access your **Cluster** via cloudshell

3. Run the following command to create multiple replicas of the nginx deployment:

        kubectl scale --replicas=30 deployment/oci-fund-nginx

4. Navigate to **Node Pools** & Choose Your **Pool**.Wait and observe how the node pool updates in the console

    ![drawing](./img/nodepoolcreation.png)

5. Verify new **Nodes** are under creation: 

        kubectl get nodes

6.  Verify all podes are in **Running** State: 
        
        kubectl get pods

7. Surf to your app with the external IP Address: 

        http://<EXTERNAL_IP_ADDRESS>

8. Scale down your application to a single **Pod**:

        kubectl scale --replicas=1 deployment/oci-fund-nginx

9. Wait few seconds. To verify **Nodes** are scaled to minimum, run:

        kubectl get nodes

<br>

<h3>CONGRATULATIONS!! YOU HAVE COMPLETED THE OKE LAB!</h3>
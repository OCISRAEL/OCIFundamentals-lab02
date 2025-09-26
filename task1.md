<h2><ins> TASK 1 - Create Your first OKE Cluster </ins></h2>


1. Verify you are in **Israel Central** Region


2. Create a Cluster (**Quick create**)

   1. Open the navigation menu and click **Developer Services**. Under **Containers & Artifacts**, click **OKE** and **Create Cluster**

   2. Choose **Quick Create** and **Proceed**

      ![drawing](./img/cluster_creation.png)

    -	**Name**: OKE-lab
    -	**Compartment**: demo
    -	**Kubernetes** version: v1.33 ( or latest available)
    -	**Kubernetes API Endpoint Subnet**: Public Endpoint
    -   **Node Type**: Managed
    -	**Kubernetes Worker Nodes**: Private Workers
    -	**Shape**: VM.Standard.E4.Flex (2 OCPUs, 8GB Memory)
    -	**Image**: Oracle Linux 8.10 with K8S version 1.33.1
    -	**Number of nodes**: 1 <br>

    Click **Next**
    
    3. Review and Click **Create cluster**.

3. Proceed with **Enhanced Cluster Features** and click **Continue**

4. Once the cluster creation is initiated, you can **Close** the creation window

5. Wait for the cluster status to change to **Active**

6. Go to **Quick start:Deploy sample app** tab. Click on “**Access Cluster**”

      ![drawing](./img/access_cluster.png)

7. Follow this steps:
    1. Choose **Cloud Shell Access**

    2. Copy the **Access command** to your clipboard

    3. Lunch **Cloud Shell**

    ![drawing](./img/cloud_shell_access.png)

8.	Paste the command in the CLI screen that will grant you the access to your cluster

9. Clone the code repository

    Clone the code into your device by running the following command:

        git clone https://github.com/OCISRAEL/OCIFundamentals-lab02.git

    Then, run the following command:

        cd OCIFundamentals-lab02/


10.	Deploy the **NGINX** application 

    To deploy the web application and its service type LoadBalancer (which will expose the application to the public), run the following command:

        kubectl apply -f nginx.yaml

11.	Validate the application is is **Running** state

        kubectl get pods
    
    Did the status changed to **Running**?

<br>

12.	**Get the Service Public IP Address**

    Run the following command in order to get the Service Public IP Address:

        kubectl get service oci-fund-nginx

    ![drawing](./img/oci_fund_nginx.png)
 
13. Copy the IP Address and paste it in the browser (http://<IP-ADDRESS\>)

    ![drawing](./img/welcome_to_nginx.png)
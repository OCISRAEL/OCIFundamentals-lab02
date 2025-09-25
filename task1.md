<h2><ins> TASK 1 - Create Your first OKE Cluster </ins></h2>


1. Create a Cluster (**Quick create**)

   1. Open the navigation menu and click **Developer Services**. Under **Containers & Artifacts**, click **OKE** and **Create Cluster**

      ![drawing](./img/cluster_creation.png)

    -	**Name**: OKE-lab
    -	**Compartment**: demo
    -	**Kubernetes** version: v1.33 ( orl latest available)
    -	**Kubernetes API Endpoint Subnet**: Public Endpoint
    -   **Node Type**: Managed
    -	**Kubernetes Worker Nodes**: Private Workers
    -	**Shape**: VM.Standard.E4.Flex (2 OCPUs, 8GB Memory)
    -	**Image**: Default Value
    -	**Number of nodes**: 1
    Click **Next**
    
    2. Review and Click **Create cluster**.


2. Go to the Cluster page, click on “**Access Cluster**”

      ![drawing](./img/access_cluster.png)



3.	Wait for Creation & Launch “**Cloud Shell**” and paste the command grant you the access to your cluster.



4. **Clone the code repository**

    Clone the code into your device by running the following command:

        git clone https://github.com/OCISRAEL/OCIFundamentals-lab02.git

    Then, run the following command:

        cd OCIFundamentals-lab02/


5.	**Deploy the Application (NGINX) & Service type LoadBalancer**

    To deploy the web application and its service type LoadBalancer (which will expose the application to the public), run the following command:

        kubectl apply -f nginx.yaml


6.	**Validate the application is running**

    Validate the application is running by running the following command:

        kubectl get pods
    
    Did the status changed to **Running**?

<br>

7.	**Get the Service Public IP Address**

    Run the following command in order to get the Service Public IP Address:

        kubectl get service oci-fund-nginx

    ![drawing](./img/oci_fund_nginx.png)
 
8. Copy the IP Address and paste it in the browser (http://<IP-ADDRESS\>)

    ![drawing](./img/welcome_to_nginx.png)
# OKE Workshop


<ins>**Lab 2 – OKE – NGINX Web Application** </ins>

- **Pre-requisites (for this lab):**

    * Make sure port 80 is open for ingress traffic to your public subnet


1. Create an OKE Cluster (**Custom create**)

   1. First, make sure you're using the right region - Israel Central (Jerusalem)

      ![drawing](./img/cluster_creation.png)

    -	**Name**: Choose your cluster name
    -	**Kubernetes** version: v1.25.4
    -	**Kubernetes API Endpoint Subnet**: Choose **"Public Endpoint"**
    -	**Kubernetes Worker Nodes**: Choose **"Private Workers"**
    -	**Shape**: VM.Standard.E3.Flex (2 OCPUs, 8GB Memory)
    -	**Image**: Oracle Linux 8
    -	**Number of nodes**: 1
    Click **Next** and **"Create"**.


2. Go to the Cluster page, click on “**Access Cluster**”

      ![drawing](./img/access_cluster.png)



3.	Launch “**Cloud Shell**” and paste the command grant you the access to your cluster.



4. **Clone the code repository**

    Clone the code into your device by running the following command:

        git clone https://github.com/OCI-IL/OCIFundamentals-lab-02.git

    Then, run the following command:

        cd OCIFundamentals-lab-02/


5.	**Deploy the Application (NGINX) & Service type LoadBalancer**

    To deploy the web application and its service type LoadBalancer (which will expose the application to the public), run the following command:

        kubectl apply -f nginx.yaml


6.	**Validate the application is running**

    Validate the application is running by running the following command:

        kubectl get pods


7.	**Get the Service Public IP Address**

    Run the following command in order to get the Service Public IP Address:

        kubectl get service oci-fund-nginx

    ![drawing](./img/oci_fund_nginx.png)
 
    Copy the IP Address and paste it in the browser (http://<IP-ADDRESS\>)

    ![drawing](./img/welcome_to_nginx.png)



***Bonus***

1.	**Deploy OKE Cluster Autoscaler**
    Deploy the OKE Cluster Autoscaler by using the following documentation:
    
    https://docs.oracle.com/en-us/iaas/Content/ContEng/Tasks/contengusingclusterautoscaler.htm#Working_with_the_Cluster_Autoscaler

	Follow the instructions and validate that the number of nodes increased on the cluster.
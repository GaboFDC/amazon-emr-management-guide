# View web interfaces hosted on Amazon EMR clusters<a name="emr-web-interfaces"></a>

**Important**  
It is possible to configure a custom security group to allow inbound access to these web interfaces\. Keep in mind that any port on which you allow inbound traffic represents a potential security vulnerability\. Carefully review custom security groups to ensure that you minimize vulnerabilities\. For more information, see [Control network traffic with security groups](emr-security-groups.md)\.

Hadoop and other applications you install on your Amazon EMR cluster, publish user interfaces as web sites hosted on the master node\. For security reasons, when using EMR\-Managed Security Groups, these web sites are only available on the master node's local web server, so you need to connect to the master node to view them\. For more information, see [Connect to the master node using SSH](emr-connect-master-node-ssh.md)\. Hadoop also publishes user interfaces as web sites hosted on the core and task nodes\. These web sites are also only available on local web servers on the nodes\. 

The following table lists web interfaces that you can view on cluster instances\. These Hadoop interfaces are available on all clusters\. For the master instance interfaces, replace *master\-public\-dns\-name* with the **Master public DNS** listed on the cluster **Summary** tab in the EMR console\. For core and task instance interfaces, replace *coretask\-public\-dns\-name* with the **Public DNS name** listed for the instance\. To find an instance's **Public DNS name**, in the EMR console, choose your cluster from the list, choose the **Hardware** tab, choose the **ID** of the instance group that contains the instance you want to connect to, and then note the **Public DNS name** listed for the instance\.


|  Name of interface |   URI  | 
| --- | --- | 
| Flink history server \(EMR version 5\.33 and later\) | http://master\-public\-dns\-name:8082/ | 
| Ganglia | http://master\-public\-dns\-name/ganglia/ | 
| Hadoop HDFS NameNode \(EMR version pre\-6\.x\) | https://master\-public\-dns\-name:50470/ | 
| Hadoop HDFS NameNode | http://master\-public\-dns\-name:50070/ | 
| Hadoop HDFS DataNode | http://coretask\-public\-dns\-name:50075/ | 
| Hadoop HDFS NameNode \(EMR version 6\.x\) | https://master\-public\-dns\-name:9871/ | 
| Hadoop HDFS DataNode \(EMR version pre\-6\.x\) | https://coretask\-public\-dns\-name:50475/ | 
| Hadoop HDFS DataNode \(EMR version 6\.x\) | https://coretask\-public\-dns\-name:9865/ | 
| HBase | http://master\-public\-dns\-name:16010/ | 
| Hue | http://master\-public\-dns\-name:8888/ | 
| JupyterHub | https://master\-public\-dns\-name:9443/ | 
| Livy | http://master\-public\-dns\-name:8998/ | 
| Spark HistoryServer | http://master\-public\-dns\-name:18080/ | 
| Tez | http://master\-public\-dns\-name:8080/tez\-ui | 
| YARN NodeManager | http://coretask\-public\-dns\-name:8042/ | 
| YARN ResourceManager | http://master\-public\-dns\-name:8088/ | 
| Zeppelin | http://master\-public\-dns\-name:8890/ | 

Because there are several application\-specific interfaces available on the master node that are not available on the core and task nodes, the instructions in this document are specific to the Amazon EMR master node\. Accessing the web interfaces on the core and task nodes can be done in the same manner as you would access the web interfaces on the master node\. 

There are several ways you can access the web interfaces on the master node\. The easiest and quickest method is to use SSH to connect to the master node and use the text\-based browser, Lynx, to view the web sites in your SSH client\. However, Lynx is a text\-based browser with a limited user interface that cannot display graphics\. The following example shows how to open the Hadoop ResourceManager interface using Lynx \(Lynx URLs are also provided when you log into the master node using SSH\)\. 

```
lynx http://ip-###-##-##-###.us-west-2.compute.internal:8088/
```

There are two remaining options for accessing web interfaces on the master node that provide full browser functionality\. Choose one of the following: 
+ Option 1 \(recommended for more technical users\): Use an SSH client to connect to the master node, configure SSH tunneling with local port forwarding, and use an Internet browser to open web interfaces hosted on the master node\. This method allows you to configure web interface access without using a SOCKS proxy\.
+ Option 2 \(recommended for new users\): Use an SSH client to connect to the master node, configure SSH tunneling with dynamic port forwarding, and configure your Internet browser to use an add\-on such as FoxyProxy for Firefox or SwitchyOmega for Chrome to manage your SOCKS proxy settings\. This method lets you automatically filter URLs based on text patterns and limit the proxy settings to domains that match the form of the master node's DNS name\. For more information about how to configure FoxyProxy for Firefox and Google Chrome, see [Option 2, part 2: Configure proxy settings to view websites hosted on the master node](emr-connect-master-node-proxy.md)\.

With Amazon EMR version 5\.25\.0 or later, you can access Spark history server UI from the console without setting up a web proxy through an SSH connection\. For more information, see [One\-click access to persistent Spark history server](https://docs.aws.amazon.com/emr/latest/ManagementGuide/app-history-spark-UI.html)\.

**Topics**
+ [Option 1: Set up an SSH tunnel to the master node using local port forwarding](emr-ssh-tunnel-local.md)
+ [Option 2, part 1: Set up an SSH tunnel to the master node using dynamic port forwarding](emr-ssh-tunnel.md)
+ [Option 2, part 2: Configure proxy settings to view websites hosted on the master node](emr-connect-master-node-proxy.md)
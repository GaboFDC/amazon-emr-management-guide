# Troubleshoot a cluster<a name="emr-troubleshoot"></a>

 A cluster hosted by Amazon EMR runs in a complex ecosystem made up of several types of open\-source software, custom application code, and Amazon Web Services\. An issue in any of these parts can cause the cluster to fail or take longer than expected to complete\. The following topics will help you figure out what has gone wrong in your cluster and give you suggestions on how to fix it\. 

**Topics**
+ [What tools are available for troubleshooting?](emr-troubleshoot-tools.md)
+ [Viewing and restarting Amazon EMR and application processes \(daemons\)](emr-process-restart-stop-view.md)
+ [Troubleshoot a failed cluster](emr-troubleshoot-failed.md)
+ [Troubleshoot a slow cluster](emr-troubleshoot-slow.md)
+ [Common errors in Amazon EMR](emr-troubleshoot-errors.md)
+ [Troubleshoot a Lake Formation cluster](emr-troubleshoot-lf.md)

 When you are developing a new Hadoop application, we recommend that you enable debugging and process a small but representative subset of your data to test the application\. You may also want to run the application step\-by\-step to test each step separately\. For more information, see [Configure cluster logging and debugging](emr-plan-debugging.md) and [Step 5: Test the cluster step by step](emr-troubleshoot-failed-5-test-steps.md)\. 
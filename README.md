# DFS-Namespace On Azure Files
DFS Namespaces is a role service in Windows Server that enables you to group shares located on different servers into one or more logically structured namespaces. This makes it possible to give users a virtual view of shared folders, where a single path leads to files located on multiple servers. This article will go over some steps to setup DFS-N on Azure Files. 

You will need DFS-N on Azure Files directly if:

  1. You do not have an Azure File Sync as Azure Files is sufficient for your use case.
  2. A unified namespace across all disparate shares is needed.
  3. A larger share size all under same name is required. 
  4. A particular share name wants to be retained.

Azure Files is a fully manages SMB file share in Azure which can be leveraged for your convinient lift-and-shift of file servers. Data in Azure Files can be accessed in many different ways with the following two being dominant:
  1. **Direct SMB access to Azure Files** by mounting Azure Files Share directly either from on-premises or within Azure
  2. Continue to access the local file server by configuring **Azure Files Sync** which provides you a way to turn on-premises Windows Server into a fast disposable cache of most frequently accessed data with data tiering setup into Azure Files. If you have Azure File Sync configured, DFS-N with **Azure File Sync needs no changes** and you will **not need these instructions**. Your DFS-N will continue to work as is.

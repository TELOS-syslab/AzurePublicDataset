# Overview 概览

This repository contains public releases of Microsoft Azure traces for the benefit of the research and academic community.
此存储库包含 Microsoft Azure 的公开跟踪数据，旨在为研究和学术界提供帮助。

There are currently two classes of traces: 
目前有两类跟踪数据：

* VM Traces: two representative traces of the virtual machine (VM) workload of Microsoft Azure collected in 2017 and 2019, and one VM request trace specifically for investigating packing algorihtms.
VM 跟踪：包括 Microsoft Azure 在 2017 年和 2019 年收集的两个典型虚拟机（VM）工作负载跟踪，以及一个用于研究打包算法的 VM 请求跟踪数据。

* Azure Functions Traces: representative traces of Azure Functions invocations, collected over two weeks in 2019, and of Azure Functions blob accesses, collected between November and December of 2020.
Azure Functions 跟踪：包括 2019 年两周期间收集的 Azure Functions 调用的典型跟踪，以及 2020 年 11 月至 12 月收集的 Azure Functions blob 访问数据。

* Azure LLM Inference Traces: representative traces of LLM inference invocations with input and output tokens, collected on November 2023.
Azure LLM 推理跟踪：包括 2023 年 11 月收集的大型语言模型（LLM）推理调用的典型跟踪数据，包含输入和输出 token。

We provide the traces as they are, but are willing to help researchers understand and use them. So, please let us know of any issues or questions by sending email to our  [mailing list](mailto:azurepublicdataset@service.microsoft.com).
我们按原样提供这些跟踪数据，但愿意帮助研究人员理解和使用它们。如有任何问题或疑问，请发送电子邮件至我们的 邮件列表。

## Quick links by paper:  按论文的快速链接

* Traces ([2017](https://github.com/Azure/AzurePublicDataset/blob/master/AzurePublicDatasetV1.md))([2019](https://github.com/Azure/AzurePublicDataset/blob/master/AzurePublicDatasetV2.md)) for the paper "Resource Central: Understanding and Predicting Workloads for Improved Resource Management in Large Cloud Platforms" (SOSP'17)
Traces用于论文“资源中心：理解和预测大型云平台中改进资源管理的工作负载”（SOSP‘17）
* Traces ([2019](https://github.com/Azure/AzurePublicDataset/blob/master/AzureFunctionsDataset2019.md)) for the paper "Serverless in the Wild: Characterizing and Optimizing the Serverless Workload at a Large Cloud Provider" (ATC'19)
Traces用于论文“野外无服务器：描述和优化大型云提供商的无服务器工作负载”（ATC‘19）
* Traces ([2020](https://github.com/Azure/AzurePublicDataset/blob/master/AzureTracesForPacking2020.md)) for the paper "Protean: VM Allocation Service at Scale" (OSDI'20)
Traces用于论文“蛋白质：大规模的虚拟机分配服务”（OSDI‘20）
* Traces ([2020](https://github.com/Azure/AzurePublicDataset/blob/master/AzureFunctionsBlobDataset2020.md)) for the paper "Faa$T: A Transparent Auto-Scaling Cache for Serverless Applications" (SoCC'21)
Traces用于论文“Faa$T：一个针对无服务器应用程序的透明自动扩展缓存”（SoCC‘21）
* Traces ([2023](https://github.com/Azure/AzurePublicDataset/blob/master/AzureLLMInferenceDataset2023.md)) for the paper "Splitwise: Efficient generative LLM inference using phase splitting" (ISCA'24)
Traces用于论文“分分裂：使用相位分裂的高效生成LLM推理”（ISCA‘24）
* Dataset and code ([2023](AzureGreenSKUFramework2023.md)) for the paper "Designing Cloud Servers for Lower Carbon" (ISCA'24)
Traces用于论文“设计低碳云服务器”（ISCA‘24）


## VM Traces 
VM 跟踪

The traces are sanitized subsets of the first-party VM workload in one of Azure’s geographical regions.  We include jupyter notebooks that directly compare the main characteristics of each trace to its corresponding full VM workload, showing that they are qualitatively very similar (except for VM deployment sizes in 2019).  Comparing the characteristics of the two traces illustrates how the workload has changed over this two-year span.
这些跟踪数据是来自 Azure 某个地理区域的第一方 VM 工作负载的清理子集。我们提供了 Jupyter notebooks，直接对比每个跟踪数据与相应完整 VM 工作负载的主要特征，显示它们在质量上非常相似（2019 年的 VM 部署规模除外）。

If you do use either of these VM traces in your research, please make sure to cite our SOSP’17 paper ["Resource Central: Understanding and Predicting Workloads for Improved Resource Management in Large Cloud Platforms"](https://www.microsoft.com/en-us/research/wp-content/uploads/2017/10/Resource-Central-SOSP17.pdf), which includes a full analysis of the Azure VM workload in 2017.
通过对比两个跟踪数据的特征，可以观察到这两年间工作负载的变化。

### Trace Locations 跟踪数据位置


* [AzurePublicDatasetV1](https://github.com/Azure/AzurePublicDataset/blob/master/AzurePublicDatasetV1.md) - Trace created using data from 2017 Azure VM workload containing information about ~2M VMs and 1.2B utilization readings.
使用 2017 年的 Azure VM 工作负载数据创建的跟踪数据，包含约 200 万个 VM 和 12 亿条利用率记录。

* [AzurePublicDatasetV2](https://github.com/Azure/AzurePublicDataset/blob/master/AzurePublicDatasetV2.md) - Trace created using data from 2019 Azure VM workload containing information about ~2.6M VMs and 1.9B utilization readings.
使用 2019 年的 Azure VM 工作负载数据创建的跟踪数据，包含约 260 万个 VM 和 19 亿条利用率记录。

## Azure Traces for Packing 打包算法的 Azure 跟踪数据

* [AzureTracesForPacking2020](https://github.com/Azure/AzurePublicDataset/blob/master/AzureTracesForPacking2020.md) - This dataset represents part of the workload on Microsoft's Azure Compute and is specifically intended to evaluate packing algorithms. The dataset includes:
此数据集代表 Microsoft Azure 计算平台的部分工作负载，特别适用于评估打包算法。

  * VM requests along with their priority
  VM 请求及其优先级

  * The lifetime for each requested VM
  每个请求 VM 的生命周期

  * The (normalized) resources allocated for each VM type.
  每种 VM 类型的（标准化）资源分配


If you do use the Azure Trace for Packing in your research, please make sure to cite our OSDI'20 paper ["Protean: VM Allocation Service at Scale"](https://www.usenix.org/system/files/osdi20-hadary.pdf), which includes a description of the Azure allocator and related workload analysis.
如果您在研究中使用 Azure 打包跟踪数据，请确保引用我们的 OSDI'20 论文 "Protean: VM Allocation Service at Scale"，其中包含对 Azure 分配器和相关工作负载的分析。

## Azure Functions Traces
Azure Functions 跟踪数据

### Function Invocations 函数调用

* [AzureFunctionsDataset2019](https://github.com/Azure/AzurePublicDataset/blob/master/AzureFunctionsDataset2019.md) - These traces contain, for a subset of applications running on Azure Functions in July of 2019:
这些跟踪数据记录了 2019 年 7 月运行在 Azure Functions 上的部分应用：

  * how many times per minute each (anonymized) function is invoked and its corresponding trigger group
  每个（匿名化）函数每分钟的调用次数及其对应的触发组

  * how (anonymized) functions are grouped into (anonymized) applications, and how applications are grouped by (anonymized) owner
  匿名化）函数如何被分组到（匿名化）应用中，应用如何按（匿名化）所有者分组

  * the distribution of execution times per function
  每个函数的执行时间分布

  * the distribution of memory usage per application
  每个应用的内存使用分布

该数据集记录了 Azure Functions 中无服务器函数的调用频率、触发分组、执行时间和内存使用情况，用于研究无服务器计算的负载和性能。

If you do use the Azure Functions 2019 traces in your research, please make sure to cite our ATC'20 paper ["Serverless in the Wild: Characterizing and Optimizing the Serverless Workload at a Large Cloud Provider"](https://www.microsoft.com/en-us/research/uploads/prod/2020/05/serverless-ATC20.pdf), which includes a full analysis of the Azure Functions workload in July 2019.
如果您在研究中使用 Azure Functions 2019 跟踪数据，请确保引用我们的 ATC'20 论文 "Serverless in the Wild: Characterizing and Optimizing the Serverless Workload at a Large Cloud Provider"，其中包含对 2019 年 7 月 Azure Functions 工作负载的全面分析

* [AzureFunctionsInvocationTrace2021](https://github.com/Azure/AzurePublicDataset/blob/master/AzureFunctionsInvocationTrace2021.md) - This is a trace of function invocations for two weeks starting on 2021-01-31. The trace contains invocation arrival and departure (or compeletion) times, with the folloiwng schema:  
这是从 2021 年 1 月 31 日开始的两周函数调用跟踪，包含调用的到达和结束（或完成）时间，具体结构如下：

  * app: application id (encrypted)
  app: 应用 ID（加密）

  * func: function id (encrypted), and unique only within an application 
  func: 函数 ID（加密），在应用内唯一

  * end_timestamp: function invocation end timestamp in millisecond
  end_timestamp: 函数调用结束时间戳（以毫秒为单位）

  * duration: duration of function invocation in millisecond
  duration: 函数调用的持续时间（以毫秒为单位）

该数据集记录了函数调用的到达和完成时间，包含函数的执行时间及其他细节，适用于研究函数的响应时间和性能。

If you do use the Azure Functions 2021 trace in your research, please cite this SOSP'21 paper ["Faster and Cheaper Serverless Computing on Harvested Resources"](https://www.microsoft.com/en-us/research/publication/faster-and-cheaper-serverless-computing-on-harvested-resources/).
如果您在研究中使用 Azure Functions 2021 跟踪数据，请引用我们的 SOSP'21 论文 "Faster and Cheaper Serverless Computing on Harvested Resources"。

### Functions Blob Accesses
函数 Blob 访问

* [AzureFunctionsBlobDataset2020](https://github.com/Azure/AzurePublicDataset/blob/master/AzureFunctionsBlobDataset2020.md) - This is a sample of the blob accesses in Microsoft's Azure Functions, collected between November 23<sup>rd</sup> and December 6<sup>th</sup> 2020. This dataset is the data described and analyzed in the SoCC 2021 paper 'Faa$T: A Transparent Auto-Scaling Cache for Serverless Applications'.
AzureFunctionsBlobDataset2020 - 这是微软 Azure Functions 中的 blob 访问样本，收集时间为 2020 年 11 月 23 日至 12 月 6 日。此数据集在 SoCC 2021 论文 "Faa$T: A Transparent Auto-Scaling Cache for Serverless Applications" 中有详细描述和分析。

此数据集记录了 Azure Functions 在一段时间内的存储访问行为，适用于研究无服务器函数的缓存优化。

## Azure LLM Inference Traces
Azure LLM 推理跟踪数据

* [AzureLLMInferenceDataset2023](https://github.com/Azure/AzurePublicDataset/blob/master/AzureLLMInferenceDataset2023.md) - This is a sample of two LLM inference services in Azure containing the input and output tokens. This dataset was collected on November 11<sup>th</sup> 2023. This contains the data described and analyzed in the ISCA 2024 paper 'Splitwise: Efficient generative LLM inference using phase splitting'.
 这是 Azure 上两个 LLM 推理服务的样本数据，包含输入和输出 token。该数据集于 2023 年 11 月 11 日收集，并在 ISCA 2024 论文 "Splitwise: Efficient generative LLM inference using phase splitting" 中进行了描述和分析。

该数据集提供了 Azure LLM 推理服务的输入和输出数据，适合研究生成式 LLM 推理性能和优化策略。

* [AzureLLMInferenceDataset2024](https://github.com/Azure/AzurePublicDataset/blob/master/AzureLLMInferenceDataset2024.md) - This is a longer one week sample of two LLM inference services in Azure containing the input and output tokens. This dataset was collected on May 2024. This contains the data described and analyzed in the arxiv paper 'DynamoLLM: Designing LLM Inference Clusters for Performance and Energy Efficiency'.
这是 Azure 上两个 LLM 推理服务的一周样本数据，包含输入和输出 token。该数据集于 2024 年 5 月收集，并在 arxiv 论文 "DynamoLLM: Designing LLM Inference Clusters for Performance and Energy Efficiency" 中进行了描述和分析。

此数据集包含更长时间跨度的 LLM 推理服务数据，便于分析 LLM 集群的性能和能效。

### Contact us
Please let us know of any issues or questions by sending email to our [mailing list](mailto:azurepublicdataset@service.microsoft.com).
如有问题或疑问，请发送电子邮件至我们的 邮件列表。

These traces derive from a collaboration between Azure and Microsoft Research.
提供联系信息，方便研究人员针对数据集进行咨询。

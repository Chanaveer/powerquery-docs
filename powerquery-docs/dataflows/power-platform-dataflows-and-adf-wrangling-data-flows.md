---
title: How Power Platform dataflows and Azure Data Factory wrangling dataflows relate to each other
description: How Power Platform dataflows and Azure Data Factory wrangling dataflows relate to each other
author: radacad

ms.service: powerquery
ms.reviewer: v-douklo
ms.topic: conceptual
ms.date: 05/25/2020
ms.author: v-douklo
---

# How Power Platform dataflows and Azure Data Factory wrangling dataflows relate to each other?

[!INCLUDE [CDS note](../includes/cc-data-platform-banner.md)]

Power Platform dataflows and Azure Data Factory dataflows are often considered to be doing the same thing: extraction of the data from source systems, transforming the data, and loading the transformed data into a destination. However, there are differences in these two types of dataflows, and you can have a solution implemented that works with a combination of these technologies. This article describes this relationship in more detail.

## Power Platform dataflows

Power Platform dataflows are data transformation services empowered by the Power Query engine and hosted in the cloud. These dataflows get data from different data sources and, after applying transformations, store it either in Dataverse or in Azure Data Lake Storage.

![Power Platform dataflows diagram](media/dataflows-power-platform-dynamics-365/dataflow-function.png)

## Azure Data Factory wrangling dataflows

Azure Data Factory is an ETL service, which is cloud-based, and supports many different sources and destinations. There are two types of dataflows under this technology: mapping dataflows and wrangling dataflows. Wrangling dataflows are empowered by the Power Query engine for data transformation.

![Wrangling dataflow](https://docs.microsoft.com/azure/data-factory/media/wrangling-data-flow/tutorial6.png)

## What's in common?

Both Power Platform dataflows and Azure Data Factory wrangling dataflows are useful for getting data from one or more sources, applying transformations on the data using Power Query, and loading the transformed data into destinations (Extract, Transform, Load&mdash;in short, ETL). 

- both are empowered using Power Query data transformation.
- both are cloud-based technologies.

## What's the difference?

The main point is knowing their differences, because then you can think about scenarios to use each.

| Features                   | Power Platform dataflows                                     | Azure Data Factory wrangling dataflows                       |
| -------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Destinations               | Dataverse or Azure Data Lake Storage        | Many destinations, listed [here](https://azure.microsoft.com/blog/new-connectors-available-in-azure-data-factory-v2/) |
| Power Query transformation | All Power Query functions are supported                      | A limited list of functions supported&mdash;here is the [list](https://docs.microsoft.com/azure/data-factory/wrangling-data-flow-functions) |
| Sources                    | Many sources are supported                                  | Only a few sources&mdash;here is the [list](https://docs.microsoft.com/azure/data-factory/wrangling-data-flow-functions) |
| Scalability                | Depends on the Premium capacity and the use of the enhanced compute engine | Highly scalable, the query folding into spark code for cloud scale execution |

## What persona of the user?

If you're a citizen application developer or citizen data analyst with small to medium scale data to be integrated and transformed, you'll find the Power Platform dataflows more convenient. The large number of transformations available, and the ability to work with it without having developer knowledge, and the fact that it can be authored, monitored, and edited inside the Power BI or Power Platform portal, are all reasons that make Power Platform dataflows a great data integration solution for this type of developer.

If you're a data developer who's dealing with big data and huge datasets, and with a large scale of rows to be ingested every time, you'll find the Azure Data Factory wrangling dataflows a better tool for the job. The ability to have the spark code for the cloud scale execution can handle huge amount of data ingestion, and the other part of the dataflow can help with transforming the data. Working with the Azure portal to author, monitor, and edit wrangling dataflows requires a higher developer learning curve than the experience in Power Platform dataflows. Wrangling dataflows are best suited for this type of audience. 

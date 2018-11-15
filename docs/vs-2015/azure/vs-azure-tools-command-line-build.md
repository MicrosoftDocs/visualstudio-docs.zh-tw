---
title: 適用於 Azure 的命令列建置 |Microsoft Docs
description: 適用於 Azure 的命令列建置
author: ghogen
manager: douge
assetId: 94b35d0d-0d35-48b6-b48b-3641377867fd
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/05/2017
ms.author: ghogen
ms.openlocfilehash: fce752d91ebaa765e18efef117a3b6efe750119c
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002004"
---
# <a name="building-azure-projects-from-the-command-line"></a>建置 Azure 專案，從命令列
使用 Microsoft Build Engine (MSBuild)，您可以建置在未安裝 Visual Studio 的組建實驗室環境中的產品。 MSBuild 會使用 XML 格式之可擴充且 Microsoft 完全支援的專案檔案。 使用 MSBuild 檔案格式，您可以描述項目必須是針對一或多個平台和組態所建置。

您也可以在命令列執行 MSBuild，本主題將說明這個方法。 藉由在命令列上設定屬性，您可以建置特定專案的組態。 同樣地，您也可以定義 MSBuild 建置的目標。 如需有關命令列參數及 MSBuild 的詳細資訊，請參閱 < [MSBuild 命令列參考](https://msdn.microsoft.com/library/ms164311.aspx)。

## <a name="msbuild-parameters"></a>MSBuild 參數
建立封裝最簡單的方式是執行與 MSBuild`/t:Publish`選項。 根據預設，此命令會建立相對於專案中，根資料夾的目錄如`<ProjectDirectory>\bin\Configuration\app.publish\`。 當您建置 Azure 專案時，會產生兩個檔案： 套件檔案本身及伴隨的組態檔：

* 套件檔案 (`project.cspkg`)
* 組態檔 (`ServiceConfiguration.TargetProfile.cscfg`)

根據預設，每個 Azure 專案都會包含一個本機 （偵錯） 組建服務組態檔，另一個用於雲端 （預備或生產） 組建。 不過，您可以新增或移除所需的服務組態檔。 當您建置 Visual Studio 內的封裝時，系統會詢問要隨套件包含哪個服務組態檔。 當您使用 MSBuild 建置封裝時，預設會包含本機服務組態檔。 若要包含不同的服務組態檔，設定`TargetProfile`MSBuild 命令的屬性 (`MSBuild /t:Publish /p:TargetProfile=ProfileName`)。

如果您想要使用替代目錄儲存的封裝和組態檔，請透過設定路徑`/p:PublishDir=Directory\`選項，包括尾端的反斜線分隔符號。

## <a name="next-steps"></a>後續步驟
建置套件之後，您可以將它部署至 Azure。
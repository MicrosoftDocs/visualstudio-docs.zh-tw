---
title: 使用 Visual Studio 設定 Azure 雲端服務專案 |Microsoft Docs
description: 了解如何在 Azure 雲端服務專案在 Visual Studio 中，根據需求設定該專案。
author: ghogen
manager: douge
assetId: 609d6965-05cc-47b1-82dc-c76a92d4f295
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/06/2017
ms.author: ghogen
ms.openlocfilehash: 7417bc117de7dc472f413dd9145944cad2d48bb4
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002015"
---
# <a name="configure-an-azure-cloud-service-project-with-visual-studio"></a>使用 Visual Studio 來設定 Azure 雲端服務專案
您可以設定 Azure 雲端服務專案，根據您的需求，該專案。 您可以設定下列類別的專案屬性：

- **雲端服務發行至 Azure** -您可以設定屬性，以確保不被意外刪除現有的雲端服務部署至 Azure。
- **執行或偵錯雲端服務在本機電腦上的**-您可以選取要使用，並指出您是否想要啟動 Azure 儲存體模擬器的服務組態。
- **建立時，驗證雲端服務封裝**-您可以決定將警告視為錯誤，以便您可以確保雲端服務套件部署沒有任何問題。 

## <a name="steps-to-configure-an-azure-cloud-service-project"></a>若要設定 Azure 雲端服務專案的步驟
1. 開啟或在 Visual Studio 中建立雲端服務專案

1. 在 **方案總管**，以滑鼠右鍵按一下專案，並從操作功能表中，選取**屬性**。
   
1. 在專案的屬性頁面中，選取**開發** 索引標籤。

    ![專案屬性功能表](./media/vs-azure-tools-configuring-an-azure-project/solution-explorer-project-properties-menu.png)

1. 設定**刪除現有部署之前提示**要 **，則為 True**。 此設定可協助確保您不會意外刪除 Azure 中的現有部署

1. 選取想要**服務組態**想要使用當您執行或偵錯您的雲端服務本機表示的服務組態。 如需有關如何修改某個角色的服務組態的詳細資訊，請參閱 <<c0> [ 如何使用 Visual Studio 設定 Azure 雲端服務角色](./vs-azure-tools-configure-roles-for-cloud-service.md)。

1. 設定**啟動 Azure 儲存體模擬器**要 **，則為 True**啟動 Azure 儲存體模擬器，當您執行或偵錯您的雲端服務在本機。

1. 設定**將警告視為錯誤**要 **，則為 True**以確保發生封裝驗證錯誤時，您無法發佈。

1. 設定**使用 web 專案連接埠**要 **，則為 True**藉此確定您的 web 角色會使用相同的連接埠每次啟動 IIS Express 在本機。

1. 從 Visual Studio 工具列中，選取**儲存**。

## <a name="next-steps"></a>後續步驟
- [設定 Azure 專案使用多個服務組態](vs-azure-tools-multiple-services-project-configurations.md)


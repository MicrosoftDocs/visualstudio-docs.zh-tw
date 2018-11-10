---
title: 使用 Visual Studio 建立 Azure 雲端服務專案 |Microsoft Docs
description: 立即了解如何使用 Visual Studio 建立 Azure 雲端服務專案
author: ghogen
manager: douge
assetId: ec580df7-3dcc-45a9-a1d9-8c110678dfb5
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 8149f60440becb3c7a8d0dc08b2a1a9c00fb171a
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002058"
---
# <a name="creating-an-azure-cloud-service-project-with-visual-studio"></a>使用 Visual Studio 建立 Azure 雲端服務專案
Azure Tools for Visual Studio 提供可讓您建立的專案範本[Azure 雲端服務](/azure/cloud-services/cloud-services-choose-me)，這是一個簡單的一般用途的 Azure 服務。 一旦建立專案之後，Visual Studio 可讓您設定、 偵錯及部署至 Azure 的雲端服務。

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>在 Visual Studio 中建立的 Azure 雲端服務專案的步驟
本節會引導您在 Visual Studio 中建立的 Azure 雲端服務專案，使用一或多個 web 角色。  

1. 系統管理員身分啟動 Visual Studio。

1. 在主功能表中，選取**檔案** > **新增** > **專案**。

1. 選取 **雲端**從 視覺效果C#或 Visual Basic 專案範本節點，然後選取**Azure 雲端服務**從範本清單。

    ![新的 Azure 雲端服務](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. 指定您想要用來開發專案的.NET framework 版本。

1. 輸入名稱和位置，為您的專案和方案的名稱。 

1. 選取 [確定]。

1. 在 [**新的 Microsoft Azure 雲端服務**] 對話方塊中，選取您要新增的角色，然後選擇向右箭號按鈕，以將它們新增至您的解決方案。

    ![選取新的 Azure 雲端服務角色](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. 若要重新命名已加入的角色，將滑鼠停留在中的角色**新的 Microsoft Azure 雲端服務** 對話方塊中，然後從操作功能表中，選取**重新命名**。 您可以在您的解決方案也重新命名角色 (在**方案總管 中**) 已加入之後。

    ![重新命名 Azure 雲端服務角色](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure 專案方案中有關聯的角色專案。 專案也包含*服務定義檔*並*服務組態檔*:

- **服務定義檔**-定義您的應用程式，包括需要哪些角色、 端點和虛擬機器大小的執行階段設定。 
- **服務組態檔**-設定多少個角色執行個體都執行，以及為角色定義的設定值。 

如需有關這些檔案的詳細資訊，請參閱 <<c0> [ 使用 Visual Studio 設定 Azure 雲端服務角色](vs-azure-tools-configure-roles-for-cloud-service.md)。

## <a name="next-steps"></a>後續步驟
- [在 Azure 雲端服務專案使用 Visual Studio 中管理角色](./vs-azure-tools-cloud-service-project-managing-roles.md)

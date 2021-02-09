---
title: 建立 Azure 雲端服務專案
description: 立即了解如何使用 Visual Studio 建立 Azure 雲端服務專案
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/19/2019
ms.author: ghogen
ms.openlocfilehash: d652172bde2ecd3aea4bb027e46173eaa5fe7b17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844498"
---
# <a name="create-an-azure-cloud-service-project-with-visual-studio"></a>使用 Visual Studio 來建立 Azure 雲端服務專案

Visual Studio 提供專案範本，可讓您建立 [azure 雲端服務](/azure/cloud-services/cloud-services-choose-me)，這是一個簡單的一般用途 azure 服務。 一旦建立專案之後，Visual Studio 可讓您對雲端服務進行設定和偵錯，以及部署至 Azure。

## <a name="steps-to-create-an-azure-cloud-service-project-in-visual-studio"></a>在 Visual Studio 中建立 Azure 雲端服務專案的步驟
本節將逐步引導您在 Visual Studio 中使用一或多個 Web 角色來建立 Azure 雲端服務專案。

::: moniker range="vs-2017"
1. 以系統管理員身分開啟 Visual Studio。

1. 在主功能表中，選取 [檔案]**[新增]** > **[專案]** > 。

1. 從 Visual C# 或 Visual Basic 專案範本節點中選取 [雲端]，然後從範本清單中選取 [Azure 雲端服務]。

    ![新增 Azure 雲端服務](./media/vs-azure-tools-azure-project-create/new-project-wizard-for-cloud-service.png)

1. 指定您想要用來開發專案的 .NET Framework 版本。

1. 輸入專案的名稱和位置以及方案的名稱。

1. 選取 [確定]。
::: moniker-end
::: moniker range=">=vs-2019"
1. 在 [開始] 視窗中，選擇 [建立新專案]。

1. 在 [搜尋] 方塊中，鍵入「雲端」，然後選擇 [Azure 雲端服務]。

   ![新增 Azure 雲端服務](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service.png)

1. 提供專案名稱，然後選擇 [建立]。

   ![提供專案名稱](./media/vs-azure-tools-azure-project-create/vs-2019/new-project-cloud-service-2.png)
::: moniker-end

1. 在 [新增 Microsoft Azure 雲端服務] 對話方塊中，選取您想要新增的角色，然後選擇向右箭號按鈕以將它們新增到您的方案。

    ![選取新的 Azure 雲端服務角色](./media/vs-azure-tools-azure-project-create/new-cloud-service.png)

1. 若要將您所新增的角色重新命名，可將滑鼠游標停留在 [新增 Microsoft Azure 雲端服務] 對話方塊中的角色上方，然後從操作功能表中選取[重新命名]。 您也可以在方案內 (在 [方案總管] 中) 為已新增的角色重新命名。

    ![將 Azure 雲端服務角色重新命名](./media/vs-azure-tools-azure-project-create/new-cloud-service-rename.png)

Visual Studio Azure 專案與方案中的角色專案有關。 專案還包含「服務定義檔」和「服務組態檔」：

- **服務定義** 檔-定義應用程式的執行時間設定，包括需要哪些角色、端點和虛擬機器大小。
- **服務組態檔** - 設定一個角色可以執行的執行個體數目，以及為角色定義的設定值。

如需這些檔案的詳細資訊，請參閱[使用 Visual Studio 設定 Azure 雲端服務的角色](vs-azure-tools-configure-roles-for-cloud-service.md)。

## <a name="next-steps"></a>下一步
- [使用 Visual Studio 在 Azure 雲端服務專案中管理角色](./vs-azure-tools-cloud-service-project-managing-roles.md)

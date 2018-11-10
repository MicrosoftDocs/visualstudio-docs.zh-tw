---
title: 在使用 Visual Studio 的 Azure 雲端服務中管理角色 |Microsoft Docs
description: 了解如何新增和移除 Azure 雲端服務，使用 Visual Studio 中的角色。
author: ghogen
manager: douge
assetId: 5ec9ae2e-8579-4e5d-999e-8ae05b629bd1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 35221cbf98f26a71e2b4adf0a7178342616ff7c0
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001974"
---
# <a name="managing-roles-in-azure-cloud-services-with-visual-studio"></a>在使用 Visual Studio 的 Azure 雲端服務中管理角色
建立您的 Azure 雲端服務之後，您可以加入新的角色，或移除現有的角色。 您也可以匯入現有的專案，並將它轉換成角色。 比方說，您可以匯入 ASP.NET web 應用程式，並將它指定做為 web 角色。

## <a name="adding-a-role-to-an-azure-cloud-service"></a>將角色加入至 Azure 雲端服務
下列步驟會引導您完成將 web 或背景工作角色加入至 Visual Studio 中的 Azure 雲端服務專案。

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 [**方案總管] 中**，展開專案節點

1. 以滑鼠右鍵按一下**角色**節點以顯示操作功能表。 從操作功能表中，選取**新增**，然後從目前的方案中，選取現有的 web 角色或背景工作角色，或建立 web 或背景工作角色專案。 您也可以選取適當的專案，例如 ASP.NET web 應用程式專案，並將它與角色專案產生關聯。

    ![若要將角色新增至 Azure 雲端服務專案的功能表選項](./media/vs-azure-tools-cloud-service-project-managing-roles/add-role.png)

## <a name="removing-a-role-from-an-azure-cloud-service"></a>從 Azure 雲端服務移除角色
下列步驟會引導您從 Visual Studio 中的 Azure 雲端服務專案移除 web 或背景工作角色。

1. 建立或開啟 Visual Studio 中的 Azure 雲端服務專案。

1. 在 [**方案總管] 中**，展開專案節點

1. 依序展開**角色**節點。

1. 以滑鼠右鍵按一下您想要移除，並從操作功能表中選取的節點**移除**。 

    ![若要將角色新增至 Azure 雲端服務的功能表選項](./media/vs-azure-tools-cloud-service-project-managing-roles/remove-role.png)

## <a name="readding-a-role-to-an-azure-cloud-service-project"></a>重新角色新增至 Azure 雲端服務專案
如果您從雲端服務專案中移除角色，但稍後決定回饋給本專案中加入角色，就會加入只有角色宣告和基本屬性，例如端點和診斷資訊。 沒有其他資源或參考加入至`ServiceDefinition.csdef`檔案或`ServiceConfiguration.cscfg`檔案。 如果您想要新增這項資訊，您需要手動將它加回這些檔案。

例如，您可能會移除 web 服務角色，而您稍後決定將這個角色加回您的解決方案。 如果您這樣做時，就會發生錯誤。 若要避免這個錯誤，您必須新增`<LocalResources>`回下列 XML 所示的項目`ServiceDefinition.csdef`檔案。 使用已加回到專案的名稱屬性的 web 服務角色的名稱**<LocalStorage>** 項目。 在此範例中，web 服務角色的名稱是**WCFServiceWebRole1**。

    <WebRole name="WCFServiceWebRole1">
        <Sites>
          <Site name="Web">
            <Bindings>
              <Binding name="Endpoint1" endpointName="Endpoint1" />
            </Bindings>
          </Site>
        </Sites>
        <Endpoints>
          <InputEndpoint name="Endpoint1" protocol="http" port="80" />
        </Endpoints>
        <Imports>
          <Import moduleName="Diagnostics" />
        </Imports>
       <LocalResources>
          <LocalStorage name="WCFServiceWebRole1.svclog" sizeInMB="1000" cleanOnRoleRecycle="false" />
       </LocalResources>
    </WebRole>

## <a name="next-steps"></a>後續步驟
- [使用 Visual Studio 設定 Azure 雲端服務角色](vs-azure-tools-configure-roles-for-cloud-service.md)

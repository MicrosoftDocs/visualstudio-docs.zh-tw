---
title: 如何：建立 SharePoint 命令 |Microsoft Docs
description: 瞭解如何建立自訂 SharePoint 命令，以在 SharePoint 工具擴充功能中呼叫伺服器物件模型的 API。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 51b80124f7cf550843ad346e9d1e1c0b21ccd0f7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99923350"
---
# <a name="how-to-create-a-sharepoint-command"></a>如何：建立 SharePoint 命令
  如果您想要在 SharePoint 工具擴充功能中使用伺服器物件模型，您必須建立自訂 *SharePoint 命令* 以呼叫 API。 您可以在可以直接呼叫伺服器物件模型的元件中定義 SharePoint 命令。

 如需有關 SharePoint 命令用途的詳細資訊，請參閱 [呼叫 sharepoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

### <a name="to-create-a-sharepoint-command"></a>若要建立 SharePoint 命令

1. 建立具有下列設定的類別庫專案：

    - 以 .NET Framework 3.5 為目標。 如需有關選取目標 framework 的詳細資訊，請參閱 [如何：以 .NET Framework 版本為目標](../ide/visual-studio-multi-targeting-overview.md)。

    - 以 AnyCPU 或 x64 平臺為目標。 依預設，類別庫專案的目標平臺為 AnyCPU。 如需有關選取目標平臺的詳細資訊，請參閱 [如何：將專案設定成以平臺為目標](../ide/how-to-configure-projects-to-target-platforms.md)。

    > [!NOTE]
    > 您無法在定義 SharePoint 工具擴充功能的相同專案中，執行 SharePoint 命令，因為 SharePoint 命令以 .NET Framework 3.5 和 SharePoint 工具延伸模組為目標 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 。 您必須在個別的專案中定義您的延伸模組所使用的任何 SharePoint 命令。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

2. 加入下列組件的參考：

    - VisualStudio 命令

    - Microsoft SharePoint

3. 在專案的類別中，建立可定義 SharePoint 命令的方法。 方法必須符合下列指導方針：

    - 它可以有一或兩個參數。

         第一個參數必須是 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 物件。 這個物件會提供執行命令的 Microsoft.......................。 它也提供 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> 可用來將訊息寫入至 [ **輸出** ] 視窗或 [ **錯誤清單** ] 視窗的物件 Visual Studio 中。

         第二個參數可以是您選擇的類型，但這個參數是選擇性的。 如果您需要將 SharePoint 工具延伸模組的資料傳遞至命令，您可以將此參數新增至 SharePoint 命令。

    - 它可以有傳回值，但這是選擇性的。

    - 第二個參數和傳回值必須是可由 Windows Communication Foundation (WCF) 序列化的型別。 如需詳細資訊，請參閱 [資料合約序列化程式支援的類型](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) 和 [使用 XmlSerializer 類別](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)。

    - 方法可以有任何可見度 (**public**、 **internal** 或 **private**) ，而且可以是靜態或非靜態。

4. 將套用 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 至方法。 這個屬性會指定命令的唯一識別碼;此識別碼不需要符合方法名稱。

     當您從 SharePoint 工具延伸模組呼叫命令時，必須指定相同的唯一識別碼。 如需詳細資訊，請參閱 how [to：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。

## <a name="example"></a>範例
 下列程式碼範例示範具有識別碼的 SharePoint 命令 `Contoso.Commands.UpgradeSolution` 。 此命令會使用伺服器物件模型中的 Api 來升級至已部署的方案。

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 除了隱含的第一個 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數之外，此命令也有自訂字串參數，其中包含正在升級至 SharePoint 網站之 .wsp 檔案的完整路徑。 若要在較大範例的內容中查看這個程式碼，請參閱 [逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

## <a name="compiling-the-code"></a>編譯程式碼
 此範例需要下列元件的參考：

- VisualStudio 命令

- Microsoft SharePoint

## <a name="deploying-the-command"></a>部署命令
 若要部署命令，請將命令元件包含在相同的 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 延伸模組 (*Vsix*) 封裝和使用命令的延伸模組元件。 您也必須在 extension.vsixmanifest 檔案中加入命令元件的專案。 如需詳細資訊，請參閱 [Visual Studio 中的部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>另請參閱
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [How to：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

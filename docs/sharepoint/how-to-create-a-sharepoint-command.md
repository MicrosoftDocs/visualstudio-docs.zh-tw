---
title: 如何：建立 SharePoint 命令 |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c07d541dc4f68f33d48e7cb41b6bc3923b2ea52
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189238"
---
# <a name="how-to-create-a-sharepoint-command"></a>如何：建立 SharePoint 命令
  如果您想要在 SharePoint 工具擴充功能中使用伺服器物件模型，您必須建立自訂*sharepoint 命令*來呼叫 API。 您會在可直接呼叫伺服器物件模型的元件中定義 SharePoint 命令。

 如需 SharePoint 命令用途的詳細資訊，請參閱[呼叫 sharepoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

### <a name="to-create-a-sharepoint-command"></a>若要建立 SharePoint 命令

1. 建立具有下列設定的類別庫專案：

    - 以 .NET Framework 3.5 為目標。 如需選取目標 framework 的詳細資訊，請參閱[如何：以 .NET Framework 的版本為目標](../ide/visual-studio-multi-targeting-overview.md)。

    - 以 AnyCPU 或 x64 平臺為目標。 根據預設，類別庫專案的目標平臺為 AnyCPU。 如需選取目標平臺的詳細資訊，請參閱[如何：將專案設定成以平臺為目標](../ide/how-to-configure-projects-to-target-platforms.md)。

    > [!NOTE]
    > 您無法在定義 SharePoint 工具延伸模組的相同專案中執行 SharePoint 命令，因為 SharePoint 命令的目標是 .NET Framework 3.5，而 SharePoint 工具延伸模組的目標是 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 您必須在個別的專案中定義擴充功能所使用的任何 SharePoint 命令。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

2. 加入下列組件的參考：

    - VisualStudio 的命令

    - Microsoft SharePoint

3. 在專案的類別中，建立可定義 SharePoint 命令的方法。 方法必須符合下列指導方針：

    - 它可以有一個或兩個參數。

         第一個參數必須是 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 物件。 這個物件會提供執行命令所在的 Microsoft. SharePoint. SPSite 或 node.js。 它也會提供 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> 物件，可用來將訊息寫入至 [**輸出**] 視窗或 Visual Studio 中的 [**錯誤清單**] 視窗。

         第二個參數可以是您選擇的類型，但此參數是選擇性的。 如果您需要將 SharePoint 工具延伸模組的資料傳遞至命令，您可以將此參數加入至 SharePoint 命令。

    - 它可以有傳回值，但這是選擇性的。

    - 第二個參數和傳回值必須是可由 Windows Communication Foundation （WCF）序列化的類型。 如需詳細資訊，請參閱[資料合約序列化程式支援的類型](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer)和[使用 XmlSerializer 類別](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)。

    - 方法可以有任何可見度（**公用**、**內部**或**私**用），而且可以是靜態或非靜態。

4. 將 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 套用至方法。 這個屬性會指定命令的唯一識別碼;此識別碼不需要符合方法名稱。

     當您從 SharePoint 工具延伸模組呼叫命令時，必須指定相同的唯一識別碼。 如需詳細資訊，請參閱[如何：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。

## <a name="example"></a>範例
 下列程式碼範例示範具有 `Contoso.Commands.UpgradeSolution`識別碼的 SharePoint 命令。 此命令會使用伺服器物件模型中的 Api 來升級至已部署的解決方案。

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 除了隱含的第一個 <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> 參數之外，此命令也具有自訂字串參數，其中包含正在升級至 SharePoint 網站之 .wsp 檔案的完整路徑。 若要在較大的範例內容中查看這個程式碼，請參閱[逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

## <a name="compiling-the-code"></a>編譯程式碼
 這個範例需要參考下列元件：

- VisualStudio 的命令

- Microsoft SharePoint

## <a name="deploying-the-command"></a>部署命令
 若要部署命令，請將命令元件包含在相同的 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 擴充功能（*vsix*）封裝中，並搭配使用命令的延伸模組元件。 您也必須在 extension.vsixmanifest 檔案中新增命令元件的專案。 如需詳細資訊，請參閱[在 Visual Studio 中部署 SharePoint 工具的擴充](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)功能。

## <a name="see-also"></a>請參閱
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [如何：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [逐步解說：擴充伺服器總管以顯示 web 元件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

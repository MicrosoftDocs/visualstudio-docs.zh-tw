---
title: HOW TO：建立 SharePoint 命令 |Microsoft Docs
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
ms.openlocfilehash: 4ac6e63bf0f669364e3011360fa74b7d8fde8662
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645104"
---
# <a name="how-to-create-a-sharepoint-command"></a>HOW TO：建立 SharePoint 命令
  如果您想要使用 SharePoint 工具擴充功能中的伺服器物件模型，您必須建立自訂*SharePoint 命令*來呼叫 API。 您可以直接呼叫伺服器物件模型的組件中定義之 SharePoint 命令。

 如需有關 SharePoint 命令的用途的詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。

### <a name="to-create-a-sharepoint-command"></a>若要建立 SharePoint 命令

1.  建立具有下列組態的類別庫專案：

    -   .NET Framework 3.5 為目標。 如需有關如何選取目標 framework 的詳細資訊，請參閱[How to:以一個 .NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。

    -   目標 AnyCPU 或 x64 平台。 根據預設，類別庫專案的目標平台會為 AnyCPU。 如需有關如何選取目標平台的詳細資訊，請參閱[How to:將專案設定到目標平台](../ide/how-to-configure-projects-to-target-platforms.md)。

    > [!NOTE]
    >  您無法在相同的專案定義的 SharePoint 工具延伸模組中，實作 SharePoint 命令，因為 SharePoint 命令的目標.NET Framework 3.5 和 SharePoint 工具擴充功能目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 您必須定義任何您在個別的專案中的延伸模組所使用的 SharePoint 命令。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

2.  加入下列組件的參考：

    -   Microsoft.VisualStudio.SharePoint.Commands

    -   Microsoft.SharePoint

3.  在專案中的類別，建立定義您的 SharePoint 命令的方法。 此方法必須符合下列指導方針：

    -   它可以有一或兩個參數。

         第一個參數必須是<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>物件。 這個物件提供 Microsoft.SharePoint.SPSite 或 Microsoft.SharePoint.SPWeb 執行命令。 它也會提供<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>可用來寫入訊息至的物件**輸出**視窗或**錯誤清單**Visual Studio 中的視窗。

         第二個參數可以是您選擇的類型，但這是選擇性參數。 如果您需要將資料從您的 SharePoint 工具延伸模組傳遞至命令，您可以新增此參數至您的 SharePoint 命令。

    -   它可以有傳回值，但這是選擇性的。

    -   第二個參數和傳回值必須是可由 Windows Communication Foundation (WCF) 序列化的型別。 如需詳細資訊，請參閱 < [Types Supported by the Data Contract Serializer](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer)並[使用 XmlSerializer 類別](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)。

    -   方法可以有任何可見性 (**公開金鑰**，**內部**，或**私人**)，而且它可以是靜態或非靜態。

4.  套用<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>方法。 這個屬性會指定命令的唯一識別碼這個識別項並沒有符合的方法名稱。

     從您的 SharePoint 工具擴充功能呼叫命令時，您必須指定相同的唯一識別碼。 如需詳細資訊，請參閱[如何：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。

## <a name="example"></a>範例
 下列程式碼範例示範具有識別碼的 SharePoint 命令`Contoso.Commands.UpgradeSolution`。 若要升級至已部署的解決方案，此命令會使用 Api 伺服器物件模型中。

 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]

 除了隱含的第一個<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>參數，此命令也有自訂的字串參數，其中包含正在升級至 SharePoint 網站的.wsp 檔案的完整路徑。 若要查看較大範例的內容中此程式碼，請參閱[逐步解說：建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。

## <a name="compiling-the-code"></a>編譯程式碼
 這個範例需要參考下列組件：

-   Microsoft.VisualStudio.SharePoint.Commands

-   Microsoft.SharePoint

## <a name="deploying-the-command"></a>部署命令
 若要部署的命令，包括命令組件在同一[!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]延伸模組 (*vsix*) 與延伸模組組件，以使用命令的封裝。 您也必須加入一個項目命令中的組件 extension.vsixmanifest 檔案。 如需詳細資訊，請參閱 <<c0> [ 部署適用於 Visual Studio 中 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。

## <a name="see-also"></a>另請參閱
- [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [如何：執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [逐步解說：擴充伺服器總管以顯示 web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

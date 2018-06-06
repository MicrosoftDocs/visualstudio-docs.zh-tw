---
title: 如何： 建立 SharePoint 命令 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 026c15241ace87a3d7454afb2439e045d06ce67b
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2018
ms.locfileid: "34767659"
---
# <a name="how-to-create-a-sharepoint-command"></a>如何： 建立 SharePoint 命令
  如果您想要使用伺服器物件模型中的 SharePoint 工具擴充功能，您必須建立自訂*SharePoint 命令*來呼叫 API。 您可以直接呼叫伺服器物件模型的組件中定義 SharePoint 命令。  
  
 如需有關 SharePoint 命令的用途的詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
### <a name="to-create-a-sharepoint-command"></a>若要建立 SharePoint 命令  
  
1.  建立類別庫專案具有下列設定：  
  
    -   以.NET Framework 3.5 為目標。 如需選取的目標 framework 的詳細資訊，請參閱[How to： 以.NET Framework 版本為目標](../ide/how-to-target-a-version-of-the-dotnet-framework.md)。  
  
    -   目標 AnyCPU 或 x64 平台。 根據預設，類別庫專案的目標平台為 AnyCPU。 如需選取目標平台的詳細資訊，請參閱[How to： 設定專案的目標平台](../ide/how-to-configure-projects-to-target-platforms.md)。  
  
    > [!NOTE]  
    >  您無法在相同的專案定義的 SharePoint 工具擴充功能，實作 SharePoint 命令，因為 SharePoint 命令的目標.NET Framework 3.5 和 SharePoint 工具擴充功能目標[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]。 您必須定義您的擴充功能，在個別的專案由任何 SharePoint 命令。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
2.  加入下列組件的參考：  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  在專案中的類別，建立定義 SharePoint 命令的方法。 此方法必須符合下列指導方針：  
  
    -   它可以有一或兩個參數。  
  
         第一個參數必須是<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>物件。 這個物件提供 Microsoft.SharePoint.SPSite 或 Microsoft.SharePoint.SPWeb 執行命令。 它也提供<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger>物件，可用於寫入訊息至**輸出**視窗或**錯誤清單**Visual Studio 中的視窗。  
  
         第二個參數可以是一種您的選擇，但這是選擇性參數。 如果您要從您的 SharePoint 工具擴充功能的資料傳遞給命令，您可以對您的 SharePoint 命令新增這個參數。  
  
    -   它可以有傳回值，但這是選擇性的。  
  
    -   第二個參數和傳回值必須是 Windows Communication Foundation (WCF) 可序列化的型別。 如需詳細資訊，請參閱[資料合約序列化程式所支援的型別](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer)和[使用 XmlSerializer 類別](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class)。  
  
    -   此方法可以有任何可見性 (**公用**，**內部**，或**私人**)，而且它可以是靜態或非靜態。  
  
4.  套用<xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute>方法。 這個屬性會指定命令; 的唯一識別碼要比對的方法名稱沒有這個識別項。  
  
     當您從您的 SharePoint 工具擴充功能呼叫命令時，您必須指定相同的唯一識別碼。 如需詳細資訊，請參閱[如何： 執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範具有識別碼的 SharePoint 命令`Contoso.Commands.UpgradeSolution`。 若要升級至已部署的方案，此命令會使用 Api 伺服器物件模型中。  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 除了隱含的第一個<xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext>參數，此命令也有自訂字串參數，其中包含正在升級至 SharePoint 網站的.wsp 檔案的完整路徑。 若要查看此程式碼之較大範例的內容中，請參閱[逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要參考下列組件：  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>部署命令  
 若要部署命令，包括命令組件在相同[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]延伸模組 (*vsix*) 與延伸模組組件，以使用命令的封裝。 您也必須加入一個項目命令中的組件 extension.vsixmanifest 檔案。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱
 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [如何： 執行 SharePoint 命令](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [逐步解說：擴充伺服器總管以顯示 Web 組件](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  

---
title: Visual Studio Tools for Office 執行時間中的元件
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6c227748e1808aecabd9554b0e6b398a7c6c6df1
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986197"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office 執行時間中的元件
  當您建立 Office 專案時，Visual Studio 會自動針對專案類型和專案的目標 .NET Framework，加入適用 [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] 組件的參考。 適用於 .NET Framework 3.5、 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]和 [!INCLUDE[net_v45](includes/net-v45-md.md)]的 Office 擴充功能包含不同的組件。 如需 Office 擴充功能的詳細資訊，請參閱[Visual Studio Tools for Office 執行時間總覽](visual-studio-tools-for-office-runtime-overview.md)。

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-includenet_v45includesnet-v45-mdmd"></a>適用于 .NET Framework 4 和 [!INCLUDE[net_v45](includes/net-v45-md.md)] 之 Office 擴充功能中的元件
 下表列出適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](includes/net-v45-md.md)]的 Office 擴充功能隨附的組件。 如需這些元件中之命名空間和類型的相關檔，請參閱[Visual Studio &#40; &#41;中的 Managed 參考 Office 程式開發](managed-reference-office-development-in-visual-studio.md)。

|組件名稱|描述|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|提供下列類型：<br /><br /> -用於建立功能區自訂和智慧標籤的類型。 **注意：**     智慧標籤在 [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](includes/word-14-short-md.md)]中已被取代。<br />-用來在檔層級自訂中建立執行窗格的類型，以及 VSTO 增益集的自訂工作窗格。|
|Microsoft.Office.Tools.Excel.dll|提供代表 Excel 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱[使用擴充物件自動化 Excel](automating-excel-by-using-extended-objects.md)。|
|Microsoft.Office.Tools.Outlook.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類型。|
|Microsoft.Office.Tools.Word.dll|提供代表 Word 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱[使用擴充物件自動化 Word](automating-word-by-using-extended-objects.md)。|
|Microsoft.Office.Tools.v4.0.Framework.dll|提供下列類型：<br /><br /> -Visual Studio Tools for Office 執行時間可以擲回的例外狀況。<br />-您可以在建立 Outlook 表單區域時使用的屬性。|
|Microsoft.Office.Tools.dll|提供屬於 Visual Studio Tools for Office Runtime 基礎結構，而且不適合直接從程式碼使用的類型。|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性和 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 介面，您可以用來快取檔層級自訂中的資料物件。 如需詳細資訊，請參閱快取[資料](caching-data.md)。<br />-<xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 介面，您可以將它執行以執行其他安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](deploying-an-office-solution-by-using-clickonce.md)。<br />-Visual Studio Tools for Office 執行時間可以擲回的例外狀況。<br />-屬於 Visual Studio Tools for Office 執行時間基礎結構，但不適合直接從程式碼使用的其他類型。|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別，您可以用來將自訂群組件附加至檔，並存取檔中的快取資料。 如需詳細資訊，請參閱[使用 ServerDocument 類別管理伺服器上的檔](managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-數個類別，代表檔層級自訂中快取資料的階層。 如需詳細資訊，請參閱在[伺服器上存取檔中的資料](accessing-data-in-documents-on-the-server.md)。|

 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](includes/net-v45-md.md)] 為目標的專案還會參考下列組件。 這些組件不是 [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] 可轉散發套件的一部分， 而是必須隨方案一起部署的相依組件。 根據預設，這些組件會複製到專案的組建輸出資料夾 (當這些組件的 [複製到本機] 屬性設定為 [True]時)。 如果使用 ClickOnce 部署專案，這些組件會包含在產生的套件中。

|組件名稱|描述|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|提供 VSTO 增益集專案中產生之 `ThisAddIn` 類別的基底類別，以及所有專案中產生之功能區類別的基底類別。|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|提供下列類型：<br /><br /> -在 Excel 檔層級專案中產生的 `ThisWorkbook` 和 `Sheet` 類別的基類。<br />-Windows Forms 控制項，可用於 Excel 專案中的工作表。|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|提供 Outlook 專案中產生之 `ThisAddIn` 和表單區域類別的基底類別。|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|提供下列類型：<br /><br /> -Word 檔層級專案中產生之 `ThisDocument` 類別的基底類別。<br />-您可以在 Word 專案中的檔上使用的 Windows Forms 控制項。|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>適用于 .NET Framework 3.5 之 Office 擴充功能中的元件
 下表列出適用於 .NET Framework 3.5 的 Office 擴充功能隨附的組件。 如需這些元件中之命名空間和類別的相關檔，請參閱 Visual Studio 2008 檔中的下列參考章節： [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md)。

|組件名稱|描述|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|提供下列類型：<br /><br /> -VSTO 增益集的 Microsoft. Tools .Addin 基類。<br />-用於建立功能區自訂和智慧標籤的類別。 **注意：**     智慧標籤在 [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](includes/word-14-short-md.md)]中已被取代。<br />-在檔層級自訂和 VSTO 增益集的自訂工作窗格中建立動作窗格的類別。|
|Microsoft.Office.Tools.Excel.v9.0.dll|提供 Excel 方案的主項目和主控制項。 如需詳細資訊，請參閱[使用擴充物件自動化 Excel](automating-excel-by-using-extended-objects.md)。|
|Microsoft.Office.Tools.Outlook.v9.0.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類別。|
|Microsoft.Office.Tools.Word.v9.0.dll|提供 Word 方案的主項目和主控制項。 如需詳細資訊，請參閱[使用擴充物件自動化 Word](automating-word-by-using-extended-objects.md)。|
|Microsoft.Office.Tools.v9.0.dll|提供下列類型：<br /><br /> - [RemoteBindableComponent](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90))類別，提供檔層級自訂中主控制項的資料系結功能。<br />-屬於 Visual Studio Tools for Office 執行時間基礎結構，但不適合直接從程式碼使用的其他類型。|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性和 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 介面，您可以用來快取檔層級自訂中的資料物件。 如需詳細資訊，請參閱快取[資料](caching-data.md)。<br />-Visual Studio Tools for Office 執行時間可以擲回的例外狀況。<br />-屬於 Visual Studio Tools for Office 執行時間基礎結構，但不適合直接從程式碼使用的其他類型。|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|提供 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 介面，您可以實作這個介面來執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[Advanced Office solution deployment](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100))。|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|提供下列類型：<br /><br /> -<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別，您可以用來以程式設計方式將自訂群組件附加至檔，並存取檔中的快取資料。 如需詳細資訊，請參閱[使用 ServerDocument 類別管理伺服器上的檔](managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-數個類別，代表檔層級自訂中快取資料的階層。 如需詳細資訊，請參閱在[伺服器上存取檔中的資料](accessing-data-in-documents-on-the-server.md)。|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|提供下列類型：<br /><br /> -VisualStudio，您可以使用 AddInSecurityEntry 和 VisualStudio 類別來建立使用者內含清單專案，以授與信任給 Office 的許可權，並將其授與給 Office以 .NET Framework 3.5 為目標的解決方案。<br />-屬於 Visual Studio Tools for Office 執行時間基礎結構，但不適合直接從程式碼使用的其他類型。|

## <a name="see-also"></a>請參閱
- [Visual Studio Tools for Office 執行時間總覽](visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools for Office 執行時間安裝案例](visual-studio-tools-for-office-runtime-installation-scenarios.md)

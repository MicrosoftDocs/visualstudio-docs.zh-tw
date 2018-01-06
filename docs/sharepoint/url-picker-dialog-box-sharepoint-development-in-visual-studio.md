---
title: "URL 選擇器對話方塊 （Visual Studio 中的 SharePoint 程式開發） |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
ms.assetid: 33f8f521-e1f8-4242-a580-8a4bd9cb5ddc
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: c475b44b15b206464e2a910cc410964906706bd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL 選擇器對話方塊 (Visual Studio 中的 SharePoint 開發)
  在 [URL 選擇器] 對話方塊中，您可以選擇位於您的專案中或執行 SharePoint 的本機伺服器中的檔案，例如主版頁面檔案或影像檔。  
  
 如果有可供您選擇檔案以設定屬性的選項，這個對話方塊就會出現。 您可以開啟此對話方塊中，選擇省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 中的各種屬性旁邊**屬性**視窗。 省略符號按鈕時也會顯示為 IntelliSense 提示您將值指派給特定屬性中**來源**設計工具的檢視。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **專案資料夾**  
 顯示專案中或執行 SharePoint 的本機伺服器上定義的資料夾清單。 選擇展開按鈕顯示子資料夾。  
  
 展開**專案**節點，選擇您的專案中的檔案。 若要顯示為可選取在對話方塊中，您的專案中的檔案必須符合下列準則：  
  
-   檔案必須包含在對應的資料夾。  
  
-   將檔案必須加入至方案套件。  
  
-   在另一個專案中找不到檔案。  
  
 如果您想要參考不符合這些準則的檔案，您必須手動輸入檔案的路徑。  
  
 展開**伺服器**節點，選擇執行 SharePoint 的本機伺服器上的檔案。 若要顯示為可選取在對話方塊中，這些檔案必須符合下列準則：  
  
-   檔案必須位於下列對應的資料夾中的一個：**映像**，**配置**，或**ControlTemplates**。  
  
-   在 SharePoint 內容資料庫中找不到檔案。  
  
 如果您想要參考不符合這些準則的檔案，您必須手動輸入檔案的路徑。  
  
 **資料夾的內容**  
 顯示所選資料夾中的檔案清單。 選擇檔案、，然後選擇**確定**按鈕以關閉對話方塊，並將您選擇傳送至呼叫它的處理序。  
  
 **檔案類型**  
 可讓您選擇您正執行的工作所適用之檔案的清單。  
  
## <a name="see-also"></a>請參閱  
 [建立 SharePoint 應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [建立 SharePoint Web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [為 Web 組件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
  
  
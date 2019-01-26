---
title: URL 選擇器對話方塊 （Visual Studio 中的 SharePoint 程式開發） |Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.VWD.URLPicker
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, URL picker
- SharePoint development in Visual Studio, designer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbb0c682f478ca7a950cb4d5c1ef88eeee98731a
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870749"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL 選擇器對話方塊 （Visual Studio 中的 SharePoint 程式開發）
  在 [URL 選擇器] 對話方塊中，您可以選擇位於您的專案中或執行 SharePoint 的本機伺服器中的檔案，例如主版頁面檔案或影像檔。  
  
 如果有可供您選擇檔案以設定屬性的選項，這個對話方塊就會出現。 您可以開啟這個對話方塊中，選擇省略符號按鈕 (![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 中的各種屬性旁邊**屬性**  視窗。 省略符號按鈕也會顯示為 IntelliSense 提示時，您將值指派給特定的屬性，在**來源**設計工具的檢視。  
  
## <a name="uielement-list"></a>UIElement 清單
 **專案資料夾**  
 顯示專案中或執行 SharePoint 的本機伺服器上定義的資料夾清單。 選擇展開按鈕顯示子資料夾。  
  
 依序展開**專案**節點，選擇您的專案中的檔案。 在對話方塊中，都會顯示為可選取，您的專案中的檔案必須符合下列準則：  
  
- 檔案必須包含在對應的資料夾。  
  
- 檔案必須新增至方案套件。  
  
- 在另一個專案中找不到檔案。  
  
  如果您想要參考不符合這些準則的檔案，您必須以手動方式輸入檔案的路徑。  
  
  依序展開**Server**節點，選擇位於本機執行 SharePoint 的伺服器的檔案。 若出現可選取在對話方塊中，這些檔案必須符合下列準則：  
  
- 檔案必須位於下列的對應資料夾中的一個：**映像**，**版面配置**，或**ControlTemplates**。  
  
- 在 SharePoint 內容資料庫中找不到檔案。  
  
  如果您想要參考不符合這些準則的檔案，您必須以手動方式輸入檔案的路徑。  
  
  **資料夾的內容**  
  顯示所選資料夾中的檔案清單。 選擇檔案，然後選擇**確定**按鈕以關閉對話方塊，並將您選擇傳送至呼叫它的處理序。  
  
  **檔案類型**  
  可讓您選擇您正執行的工作所適用之檔案的清單。  
  
## <a name="see-also"></a>另請參閱
 [建立 SharePoint 相關應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [建立 SharePoint web 組件](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [建立可重複使用的控制項，為 web 組件或應用程式頁面](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   

---
title: " (SharePoint 開發) 的 URL 選擇器對話方塊"
description: 深入瞭解 [URL 選擇器] 對話方塊，可讓使用者選擇位於其專案中或執行 SharePoint 之本機伺服器上的檔案。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d04857f0e61e5d9f293d73902cd090f718c65cd0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892212"
---
# <a name="url-picker-dialog-box-sharepoint-development-in-visual-studio"></a>URL 選擇器對話方塊 (Visual Studio 中的 SharePoint 開發) 
  在 [URL 選擇器] 對話方塊中，您可以選擇位於您的專案中或執行 SharePoint 的本機伺服器中的檔案，例如主版頁面檔案或影像檔。

 如果有可供您選擇檔案以設定屬性的選項，這個對話方塊就會出現。 您可以在 [**屬性**] 視窗中的各種屬性旁，選擇省略號按鈕 (![ASP.NET 行動設計工具橢圓形](../sharepoint/media/mwellipsis.gif "ASP.NET Mobile 設計工具橢圓形")) 來開啟此對話方塊。 當您在設計工具的 [ **來源** ] 視圖中指派值給特定屬性時，省略號按鈕也會顯示為 IntelliSense 提示。

## <a name="uielement-list"></a>UIElement 清單
 **專案資料夾** 顯示專案中或執行 SharePoint 的本機伺服器上所定義的資料夾清單。 選擇展開按鈕顯示子資料夾。

 展開 **專案** 節點以選擇您專案中的檔案。 您專案中的檔案必須符合下列準則，才能在對話方塊中顯示為可選取：

- 檔案必須包含在對應的資料夾中。

- 必須將檔案新增至方案套件。

- 在另一個專案中找不到該檔案。

  如果您想要參考不符合這些準則的檔案，您必須手動輸入檔案的路徑。

  展開 [ **伺服器** ] 節點，選擇位於執行 SharePoint 之本機伺服器上的檔案。 若要在對話方塊中顯示為可選取，這些檔案必須符合下列準則：

- 檔案必須位於下列其中一個對應的資料夾中： **影像**、 **版面** 配置或 **ControlTemplates**。

- 在 SharePoint 內容資料庫中找不到該檔案。

  如果您想要參考不符合這些準則的檔案，您必須手動輸入檔案的路徑。

  **資料夾的內容** 顯示所選資料夾中的檔案清單。 選擇檔案，然後選擇 [ **確定** ] 按鈕以關閉對話方塊，並將您的選取專案傳送至呼叫它的進程。

  **檔案類型** 可讓您從適用于您正在執行之工作的檔案清單中進行選擇。

## <a name="see-also"></a>另請參閱
- [建立 SharePoint 的應用程式頁面](../sharepoint/creating-application-pages-for-sharepoint.md)
- [建立 SharePoint 的網頁元件](../sharepoint/creating-web-parts-for-sharepoint.md)
- [為 web 元件或應用程式頁面建立可重複使用的控制項](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

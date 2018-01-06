---
title: "取得字型和色彩資訊文字的顏色標示 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: "22"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97b97b6a79ac93dd614cf6557d338d5f0398192e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>取得字型和色彩資訊文字的顏色標示
呈現或彩色的文字顯示在使用者介面 (UI) 項目中的程序取決於專案、 技術和開發人員的喜好設定的類型。 **字型和色彩**屬性頁儲存設定。  
  
 需要顯示彩色的文字的大部分實作`T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults`和相關聯的呈現、 擷取和儲存文字顯示設定的介面。  
  
> [!NOTE]
>  自訂核心編輯器時 (其支援**文字 EditorCategory**)，強烈建議您使用的語言服務中的著色技術。 如需詳細資訊，請參閱[字型和色彩概觀](../extensibility/font-and-color-overview.md)。  
  
## <a name="getting-default-font-and-color-information"></a>取得預設字型和色彩資訊  
 所有**字型和色彩**應該中指定的任何視窗，以顯示文字的設定**顯示項目**其中**類別**。 如需詳細資訊，請參閱[字型和色彩、 環境、 選項對話方塊](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)。  
  
 若要以色彩標示，VSPackage 必須取得目前**字型和色彩**設定。 VSPackage 可以完成這項作業以下列方式，視其需求而定：  
  
-   您可以使用的字型和色彩的持續性機制來擷取預存] 或 [目前狀態。 如需詳細資訊，請參閱[存取儲存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)。  
  
-   使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面的服務，提供要取得的執行個體的字型和色彩資料<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>，如果 VSPackage 也不是字型和色彩提供者。  
  
-   實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 介面。  
  
 為了確保取得輪詢結果的最新狀態，可能很有用使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>介面，以判斷更新是否需要在呼叫的方法擷取之前<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>介面。  
  
 取得字型和色彩資訊之後剖析文字，以顯示以識別需要顏色標示的項目，然後使用適當的字型和色彩 視窗中顯示文字。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [使用字型和文字](/dotnet/framework/winforms/advanced/using-fonts-and-text)   
 [使用色彩](/cpp/windows/working-with-color-image-editor-for-icons)   
 [GDI （圖形裝置介面）](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)
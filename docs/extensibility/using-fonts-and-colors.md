---
title: "使用字型和色彩 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce64c7cac36319d1e55efb0ddf2216dc218805c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2017
---
# <a name="using-fonts-and-colors"></a>使用字型和色彩
[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]支援使用顯示文字的字型和色彩。  
  
## <a name="in-this-section"></a>本章節內容  
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)  
 討論中的文字字型和色彩設定[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 也介紹的概念分類和顯示項目，並說明如何 Vspackage 和核心編輯器使用 文字屬性。  
  
 [取得字型和色彩資訊文字的顏色標示](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 提供的指導方針中管理的 Vspackage 實作文字的顏色標示**類別**以外**文字編輯器**。  
  
 [存取預存的字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)  
 說明如何在目前的字型和色彩設定可儲存、 擷取及套用。  
  
 [實作自訂的分類和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)  
 描述的基本步驟，藉以視窗可以建立並使用它自己的**顯示項目**和**類別**支援文字顯示。  
  
 這個方法會要求實作 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面和相關的介面。  
  
 [如何： 存取的內建的字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 討論如何定義和使用內建的字型和色彩、 註冊一個分類，並起始使用系統提供的字型和色彩。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 提供的執行個體`IVsFontAndColorDefaults`或<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>對應至特定項目中所列的介面**顯示設定為**清單中**字型和色彩**頁面**選項** 對話方塊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 可讓 VSPackage 也可以支援 IDE**字型和色彩**藉由定義預設字型和色彩 視窗或 UI 元件的頁面。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 提供一個機制，藉以提供字型和色彩的支援，可以指定顯示項目群組-超級類別，表示兩個或多個類別的聯集的 VSPackage。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 可讓 VSPackage 也可以擷取字型和色彩的資料，或將它儲存至登錄。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 告知 Vspackage 使用字型和色彩設定中變更的字型和色彩資訊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 提供的工具使用的方法使用輸入和輸出資料[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**字型和色彩**機制。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 控制字型和色彩設定的快取。  
  
## <a name="related-sections"></a>相關章節  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 討論 Vspackage 如何使用語言服務來自訂[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]編輯器。  
  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 如何[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]編輯器所使用語言服務實作的語法著色。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]服務建立符合的其餘部分的 UI 項目[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。
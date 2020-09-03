---
title: 使用字型和色彩 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177233"
---
# <a name="using-fonts-and-colors"></a>使用字型和色彩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]提供使用字型和色彩來顯示文字的支援。  
  
## <a name="in-this-section"></a>本節內容  
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)  
 討論 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (IDE) 整合式開發環境中的文字字型和色彩設定。 也介紹類別和顯示專案的概念，並說明 Vspackage 和核心編輯器如何使用文字屬性。  
  
 [取得顏色標示的字型和色彩資訊](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 提供在 Vspackage 中執行文字顏色標示的指導方針，以管理**文字編輯器**以外的**類別**。  
  
 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)  
 說明如何儲存、取出及套用目前的字型和色彩設定。  
  
 [實作自訂類別和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)  
 描述視窗可以建立的基本步驟，並使用自己的 **顯示專案** 和 **分類** 來支援文字顯示。  
  
 這種方法需要 VSPackage 來執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> 介面和相關的介面。  
  
 [如何：存取內建字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 討論如何使用內建字型和色彩來定義及註冊類別，以及起始系統提供的字型和色彩的使用。  
  
## <a name="reference"></a>參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 提供的實例， `IVsFontAndColorDefaults` 或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> 對應至 [**選項**] 對話方塊之 [字型**和色彩**] 頁面的 [**顯示設定**] 清單中所列特定專案的介面。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 藉由定義視窗或 UI 元件的預設字型和色彩，讓 VSPackage 支援 IDE 字型 **和色彩** 頁面。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 提供一種機制，可讓提供字型和色彩支援的 VSPackage 指定顯示專案群組，也就是代表兩個或多個類別聯集的超級類別。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 讓 VSPackage 取得字型和色彩資料，或將其儲存至登錄。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 使用字型和色彩設定中的變更，通知 Vspackage 使用字型和色彩資訊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 提供工具來處理 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **字型和色彩** 機制的方法所使用的輸入和輸出資料。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 控制字型和色彩設定的快取。  
  
## <a name="related-sections"></a>相關章節  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 討論 Vspackage 可以如何使用語言服務自訂 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 編輯器。  
  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 編輯器如何 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 使用語言服務來執行語法著色。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 服務建立 UI 項目，比對其餘的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68177233"
---
# <a name="using-fonts-and-colors"></a>使用字型和色彩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]支援使用顯示文字的字型和色彩。  
  
## <a name="in-this-section"></a>本節內容  
 [字型和色彩概觀](../extensibility/font-and-color-overview.md)  
 討論中的文字字型和色彩設定[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]整合式的開發環境 (IDE)。 也介紹的概念的類別和 顯示項目，並說明如何在 Vspackage 和核心編輯器使用文字屬性。  
  
 [取得顏色標示的字型和色彩資訊](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 提供的指導方針在管理的 Vspackage 中實作文字顏色標示**分類**以外**文字編輯器**。  
  
 [存取預存字型和色彩設定](../extensibility/accessing-stored-font-and-color-settings.md)  
 說明如何在目前的字型和色彩設定可儲存、 擷取及套用。  
  
 [實作自訂類別和顯示項目](../extensibility/implementing-custom-categories-and-display-items.md)  
 描述視窗可供建立，並使用它自己的基本步驟**顯示的項目**並**類別**來支援文字顯示。  
  
 此方法需要實作 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>介面和相關的介面。  
  
 [如何：存取內建字型和色彩配置](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 討論如何定義並使用內建的字型和色彩，來註冊類別並起始使用系統提供的字型和色彩。  
  
## <a name="reference"></a>參考資料  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 提供的執行個體`IVsFontAndColorDefaults`或<xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>對應至特定項目中所列的介面**顯示設定為**清單中**字型和色彩**頁面**選項** 對話方塊。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 可讓 VSPackage 也可以支援 IDE**字型和色彩**頁面所定義之視窗或 UI 元件預設字型和色彩。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 提供一個機制，用 VSPackage 提供 字型和色彩支援可以指定顯示項目群組-超級類別，表示兩個或多個類別的聯集。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 可讓 VSPackage 也可以擷取字型和色彩的資料，或將它儲存至登錄。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 通知使用的字型和色彩設定中變更的字型和色彩資訊的 Vspackage。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 提供的工具使用的輸入和輸出資料所使用的方法[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**字型和色彩**機制。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 控制字型和色彩設定的快取。  
  
## <a name="related-sections"></a>相關章節  
 [開發舊版語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 討論 Vspackage 如何使用語言服務，自訂[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]編輯器。  
  
 [自訂編輯器中的語法著色](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries 如何[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]編輯器使用的語言服務來實作語法著色。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何使用 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 服務建立 UI 項目，比對其餘的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]。

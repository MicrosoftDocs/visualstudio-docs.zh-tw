---
title: 字符控制 (原始檔控制 VSPackage) |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 820ffdd2578cc40f91d95bb489f13403c5cdecc5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772348"
---
# <a name="glyph-control-source-control-vspackage"></a>字符控制 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

加入原始檔控制 Vspackage 提供的深入整合的一部分是能夠顯示自己的字符，以指出原始檔控制下的項目狀態。  
  
## <a name="levels-of-glyph-control"></a>字符控制層級  
 狀態的圖像 （glyph） 是以圖示表示的項目時顯示，如範例中的目前狀態**方案總管**或是在**類別檢視**。 原始檔控制 VSPackage 可以訓練字符控制的兩個層的級。 它可以限制的一組預先定義的圖像 （glyph） 所提供的圖像選擇[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE，也可以定義一組自訂的字符才能顯示。  
  
### <a name="default-set-of-glyphs"></a>一組預設的圖像 （glyph）  
 若要判斷與中的項目相關聯的狀態字符**方案總管**，專案會從原始檔控制使用要求狀態圖像 （glyph） <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>。 原始檔控制 VSPackage 可能會決定要保留的限制為預先定義的圖像 （glyph） IDE 所提供的圖像 （glyph） 的選擇。 在此情況下，VSPackage 回傳遞值，表示 vsshell.idl 中所定義的圖像 （glyph） 列舉型別的陣列。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>。這是一組預先定義設定的 IDE，例如 [簽入] 圖像 （glyph），和為 [已取出] 字符的核取記號掛鎖的圖像 （glyph）。  
  
### <a name="custom-set-of-glyphs"></a>自訂設定的圖像 （glyph）  
 原始檔控制 VSPackage 在安裝時，可以使用自己圖像 （glyph） 的唯一 「 外觀與風格 」。 使用新的原始檔控制 VSPackage 時，它應該能夠開始使用它自己的字符即使上一個原始檔控制 VSPackage 仍載入而非使用中。 在此模式中，原始檔控制 VSPackage 仍然可以使用現有的圖示維持一致的外觀[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]如果選擇。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服務支援的介面中， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>，而此 VSPackage 可以選擇性地實作，並在其中將會要求由 IDE。 當 IDE 發出要求，[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]接著會嘗試從目前已註冊的原始檔控制 VSPackage 取得這個介面。 如果介面都存在於已註冊的 VSPackage，自訂圖像的 IDE 的要求將會成功;否則， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 使用其預設組圖像 （glyph）。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>方法由[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]若要取得一份圖像： 顯示各種原始檔控制狀態。 原始檔控制 VSPackage IDE 傳回其自訂圖像 （glyph） 的映像清單的控制代碼。 IDE 在此時會建立一份映像清單，並稍後使用它來選擇字符才能顯示。 如果不支援新的介面或`IVsSccGlyphs::GetCustomGlyphList`方法會傳回 E_NOTIMPL，則 IDE 會從所提供的圖像 （glyph） 的預設清單取得其圖像 （glyph） [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>


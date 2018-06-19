---
title: 字符控制項 (原始檔控制 VSPackage) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c3787b0afad7f89743950a922d5b19c2d204bdd9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130712"
---
# <a name="glyph-control-source-control-vspackage"></a>字符控制項 (原始檔控制 VSPackage)
加入原始檔控制 Vspackage 可用的深度整合的一部分是能夠顯示自己圖像來表示的原始檔控制下的項目狀態。  
  
## <a name="levels-of-glyph-control"></a>層級的圖像 （glyph） 控制  
 狀態字符會指出項目時顯示，如範例中的目前狀態的圖示**方案總管 中**或**類別檢視**。 原始檔控制 VSPackage 可以執行兩個層級的圖像 （glyph） 控制。 它可以限制，這些圖像會一組預先定義圖像 （glyph） 所提供的選擇[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE，也可以定義一組自訂的字符才能顯示。  
  
### <a name="default-set-of-glyphs"></a>預設圖像 （glyph） 集合  
 若要判斷與中的項目相關聯的狀態圖像**方案總管 中**，專案會從原始檔控制使用要求狀態字符<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>。 原始檔控制 VSPackage 可能會決定要保留的選擇限制為 IDE 所提供預先定義圖像 （glyph） 的圖像 （glyph）。 在此情況下，VSPackage 傳遞回代表 vsshell.idl 中所定義的圖像 （glyph） 列舉值的陣列。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>。這是一組預先定義設定的 IDE，例如 「 簽入 」 字符，和核取標記為 [已取出] 圖像鎖頭的圖像 （glyph）。  
  
### <a name="custom-set-of-glyphs"></a>自訂圖像 （glyph） 集合  
 原始檔控制 VSPackage 可以使用它自己的圖像 （glyph） 唯一 」 外觀及操作 「 安裝時。 使用新的原始檔控制 VSPackage 時，它應該能夠使用自己的圖像即使前一個原始檔控制 VSPackage 仍載入而非使用中。 在此模式中，原始檔控制 VSPackage 仍然可以使用現有的圖示以維護與一致的外觀[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果選擇。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>服務支援介面， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>，而此 VSPackage 可以選擇性地實作，這會要求提供 ide。 當提出要求時，IDE 時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]接著會嘗試從目前已註冊的原始檔控制 VSPackage 取得此介面。 如果介面存在於已註冊的 VSPackage，自訂圖像的 IDE 的要求將會成功;否則， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 使用其預設圖像 （glyph）。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>方法由[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]若要取得一份映像顯示各種原始檔控制狀態。 原始檔控制 VSPackage IDE 傳回其自訂圖像的影像清單控制代碼。 IDE 此時會建立一份影像清單，並稍後再使用它來選擇要顯示的圖像。 如果不支援新的介面或`IVsSccGlyphs::GetCustomGlyphList`方法會傳回 E_NOTIMPL，則 IDE 圖像 （glyph） 所提供的預設清單中取得其圖像[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>
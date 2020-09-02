---
title: 字元控制項 (原始檔控制 VSPackage) |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b0960209b67c8d2f111296840119807d95bb2e2d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538417"
---
# <a name="glyph-control-source-control-vspackage"></a>字符控制 (原始檔控制 VSPackage)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

可供原始檔控制 Vspackage 使用的深層整合有一部分，就是能夠顯示自己的字元來指出原始檔控制下的專案狀態。  
  
## <a name="levels-of-glyph-control"></a>字型控制項的層級  
 狀態圖像是一個圖示，指出專案在顯示時的目前狀態（例如，在 **方案總管** 或 **類別檢視**中）。 原始檔控制 VSPackage 可以執行兩個層級的字元控制項。 它可以將字元選擇限制為 IDE 所提供的一組預先定義的字元 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ，也可以定義一組要顯示的自訂圖像。  
  
### <a name="default-set-of-glyphs"></a>預設的一組字元  
 若要判斷與 **方案總管**中的專案相關聯的狀態圖像，專案會使用從原始檔控制要求狀態圖像 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> 。 原始檔控制 VSPackage 可能會決定要讓選擇的字元限制為 IDE 所提供的預先定義圖像。 在此情況下，VSPackage 會傳回值陣列，這些值代表 vsshell 中定義的圖像列舉。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon> 。這是 IDE 所設定的一組預先定義的圖像，例如「已簽入」圖像的掛鎖，以及「簽出」圖像的核取記號。  
  
### <a name="custom-set-of-glyphs"></a>自訂的一組字元  
 原始檔控制 VSPackage 在安裝時，可以使用自己的字元來提供獨特的「外觀與風格」。 當新的原始檔控制 VSPackage 為作用中時，即使先前的原始檔控制 VSPackage 仍處於非使用中狀態，也應該能夠開始使用自己的圖像。 在此模式中，原始檔控制 VSPackage 仍然可以使用現有的圖示，以保持與選擇一致的外觀 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
 此 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 服務支援介面， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> 此介面可讓 VSPackage 選擇性地執行，而 IDE 將會要求您這樣做。 當 IDE 提出要求時， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 接著會嘗試從目前註冊的原始檔控制 VSPackage 取得這個介面。 如果介面存在於已註冊的 VSPackage 中，IDE 的自訂字元要求便會成功;否則， [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE 會使用其預設的字元組。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>使用方法 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 來取得顯示各種原始檔控制狀態的影像清單。 原始檔控制 VSPackage 會將影像清單的控制碼傳回至 IDE，以作為其自訂字元。 IDE 會在此時建立影像清單的複本，並在稍後用它來選擇要顯示的圖像。 如果不支援新的介面 `IVsSccGlyphs::GetCustomGlyphList` ，或方法傳回 E_NOTIMPL，則 IDE 會從所提供的預設圖像清單中取得其圖像 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

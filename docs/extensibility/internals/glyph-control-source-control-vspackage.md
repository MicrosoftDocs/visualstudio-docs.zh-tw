---
title: 字元控制項 (原始檔控制 VSPackage) |Microsoft Docs
description: 瞭解如何在原始檔控制 VSPackage 中顯示自訂字元，讓您可以使用自己的圖示來指出原始檔控制下的專案狀態。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glyphs, source control packages
- source control packages, glyphs
ms.assetid: b9413b08-b3c3-4fc3-a6e0-3dc0db3652d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eaf7f40224e2f197627bb995dc6cccdf297b46e5
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480469"
---
# <a name="glyph-control-source-control-vspackage"></a>字元控制項 (原始檔控制 VSPackage) 
可供原始檔控制 Vspackage 使用的深層整合有一部分，就是能夠顯示自己的字元來指出原始檔控制下的專案狀態。

## <a name="levels-of-glyph-control"></a>字型控制項的層級
 狀態圖像是一個圖示，指出專案在顯示時的目前狀態（例如，在 **方案總管** 或 **類別檢視** 中）。 原始檔控制 VSPackage 可以執行兩個層級的字元控制項。 它可以將字元選擇限制為 IDE 所提供的一組預先定義的字元 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，也可以定義一組要顯示的自訂圖像。

### <a name="default-set-of-glyphs"></a>預設的一組字元
 若要判斷與 **方案總管** 中的專案相關聯的狀態圖像，專案會使用從原始檔控制要求狀態圖像 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A> 。 原始檔控制 VSPackage 可能會決定要讓選擇的字元限制為 IDE 所提供的預先定義圖像。 在此情況下，VSPackage 會傳回值陣列，這些值代表 *vsshell* 中定義的圖像列舉。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>。 這是 IDE 所設定的一組預先定義的字元，例如已簽入圖像的掛鎖，以及簽出圖像的核取記號。

### <a name="custom-set-of-glyphs"></a>自訂的一組字元
 原始檔控制 VSPackage 可以在安裝時，使用自己的圖像來取得獨特的外觀和風格。 當新的原始檔控制 VSPackage 為作用中時，即使先前的原始檔控制 VSPackage 仍處於非使用中狀態，也應該能夠開始使用自己的圖像。 在此模式中，原始檔控制 VSPackage 仍然可以使用現有的圖示，以保持與選擇一致的外觀 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

 此 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> 服務支援介面， <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs> 此介面可讓 VSPackage 選擇性地執行，而 IDE 將會要求您這樣做。 當 IDE 提出要求時， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 接著會嘗試從目前註冊的原始檔控制 VSPackage 取得這個介面。 如果介面存在於已註冊的 VSPackage 中，IDE 的自訂字元要求便會成功;否則， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE 會使用其預設的字元組。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>使用方法 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 來取得顯示各種原始檔控制狀態的影像清單。 原始檔控制 VSPackage 會將影像清單的控制碼傳回至 IDE，以作為其自訂字元。 IDE 會在此時建立影像清單的複本，並在稍後用它來選擇要顯示的圖像。 如果不支援新的介面或方法傳回 `IVsSccGlyphs::GetCustomGlyphList` ，則 `E_NOTIMPL` IDE 會從所提供的圖像的預設清單中取得其字型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

---
title: 字形控制(來源 VS 套件) :微軟文件
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
ms.openlocfilehash: 9db1b4542eae293e39cda674fac3eb984aa77d3e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708324"
---
# <a name="glyph-control-source-control-vspackage"></a>字形控制 (來源)
原始碼管理 VSPackages 可用於的深度整合的一部分是能夠顯示自己的字形來指示原始程式碼管理下的項的狀態。

## <a name="levels-of-glyph-control"></a>字形控制等級
 狀態字形是顯示項目時指示項目目前狀態的圖示,例如在**解決方案資源管理器**或**類別檢視中**。 原始碼管理 VSPackage 可以執行兩個級別的字形控制。 它可以將字形的選擇限制為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 提供的預定義的字形集,也可以定義要顯示的自訂字形集。

### <a name="default-set-of-glyphs"></a>預設字形集
 要確定與**解決方案資源管理員**中的項目的狀態字形,專案使用 要求來源控制項中的狀態字<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.GetSccGlyph%2A>形 。 原始碼管理 VSPackage 可能決定將字形的選擇限制為 IDE 提供的預定義字形。 在這種情況下,VSPackage 傳遞一個值陣列,表示在*vsshell.idl*中定義的字形枚舉。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>。 這是由 IDE 設置的預定義字形集,例如已簽入字形的掛鎖和簽出字形的複選標記。

### <a name="custom-set-of-glyphs"></a>自訂字形集
 原始碼管理 VSPackage 在安裝時可以使用自己的字形來提供獨特的外觀。 當新的原始碼管理 VSPackage 處於活動狀態時,它應該能夠開始使用自己的字形,即使以前的原始程式碼管理 VSPackage 仍然載入但不活動。 在此模式下,原始程式碼管理 VSPackage 仍可以使用現有圖示,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]以便在選擇 時保持與外觀一致的外觀。

 該服務<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>支援一個介面,VS<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>包可以選擇實現該介面,IDE 會要求該介面。 當 IDE 發出[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]請求時 ,將嘗試從當前註冊的原始程式碼管理 VSPackage 獲取此介面。 如果介面存在於已註冊的 VSPackage 中,則 IDE 的自定義字形請求將成功;如果該介面位於已註冊的 VSPackage 中,則 IDE 對自定義字形的請求將成功;否則,IDE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]將使用其預設的字形集。

 該方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs.GetCustomGlyphList%2A>[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]用於獲取顯示各種原始程式碼管理狀態的影像清單。 源控件 VSPackage 將自定義字形的句柄返回到映射清單的句柄。 IDE 此時會複製圖像清單,然後使用它選擇要顯示的字形。 如果不支援新介面或`IVsSccGlyphs::GetCustomGlyphList`該方法`E_NOTIMPL`返回 ,則 IDE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]將從 提供的 字形的默認清單中獲取其字形。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccGlyphs>
- <xref:Microsoft.VisualStudio.Shell.Interop.VsStateIcon>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

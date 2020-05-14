---
title: 為 VS 套件選擇安裝目錄 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, installation directory
ms.assetid: 01fbbb5b-f747-446c-afe0-2a081626a945
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8391cbdd3a857ea4ebaf3a36655520935f1a128
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709767"
---
# <a name="choose-the-installation-directory-for-a-vspackage"></a>選擇 VSPackage 的安裝目錄
VSPackage 及其支援文件必須位於使用者的檔案系統上。 位置取決於 VSPackage 是託管還是非託管、並行版本控制方案和用戶選擇。

## <a name="unmanaged-vspackages"></a>非託管 VS 套件
 非託管 VSPackage 是可在任何位置安裝的 COM 伺服器。 其註冊信息必須準確反映其位置。 安裝程式使用者介面 (UI) 應提供預設位置作為 Windows`ProgramFilesFolder`安裝程式屬性值 的子目錄。 例如：

*&lt;程式檔案資料夾&gt;\\&lt;我的&gt;\\&lt;公司 MyVS&gt;包產品 #V1.0\\*

 應允許使用者更改預設目錄,以適應保留小型引導分區並更願意在另一卷上安裝應用程式和工具的使用者。

 如果並行方案使用版本化 VSPackage,則可以使用子目錄來存儲不同的版本。 例如：

 *&lt;程式檔案資料夾&gt;\\&lt;我的&gt;\\&lt;公司&gt;\\MyVS 套件產品\\V1.0 2002\\*

 *&lt;程式檔案資料夾&gt;\\&lt;我的&gt;\\&lt;公司&gt;\\MyVS 套件產品\\V1.0 2003\\*

 *&lt;程式檔案資料夾&gt;\\&lt;我的&gt;\\&lt;公司&gt;\\MyVS 套件產品\\V1.0 2005\\*

## <a name="managed-vspackages"></a>Managed VSPackage
 託管 VS 套件也可以安裝在任何位置。 但是,應考慮始終將它們安裝到全域程式集緩存 (GAC) 以縮短程式集載入時間。 由於託管 VSPackages 始終是強名稱程式集,因此在 GAC 中安裝它們意味著其強名稱簽名驗證僅在安裝時才需要。 檔案系統中其他位置安裝的強命名程式集必須在每次載入時驗證其簽名。 在 GAC 中安裝託管 VSPackages 時,請使用 regpkg 工具的 **/程式集**開關寫入指向程式集的強名稱的註冊表項。

 如果在 GAC 以外的位置安裝託管 VS 包,請按照前面為非託管 VSPackages 提供的建議來選擇目錄層次結構。 使用 regpkg 工具的 **/codebase**開關編寫指向 VSPackage 程式集路徑的註冊表項。

 有關詳細資訊,請參閱[註冊和取消註冊 VS 包](../../extensibility/registering-and-unregistering-vspackages.md)。

## <a name="satellite-dlls"></a>附屬 DLL
 按照慣例,包含特定區域設置資源的 VSPackage 衛星 DLL 位於*VSPackage*目錄的子目錄中。 子目錄對應於區域設置 ID (LCID) 值。

 ["管理 VSPackages"](../../extensibility/managing-vspackages.md)一文指示註冊[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]表項 控制實際查找 VSPackage 的衛星 DLL 的位置。 但是,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]嘗試按以下順序在名為 LCID 值的子目錄中載入衛星 DLL:

1. 預設 LCID(視覺工作室 LCID;例如,英語 *#1033)*

2. 預設 LCID 與預設子語言。

3. 系統預設 LCID。

4. 系統預設 LCID 與預設子語言。

5. 美國英語 *(.1033*或 *.\0x409*)。

如果您的 VSPackage DLL 包含**SatelliteDll\DllName**資源,並且 SatelliteDll_DllName[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]註冊表條目 指向它,則嘗試按上述順序載入它們。

## <a name="see-also"></a>另請參閱
- [在分享與版本化 VS 套件之間進行選擇](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)
- [管理 VSPackages](../../extensibility/managing-vspackages.md)
- [管理包註冊](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)

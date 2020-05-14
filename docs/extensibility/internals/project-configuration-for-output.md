---
title: 輸出項目設定 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706662"
---
# <a name="project-configuration-for-output"></a>輸出的專案組態
每個配置都可以支援一組生成進程,這些生成進程生成輸出項(如可執行檔或資源檔)。 這些輸出項是使用者專用的,可以放置在連結相關輸出類型的組中,如可執行檔(.exe、.dll、.lib)和源檔(.idl、.h 檔)。

 輸出項可以通過這些方法提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>,<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>並隨 這些方法枚舉。 如果要對輸出項目進行群組,專案還應實現介面<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>。

 通過實現`IVsOutputGroup`開發的構造允許項目根據使用方式對輸出進行分組。 例如,DLL 可能與其程式資料庫 (PDB) 進行分組。

> [!NOTE]
> PDB 檔包含除錯資訊,並在生成 .dll 或 .exe 時指定"生成除錯資訊"選項時創建該檔。 .pdb 檔通常僅用於除錯專案配置。

 項目必須為其支援的每個配置返回相同數量的組,即使組中包含的輸出數可能因配置而異。 例如,專案 Matt 的 DLL 可能包括除錯配置中的 mattd.dll 和 mattd.pdb,但在零售配置中僅包括 matt.dll。

 從專案中的配置到配置,這些組還具有相同的標識符資訊,如規範名稱、顯示名稱和組資訊。 這種一致性允許部署和打包繼續運行,即使配置發生變化也是如此。

 組還可以具有密鑰輸出,允許打包快捷方式指向有意義的內容。 給定配置中的任何組可能為空,因此不應對組的大小進行假設。 任何配置中每個組的大小(輸出數)可能不同於同一配置中另一個組的大小。 它也可能與另一個配置中同一組的大小不同。

 ![輸出群組圖形](../../extensibility/internals/media/vsoutputgroups.gif "vs 輸出群組")輸出群組

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>介面的主要用途是提供生成、部署和調試管理物件的訪問,並允許專案自由分組輸出。 有關使用此介面的詳細資訊,請參考[專案設定物件](../../extensibility/internals/project-configuration-object.md)。

 在上圖中,Group Built 具有跨配置(bD.exe 或 b.exe)的關鍵輸出,因此使用者可以創建"已建"快捷方式,並且知道無論部署的配置如何,快捷方式都工作。 組源沒有金鑰輸出,因此使用者無法創建其快捷方式。 如果調試組"構建"具有密鑰輸出,但零售組生成沒有,則這將是不正確的實現。 因此,如果任何配置具有不包含輸出的組,因此沒有密鑰檔,則具有該組包含輸出的其他配置不能具有密鑰檔。 安裝程式編輯器假定規範名稱和組顯示名稱,加上密鑰檔的存在,不會根據配置進行更改。

 請注意,如果專案具有它不想`IVsOutputGroup`打包或部署的 a,則不將該輸出放在組中就足夠了。 通過實現返回配置的所有輸出<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>的方法,無論分組如何,仍可以正常枚舉輸出。

 有關詳細資訊,請參閱[專案 MPF](https://github.com/tunnelvisionlabs/MPFProj10)`IVsOutputGroup`的自定義專案示例中的實現。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
- [方案組態](../../extensibility/internals/solution-configuration.md)

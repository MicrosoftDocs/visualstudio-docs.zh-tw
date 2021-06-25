---
title: 輸出的專案設定 |Microsoft Docs
description: 瞭解每個設定可支援的組建程式，以及可供使用輸出專案的介面和方法。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b718e70bac0d9e09936daf743420acc04a1c4ad
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899871"
---
# <a name="project-configuration-for-output"></a>輸出的專案組態
每個設定都可以支援一組產生輸出專案的組建處理常式，例如可執行檔或資源檔。 這些輸出專案是使用者私用的，而且可以放在連結相關輸出類型的群組中，例如可執行檔 (.exe、.dll、.lib) 和原始程式檔 ( .idl、.h 檔案) 。

 輸出專案可透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> 方法提供，並以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> 方法列舉。 當您想要將輸出專案分組時，您的專案也應執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 介面。

 實作為實行所開發的結構 `IVsOutputGroup` ，可讓專案根據使用方式將輸出分組。 比方說，DLL 可能會以其程式資料庫 (PDB) 來分組。

> [!NOTE]
> PDB 檔案包含偵錯工具資訊，並且會在建立 .dll 或 .exe 時指定 [產生 Debug 資訊] 選項時建立。 .Pdb 檔案通常只會針對 Debug 專案設定產生。

 專案必須針對其所支援的每個設定傳回相同的群組數目，即使群組中包含的輸出數目可能會因設定而異。 例如，專案 Matt 的 DLL 可能會在 Debug 設定中包含 mattd.dll 和 mattd，但僅包含零售設定中的 matt.dll。

 這些群組也具有相同的識別碼資訊，例如正式名稱、顯示名稱和群組資訊，從設定到專案內的設定。 這種一致性可讓部署和封裝繼續運作，即使設定變更也一樣。

 群組也可以有允許封裝快捷方式的按鍵輸出，以指向有意義的內容。 任何群組在指定的設定中可能是空的，因此不應該對群組的大小進行任何假設。 在任何設定中，每個群組)  (的輸出數目，可能與相同設定中另一個群組的大小不同。 它也可以與另一個設定中相同群組的大小不同。

 ![輸出群組圖形](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") 輸出群組

 介面的主要用途 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> 是提供組建、部署和偵錯工具管理物件的存取權，並允許專案自由分組輸出。 如需使用此介面的詳細資訊，請參閱 [專案設定物件](../../extensibility/internals/project-configuration-object.md)。

 在上圖中，[建立群組] 具有橫跨設定的主要輸出 (bD.exe 或 b.exe) 讓使用者可以建立建立的快捷方式，並知道無論部署的設定為何，快速鍵都能運作。 群組來源沒有金鑰輸出，因此使用者無法建立其快捷方式。 如果建立的 Debug 群組具有金鑰輸出，但建立的零售群組不是，則這會是不正確的執行。 接下來，如果有任何設定沒有包含輸出的群組，且結果沒有金鑰檔，則其他具有包含輸出之群組的設定就不能有金鑰檔。 安裝程式編輯器會假設群組的標準名稱和顯示名稱，加上金鑰檔的存在，不會根據設定而變更。

 請注意，如果專案中有不 `IVsOutputGroup` 想要封裝或部署的專案，就足以將該輸出放在群組中。 您仍然可以藉由實會傳回所有設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> 輸出的方法（不論群組為何），正常地列舉輸出。

 如需詳細資訊，請參閱 `IVsOutputGroup` 在 [適用于專案的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)上自訂專案範例中的實作為。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
- [解決方案設定](../../extensibility/internals/solution-configuration.md)

---
title: 輸出的專案設定 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: addd7e8630ce35c6bdbbbb4c063197f75a74c97d
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300682"
---
# <a name="project-configuration-for-output"></a>輸出的專案組態
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

每個設定都可以支援一組會產生輸出專案（例如可執行檔或資源檔）的組建進程。 這些輸出專案是使用者的私用，而且可以放在連結相關輸出類型的群組中，例如可執行檔（.exe、.dll、.lib）和原始程式檔（.idl、.h 檔案）。  
  
 輸出專案可以透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> 方法提供，並使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> 方法進行列舉。 當您想要將輸出專案分組時，您的專案也應該會執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> 介面。  
  
 藉由執行 `IVsOutputGroup` 所開發的結構，可讓專案根據使用方式將輸出分組。 例如，DLL 可能會與其程式資料庫（PDB）群組在一起。  
  
> [!NOTE]
> PDB 檔案包含調試資訊，而且會在建立 .dll 或 .exe 時指定 [產生 Debug Info] 選項時建立。 .Pdb 檔案通常只會針對 Debug 專案設定而產生。  
  
 專案必須針對其支援的每個設定傳回相同的群組數目，即使群組中包含的輸出數目可能與設定不同。 例如，專案 Matt 的 DLL 可能會在 Debug 設定中包含 mattd 和 mattd，但僅包含零售設定中的 Matt。  
  
 這些群組也具有相同的識別碼資訊，例如標準名稱、顯示名稱和群組資訊（從設定到專案內的設定）。 這種一致性可讓部署和封裝繼續運作，即使設定變更也一樣。  
  
 群組也可以有金鑰輸出，以允許封裝快捷方式指向有意義的內容。 在指定的設定中，任何群組可能是空的，因此不應該對群組的大小進行任何假設。 任何設定中每個群組的大小（輸出數目）可能會與相同設定中另一個群組的大小不同。 它也可以與另一個設定中相同群組的大小不同。  
  
 ![輸出群組圖形](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
輸出群組  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> 介面的主要用途是提供組建、部署和調試層管理物件的存取權，並允許專案自由分組輸出。 如需使用此介面的詳細資訊，請參閱[專案設定物件](../../extensibility/internals/project-configuration-object.md)。  
  
 在上圖中，組建群組具有跨設定（cmd.exe 或 b. .exe）的按鍵輸出，因此使用者可以建立建立的快捷方式，並知道不論部署的設定為何，快捷方式都能正常執行。 群組來源沒有金鑰輸出，因此使用者無法建立其快捷方式。 如果建立的 Debug 群組具有金鑰輸出，但建立的零售群組不是，則會是不正確的執行。 接著，如果有任何設定的群組不包含任何輸出，因此沒有金鑰檔案，則包含該群組且含有輸出的其他設定不能有金鑰檔案。 安裝程式編輯器會假設群組的正式名稱和顯示名稱，加上金鑰檔的存在，並不會根據設定而變更。  
  
 請注意，如果專案有不想封裝或部署的 `IVsOutputGroup`，就足以將該輸出放在群組中。 您仍然可以藉由執行會傳回所有設定輸出的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> 方法（不論群組為何），正常地列舉輸出。  
  
 如需詳細資訊，請參閱在[適用于專案之 MPF](https://archive.codeplex.com/?p=mpfproj12)的自訂專案範例中執行 `IVsOutputGroup`。  
  
## <a name="see-also"></a>另請參閱  
 [管理設定選項](../../extensibility/internals/managing-configuration-options.md)   
 [建立  的專案](../../extensibility/internals/project-configuration-for-building.md)設定  
 [專案設定物件](../../extensibility/internals/project-configuration-object.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)

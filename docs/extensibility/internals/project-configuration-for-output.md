---
title: 專案組態輸出 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 72660ab5a3c3aedd888f22bdf7db1ef635d5bc34
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069547"
---
# <a name="project-configuration-for-output"></a>輸出的專案組態
每個設定可以支援一組產生輸出項目，例如可執行檔或資源檔案的建置程序。 這些輸出項目都是私用使用者，並可以放在連結相關的類型的輸出，例如可執行檔 （.exe、.dll、.lib） 和原始程式檔 （.idl，.h 檔案） 的群組。  
  
 輸出項目可透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>方法和列舉使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>方法。 當您想要輸出項目分組時，您的專案應該也會實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>介面。  
  
 藉由實作所開發的建構`IVsOutputGroup`可讓專案群組輸出，根據使用方式。 比方說，DLL 可能會分組成與它的程式資料庫 (PDB)。  
  
> [!NOTE]
>  PDB 檔案包含偵錯資訊，並建置.dll 或.exe 時指定 [產生偵錯資訊] 選項時，它會建立。 .Pdb 檔案通常會產生為只偵錯專案的組態。  
  
 專案必須傳回相同數目的支援，每個組態的群組，即使群組內所包含的輸出數目可能會不同組態設定。 例如，專案 Matt 的 DLL 可能會包含 mattd.dll 和 mattd.pdb 的偵錯組態，但只包含零售組態中的 matt.dll。  
  
 群組也有相同的識別項資訊，例如正式名稱、 顯示名稱和群組資訊，請設定設定在專案中。 這種一致性可讓部署與封裝能夠繼續運作，即使組態變更。  
  
 群組也可以有索引鍵的輸出，可讓封裝的捷徑，以指向有意義的名稱。 任何群組可能是在指定的組態中，空的因此應該不做任何假設，有關群組的大小。 每個群組中的任何組態的大小 （數字的輸出） 可以是不同於在相同的組態中的另一個群組的大小。 它也可以從另一個組態中相同的群組的大小不同。  
  
 ![輸出群組圖形](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
輸出群組  
  
 主要用途<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>介面是以建置、 部署和偵錯管理物件及允許專案能夠自由地群組輸出存取。 如需使用此介面的詳細資訊，請參閱 <<c0> [ 專案組態物件](../../extensibility/internals/project-configuration-object.md)。  
  
 在上圖中，群組內建有金鑰，因此輸出到組態 （bD.exe 或 b.exe） 使用者可以建立內建的捷徑，並了解快顯，不管部署的組態。 群組來源沒有輸出的索引鍵，因此使用者無法建立它的捷徑。 如果偵錯群組內建有索引鍵的輸出，但零售群組建置沒有，那就是實作不正確。 說明如下，然後，如果任何組態都包含沒有輸出中，有群組，如此一來，任何索引鍵的檔案，則包含輸出的其他設定與該群組不能將金鑰檔案。 安裝程式編輯器假設，標準的名稱和顯示名稱的群組，再加上存在的索引鍵的檔案，不會變更型組態中。  
  
 請注意，如果專案具有`IVsOutputGroup`，它不想要封裝或部署，便可將該輸出放在群組中。 輸出仍可列舉通常藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>方法會傳回所有不論群組組態的輸出。  
  
 如需詳細資訊，請參閱 < 實作`IVsOutputGroup`中的自訂專案範例[專案的 MPF](https://github.com/tunnelvisionlabs/MPFProj10)。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)
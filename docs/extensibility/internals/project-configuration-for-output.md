---
title: "專案組態輸出 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 4f3927ac9aa9e85be026d2b9a2af1c0c4d956c9f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="project-configuration-for-output"></a>專案組態的輸出
每個設定可以支援一組產生輸出項目，例如可執行檔或資源檔案的建置處理序。 這些輸出項目的私用使用者，而且可以放置在連結相關的類型的輸出，例如可執行檔 （.exe、.dll、.lib） 和原始程式檔 （.idl，.h 檔案） 的群組。  
  
 輸出項目可供透過<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2>方法和列舉與<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs>方法。 當您想要輸出項目分組時，也應該實作您的專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup>介面。  
  
 藉由實作開發建構`IVsOutputGroup`可讓專案以根據使用量群組輸出。 比方說，DLL 可能會與它的程式資料庫 (PDB) 組成群組。  
  
> [!NOTE]
>  PDB 檔案包含偵錯資訊，並建立.dll 或.exe 時指定 [產生偵錯資訊] 選項時，就會建立。 只偵錯專案組態通常會產生.pdb 檔案。  
  
 專案必須傳回相同數目的支援，每個設定的群組，即使群組內所包含的輸出數目而異的組態設定。 例如，專案 Matt 的 DLL 可能會包含 mattd.dll 和 mattd.pdb 偵錯組態，但只包含 matt.dll 零售組態中。  
  
 群組也有相同的識別項資訊，例如正式名稱、 顯示名稱和群組資訊的組態設定專案中。 部署與封裝來繼續運作，即使設定變更，可讓此一致性。  
  
 群組也可以有索引鍵的輸出，可讓封裝捷徑，以指向變得有意義。 任何群組可能是指定的設定，空的因此您應該有關群組的大小不進行任何假設。 任何組態中每個群組的大小 （數字的輸出） 可以不同於相同的組態中的另一個群組的大小。 它也可以從另一個組態中相同的群組的大小不同。  
  
 ![輸出群組圖形](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
輸出群組  
  
 主要用途<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg>介面是提供來建置、 部署和偵錯管理物件和允許專案輸出群組自由存取。 如需使用此介面的詳細資訊，請參閱[專案組態物件](../../extensibility/internals/project-configuration-object.md)。  
  
 在上圖中，群組內建有索引鍵因此輸出跨組態 （bD.exe 或 b.exe） 使用者可以建立內建的捷徑，並知道不論部署組態會使用的捷徑。 群組來源沒有輸出的索引鍵，因此使用者無法建立捷徑。 如果偵錯群組建置索引鍵的輸出，但零售建立群組並不會也就是使用不正確的實作。 說明如下，然後，如果任何組態都有不包含任何輸出的群組，如此一來，任何索引鍵的檔案，然後與該群組中包含輸出的其他組態不能有金鑰檔案。 安裝程式編輯器假設的正式名稱和顯示名稱的群組，再加上存在的檔案，不會變更組態中的基礎。  
  
 請注意，如果專案具有`IVsOutputGroup`，它不想要封裝或部署，便可將該輸出放在群組中。 輸出可以仍然正常列舉藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A>方法會傳回所有不論群組組態的輸出。  
  
 如需詳細資訊，請參閱的實作`IVsOutputGroup`的自訂專案範例中[專案的 MPF](http://mpfproj12.codeplex.com)。  
  
## <a name="see-also"></a>請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)   
 [方案組態](../../extensibility/internals/solution-configuration.md)
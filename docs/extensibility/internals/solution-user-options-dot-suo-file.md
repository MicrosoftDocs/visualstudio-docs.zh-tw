---
title: 方案使用者選項 (。Suo) 檔案 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b96e3ad2ec29402dddc7354df46293b99bac3ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130843"
---
# <a name="solution-user-options-suo-file"></a>方案使用者選項 (。Suo) 檔案
方案使用者選項 (.suo) 檔案包含每個使用者方案選項。 這個檔案不應該簽入原始程式碼控制項中。  
  
 結構化儲存體或以二進位格式儲存的檔案，複合方案使用者選項 (.suo) 檔案。 您要將用來識別.suo 檔案中的資訊的索引鍵的資料流的名稱儲存成資料流的使用者資訊。 方案使用者選項檔用來儲存使用者喜好設定，以及 Visual Studio 會儲存方案時自動建立。  
  
 當環境隨即開啟.suo 檔案時，它會列舉所有目前載入的 Vspackage。 如果 VSPackage 實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>介面，則環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A>vspackage 要求它從.suo 檔案載入的所有資料的方法。  
  
 它是 VSPackage 的責任，知道什麼資料流寫入.suo 檔案。 因此會寫入每個資料流，VSPackage 回撥到透過環境<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>載入特定的資料流所識別的索引鍵，這是資料流的名稱。 環境然後回撥來讀取資料流的名稱傳遞該特定資料流 VSPackage 和`IStream`指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>方法。  
  
 此時，其他呼叫`LoadUserOptions`以查看是否有要讀取的.suo 檔案的另一個區段。 此程序會繼續直到所有的.suo 檔案中的資料流已讀取及處理環境。  
  
 當方案會儲存或關閉，環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>方法指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>方法。 `IStream`包含要儲存的二進位資訊傳遞至<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>方法，然後將資訊寫入至.suo 檔案，並在呼叫`SaveUserOptions`以查看是否有另一個資料流的寫入.suo 方法檔案。  
  
 這兩種方法，`SaveUserOptions`和`WriteUserOptions`，會針對每個資料流的資訊儲存到.suo 檔案中，傳入的指標呼叫以遞迴方式`IVsSolutionPersistence`。 呼叫以遞迴方式，以允許進行的.suo 檔案的多個資料流寫入。 如此一來，使用者資訊與方案一起保存，一定會有的下次開啟方案。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [方案](../../extensibility/internals/solutions.md)